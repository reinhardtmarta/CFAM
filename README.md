# CFAM — Core Filtering AI Middleware

![Rust](https://img.shields.io/badge/Rust-000000?style=for-the-badge&logo=rust&logoColor=white)
![Docker](https://img.shields.io/badge/Docker-2496ED?style=for-the-badge&logo=docker&logoColor=white)
![Status](https://img.shields.io/badge/Status-Integração_IA_&_Contêineres-success?style=for-the-badge)
![Architecture](https://img.shields.io/badge/Arquitetura-CLI_Determinística-blue?style=for-the-badge)
![Security](https://img.shields.io/badge/Zero_Dependencies-Binário_Isolado-critical?style=for-the-badge)

---

## 🇧🇷 Português

**CFAM** é uma ferramenta de linha de comando (CLI) escrita em Rust que atua como barreira de segurança determinística (sempre gera o mesmo resultado para a mesma entrada) entre modelos de IA e sistemas internos.

### 📍 Fase Atual: Integração Real & Contêineres
O projeto avançou da Prova de Conceito (PoC) para testes práticos em ambiente isolado:
* **Integração com IA:** Conexão direta com modelos para interceptação e validação de respostas em tempo de execução (*runtime*).
* **Testes em Contêineres:** Execução via Docker para simular falhas reais, injeção de dados quebrados e medir consumo sob estresse.

> **Nota:** O motor principal com as regras proprietárias está em repositório privado. Este repositório público exibe a interface estrutural de demonstração.

### 🛡️ O que ele resolve
| Camada | Função |
| :--- | :--- |
| **Interceptação** | Captura o *payload* (carga de dados) gerado pela IA antes de chegar à sua aplicação. |
| **Veto Lógico** | Bloqueia dados truncados, malformados, injeções de código ou respostas com incerteza. |
| **Proteção contra Crash** | Funciona como fusível: se a IA falhar, o sistema interno permanece intacto. |
| **Auditoria Imutável** | Registra cada bloqueio ou aprovação em `cfam_audit_ledger.log` (*append-only* — apenas adição). |

### ⚙️ Contrato de Validação
1. **Integridade Estrutural:** Exige formatação completa e delimitadores fechados.
2. **Limite de Fronteira:** Rejeita excesso de tamanho e caracteres de controle inválidos.
3. **Rejeição de Anomalia:** Descarta padrões de ataque conhecidos.

* **Aprovado:** `Exit Code: 0` (segue o fluxo)
* **Rejeitado:** `Exit Code: 1` (execução bloqueada)
Ainda em construção 

### 🚀 Uso
```bash
./cfam "Sua tarefa ou payload de entrada"

```

# 🇺🇸 English
## CFAM is a Rust-based command-line interface (CLI) tool acting as a deterministic security barrier (always producing the same output for a given input) between AI models and internal systems.
📍 Current Phase: Live AI Integration & Containers
The project has moved from Proof of Concept (PoC) into practical validation:
 * Live AI Integration: Direct runtime interception and validation of AI model outputs.
 * Containerized Testing: Isolated Docker workloads to benchmark latency, simulate malformed payloads, and run stress tests.
> Note: The core engine containing proprietary filtering heuristics resides in a private repository. This public repository provides the architectural interface for reference.
> 
🛡️ Core Capabilities
| Layer | Function |
|---|---|
| Interception | Captures AI payloads immediately after generation before reaching downstream apps. |
| Logical Veto | Blocks truncated outputs, malformed structures, code injections, and probabilistic uncertainty. |
| Crash Protection | Acts as a technical fuse to prevent API or database failures caused by broken AI responses. |
| Immutable Audit | Logs every decision (approved/blocked) into cfam_audit_ledger.log (append-only ledger). |
⚙️ Validation Contract
 * Structural Integrity: Enforces complete formatting and closed delimiters.
 * Boundary Enforcement: Rejects oversized payloads and invalid control characters.
 * Anomaly Rejection: Drops known adversarial structures and escape sequences.
 * Approved: Exit Code: 0
 * Rejected: Exit Code: 1
   Loading...
🚀 Usage
./cfam "Your input or task description"

Author: Marta Reinhardt | Verification: Check SHA-256 checksums on official GitHub Releases.
Copyright © 2026 Marta Reinhardt. All Rights Reserved.

