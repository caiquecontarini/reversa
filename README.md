# 🔄 Reversa

**Transforme sistemas legados em especificações executáveis para agentes de IA.**

[![Node.js](https://img.shields.io/badge/Node.js-18%2B-339933?logo=node.js&logoColor=white)](https://nodejs.org/)
[![Licença MIT](https://img.shields.io/badge/Licença-MIT-yellow.svg)](LICENSE)
[![Contribuições Bem-vindas](https://img.shields.io/badge/Contribuições-bem--vindas-brightgreen.svg)](CONTRIBUINDO.md)

---

## 🎯 Por que Reversa existe

A maioria dos sistemas em produção carrega anos de conhecimento acumulado: regras de negócio implícitas, decisões arquiteturais não documentadas, lógica crítica enterrada em código que ninguém quer mexer. Esse conhecimento existe, mas está preso.

Agentes de IA são transformadores para criar e evoluir software, mas dependem de especificações para operar com segurança. Para novos sistemas, você escreve a spec e o agente executa. Para sistemas legados — ou aqueles feitos com puro "vibe coding" — não há spec: o agente não tem como saber o que não pode quebrar.

**Reversa é a ponte entre o sistema legado e agentes de IA.**

Ele analisa o código existente, extrai conhecimento acumulado (regras de negócio, fluxos, contratos de módulo, decisões arquiteturais retroativas) e transforma tudo em especificações executáveis e rastreáveis prontas para qualquer agente de codificação.

O resultado não é documentação para humanos lerem. Essas são **contratos operacionais** que permitem a um agente evoluir o sistema com fidelidade ao que já existe.

---

## 🚀 Instalação

Na raiz do projeto legado:

```bash
npx reversa install
```

O instalador vai:
1. Detectar os motores de IA presentes no ambiente (Claude Code, Codex, Cursor, etc.)
2. Perguntar quais agentes instalar — todos selecionados por padrão
3. Coletar nome do projeto, linguagem e preferências
4. Copiar agentes para `.agents/skills/` (e `.claude/skills/` para Claude Code)
5. Criar o arquivo de entrada do engine (`CLAUDE.md`, `AGENTS.md`, etc.)
6. Criar a estrutura `.reversa/` com estado, configuração e plano
7. Gerar manifest SHA-256 para atualizações seguras

> Reversa **nunca deleta ou modifica** arquivos existentes em seu projeto.
> Os agentes escrevem apenas em `.reversa/` e na pasta de saída (`_reversa_sdd/` por padrão).

**Requisitos:** Node.js 18+

---

## 🔐 Garantia de imutabilidade do projeto legado

O instalador apenas cria novos arquivos (`CLAUDE.md`, `AGENTS.md`, `.agents/skills/`, etc.) e **nunca modifica ou deleta nenhum arquivo existente** no seu projeto. Durante a análise, os agentes operam sob uma diretiva estrita e inviolável: **todas as escritas são restritas a `.reversa/` e `_reversa_sdd/`** — nenhum outro arquivo em seu projeto é tocado.

## 💾 Faça backup do seu projeto antes de começar

Embora Reversa nunca modifique seus arquivos, agentes de IA podem cometer erros. **Recomendamos fortemente:**

1. **Versionize o projeto em Git** — certifique-se de que todos os arquivos estão commitados antes de começar a análise
2. **Tenha o repositório no GitHub** (ou GitLab, Bitbucket) — para ter uma cópia remota segura
3. **Faça uma cópia local da pasta** — um simples `cp -r meu-projeto meu-projeto-backup` protege contra eventos inesperados

Se algo inesperado acontecer durante a análise, você pode restaurar o estado original com `git restore .` ou a partir da cópia de backup.

## 🔑 Segurança de chaves API

**Reversa não solicita, armazena ou transmite chaves API de nenhum serviço de LLM.** Toda inteligência é delegada ao agente de IA já presente em seu ambiente (Claude Code, Codex, Cursor, etc.) — sem dependências externas de autenticação.

---

## 📖 Como usar

Após a instalação, abra o projeto no agente de IA e ative Reversa:

```
/reversa
```

Para engines sem suporte a slash commands (como Codex):

```
reversa
```

Reversa vai se apresentar, criar um plano de exploração personalizado e coordenar toda a análise. O progresso é salvo em `.reversa/state.json` em cada checkpoint — se a sessão for interrompida, apenas digite `reversa` para retomar de onde parou.

---

## ⚙️ Como funciona

Reversa usa um pipeline de 5 fases orquestrado pelo agente **Reversa**:

```
Reconhecimento  Escavação  Interpretação  Geração  Revisão
    Scout      Arqueólogo   Detective    Escritor  Revisor
                                       Arquiteto
```

Agentes independentes (rodam em qualquer fase): **Visor**, **Data Master**, **Design System**, **Rastreador**

---

## 🤖 Agentes

### Obrigatórios

| Agente | Função |
|--------|--------|
| **Reversa** | Orquestrador central. Coordena todos os agentes, salva checkpoints, guia o usuário |
| **Scout** | Mapeia a superfície: estrutura de pastas, linguagens, frameworks, dependências, entry points |
| **Arqueólogo** | Análise profunda módulo a módulo: algoritmos, fluxos de controle, estruturas de dados |
| **Detective** | Extrai conhecimento implícito de negócio: regras, ADRs retroativas, máquinas de estado, permissões |
| **Arquiteto** | Sintetiza tudo em diagramas C4, ERD completo, mapa de integração e débito técnico |
| **Escritor** | Gera especificações como contratos operacionais com rastreabilidade de código |

### Opcionais (instalados por padrão)

| Agente | Função |
|--------|--------|
| **Revisor** | Revisa specs, encontra inconsistências e valida lacunas com o usuário |
| **Rastreador** | Análise dinâmica: resolve lacunas via logs, tracing e dados reais (somente leitura) |
| **Visor** | Documenta a interface a partir de screenshots — sem necessidade do sistema rodar |
| **Data Master** | Análise completa de banco de dados: DDL, migrações, ORM, ERD, triggers, procedures |
| **Design System** | Extrai tokens de design: cores, tipografia, espaçamento, temas e componentes |
| **Cronista** | Documenta mudanças de código durante sessões de desenvolvimento |

### Tradutores (adaptadores de entrada)

Use quando o "código" legado não é código fonte mas um artefato estruturado como um workflow visual. Gera a spec SDD e prepara o estado para o pipeline principal assumir.

| Agente | Função |
|--------|--------|
| **Tradutor N8N** | Lê workflows N8N exportados como JSON e produz specs SDD prontas para reimplementação em Python. Ativado via `/reversa-n8n` |

---

## 📦 O que é gerado

```
_reversa_sdd/
├── inventory.md              # Inventário do projeto
├── dependencies.md           # Dependências com versões
├── code-analysis.md          # Análise técnica por módulo
├── data-dictionary.md        # Dicionário de dados
├── domain.md                 # Glossário e regras de negócio
├── state-machines.md         # Máquinas de estado em Mermaid
├── permissions.md            # Matriz de permissões
├── architecture.md           # Visão geral arquitetural
├── c4-context.md             # Diagrama C4: Contexto
├── c4-containers.md          # Diagrama C4: Containers
├── c4-components.md          # Diagrama C4: Componentes
├── erd-complete.md           # ERD completo em Mermaid
├── confidence-report.md      # Relatório de confiança 🟢🟡🔴
├── gaps.md                   # Lacunas identificadas
├── questions.md              # Perguntas para validação humana
├── dynamic.md                # Achados de análise dinâmica (Rastreador)
├── sdd/                      # Specs por componente
│   └── [component].md
├── openapi/                  # Specs de API (se aplicável)
├── user-stories/             # Histórias de usuário (se aplicável)
├── adrs/                     # Decisões arquiteturais retroativas
├── flowcharts/               # Flowcharts em Mermaid
├── sequences/                # Diagramas de sequência
├── ui/                       # Specs de interface (Visor)
├── database/                 # Specs de banco de dados (Data Master)
├── design-system/            # Tokens de design (Design System)
└── traceability/
    ├── spec-impact-matrix.md # Qual spec impacta qual
    └── code-spec-matrix.md   # Arquivo de código para spec correspondente
```

### Escala de confiança

Cada afirmação nas specs é marcada com:

| Marca | Significado |
|-------|------------|
| 🟢 CONFIRMADO | Extraído diretamente do código — pode ser citado com arquivo e linha |
| 🟡 INFERIDO | Deduzido de padrões — pode estar errado |
| 🔴 LACUNA | Não determinável a partir do código — requer validação humana |

---

## 🖥️ Engines suportadas

| Engine | Arquivo criado | Caminho de skills | Ativação |
|--------|-------------|-------------|--------------|
| Claude Code ⭐ | `CLAUDE.md` | `.claude/skills/reversa-*/` e `.agents/skills/reversa-*/` | `/reversa` |
| Codex ⭐ | `AGENTS.md` | `.agents/skills/reversa-*/` | `reversa` |
| Cursor ⭐ | `.cursorrules` | `.agents/skills/reversa-*/` | `/reversa` |
| Gemini CLI | `GEMINI.md` | `.agents/skills/reversa-*/` | `/reversa` |
| Windsurf | `.windsurfrules` | `.agents/skills/reversa-*/` | `/reversa` |
| Antigravity | `AGENTS.md` | `.agents/skills/reversa-*/` | `/reversa` |
| Kiro | (nenhum) | `.kiro/skills/reversa-*/` e `.agents/skills/reversa-*/` | `/reversa` |
| Opencode | `AGENTS.md` | `.agents/skills/reversa-*/` | `reversa` |
| Cline | `.clinerules` | `.agents/skills/reversa-*/` | `/reversa` |
| Roo Code | `.roorules` | `.agents/skills/reversa-*/` | `/reversa` |
| GitHub Copilot | `.github/copilot-instructions.md` | `.agents/skills/reversa-*/` | `/reversa` |
| Aider | `CONVENTIONS.md` | `.agents/skills/reversa-*/` | `reversa` |
| Amazon Q Developer | `.amazonq/rules/reversa.md` | `.agents/skills/reversa-*/` | `/reversa` |

---

## 🛠️ Comandos CLI

```bash
npx reversa install      # Instala Reversa no projeto
npx reversa status       # Mostra o estado atual da análise
npx reversa update       # Atualiza agentes para a versão mais recente
npx reversa add-agent    # Adiciona um agente ao projeto
npx reversa add-engine   # Adiciona suporte para um novo engine
npx reversa uninstall    # Remove Reversa do projeto
```

O comando `update` detecta arquivos que você modificou via SHA-256 e nunca sobrescreve customizações.
O comando `uninstall` remove apenas arquivos criados por Reversa — nada do projeto legado é tocado.

---

## 📂 Estrutura interna

```
.reversa/
├── state.json          # Estado da análise entre sessões
├── config.toml         # Configuração do projeto
├── config.user.toml    # Preferências pessoais (não commitar)
├── plan.md             # Plano de exploração (editável pelo usuário)
├── version             # Versão instalada
├── context/
│   ├── surface.json    # Gerado pelo Scout
│   └── modules.json    # Gerado pelo Arqueólogo
└── _config/
    ├── manifest.yaml       # Metadados de instalação
    └── files-manifest.json # Hashes SHA-256 para atualizações seguras

.agents/skills/         # Skills universais (todos agentes compatíveis)
.claude/skills/         # Espelho para Claude Code
```

---

## 🤝 Contribuindo

Contribuições são bem-vindas. Abra uma issue para discutir antes de enviar um PR.

```bash
git clone https://github.com/caiquecontarini/reversa.git
cd reversa
npm install
```

---

## 📄 Licença

MIT — veja [LICENSE](LICENSE) para detalhes.

---

**Desenvolvido por Caique Contarini · [nextron.site](https://nextron.site)**
