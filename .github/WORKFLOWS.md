# 🔄 GitHub Actions Setup

Este repositório possui automação profissional com GitHub Actions.

## 📊 Workflows Configurados

### 1. **Deploy Pages** (`.github/workflows/deploy-pages.yml`)

Automáticamente constrói e deploya documentação em GitHub Pages quando há push na main.

```bash
# Triggers
- Push para main
- Pull requests
```

**O que faz:**
- ✅ Instala dependências (mkdocs, materialize)
- ✅ Constrói site estático
- ✅ Valida YAML
- ✅ Faz deploy automático

**URL:** https://caiquecontarini.github.io/reversa/

---

### 2. **Quality Checks** (`.github/workflows/quality-checks.yml`)

Valida qualidade do código a cada push e pull request.

```bash
# Triggers
- Push para main/develop
- Pull requests
```

**O que faz:**
- ✅ Lint de Markdown (`.markdownlint.json`)
- ✅ Lint de YAML (`.yamllint`)
- ✅ Scan de segurança (Trivy)
- ✅ Upload para GitHub Security

---

## 🛡️ Configurações de Segurança

### Trivy Scanner
Escaneia vulnerabilidades em:
- Dependências
- Imagens Docker
- Código

Resultados aparecem em: **Security > Code scanning**

---

## 📋 Templates Automáticos

### Issue Templates
- **Bug Report** (`.github/ISSUE_TEMPLATE/bug_report.md`)
- **Feature Request** (`.github/ISSUE_TEMPLATE/feature_request.md`)

### Pull Request Template
(`.github/pull_request_template.md`)

Aparecem quando você abre issue/PR no GitHub.

---

## 👥 Code Ownership

Ver `.github/CODEOWNERS` para regras de auto-assign.

---

## 🚀 Como Usar Localmente

### Build Docs

```bash
pip install mkdocs mkdocs-material mkdocs-glightbox
mkdocs serve  # Preview em http://localhost:8000
```

### Lint Markdown

```bash
npm install markdownlint-cli
markdownlint docs/**/*.md
```

### Lint YAML

```bash
pip install yamllint
yamllint .
```

---

## 📈 Status dos Workflows

Veja o status em: **Actions** tab do repositório.

---

## 🎯 Próximos Passos

- [ ] Adicionar testes automáticos
- [ ] Coverage reports
- [ ] Performance benchmarks
- [ ] Docker build/push

---

Qualquer dúvida? Abra uma Discussion!
