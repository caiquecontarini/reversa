# 🤝 Contribuindo para Reversa

Obrigado por tirar um tempo para contribuir! Reversa é um framework colaborativo e suas contribuições são bem-vindas.

---

## 🚀 Como começar

1. **Faça um fork** do repositório
2. **Clone seu fork:**
   ```bash
   git clone https://github.com/seu-usuario/reversa.git
   cd reversa
   ```
3. **Instale as dependências:**
   ```bash
   npm install
   ```
4. **Crie uma branch** para sua feature:
   ```bash
   git checkout -b feature/sua-feature
   ```
5. **Faça suas mudanças** e teste
6. **Commit com mensagens descritivas:**
   ```bash
   git commit -m "feat: descrição clara do que foi feito"
   ```
7. **Envie um pull request** com descrição detalhada

---

## 📋 Tipos de contribuições bem-vindas

### 🐛 Correção de bugs

1. **Abra uma issue** descrevendo o problema (se ainda não houver)
2. **Faça um fork e corrija** o bug
3. **Envie um PR** com:
   - Descrição clara do problema
   - Como reproduzir
   - Como a correção funciona
   - Testes (se aplicável)

### ✨ Novas features

1. **Abra uma issue** para discutir a ideia **antes de implementar**
2. Aguarde feedback da equipe
3. Se aprovado, implemente seguindo os padrões do projeto
4. Envie um PR bem documentado

### 📚 Melhorias na documentação

- Ortografia, clareza, exemplos
- Adicione exemplos práticos
- Traduções (mantendo português como padrão)
- Melhore explicações técnicas

### 🤖 Novos agentes

1. **Discuta a ideia** em uma issue
2. Use a estrutura padrão:
   ```
   agents/reversa-seu-agente/
   ├── SKILL.md
   ├── references/
   └── (opcional) templates/
   ```
3. Siga o padrão dos agents existentes
4. Documente bem em português

---

## 📝 Padrões de código e estilo

### JavaScript

- Use `const`/`let` (não `var`)
- Sem dependências externas no bin/
- Comentários em português para clareza

### Markdown

- Títulos em português
- Código em blocos ` ``` `
- Listas com `-` (não `*`)
- Links relativos quando possível

### Commits

Siga [Conventional Commits](https://www.conventionalcommits.org/):

```
feat: adicione novo agente reversa-xyz
fix: corrija comportamento de checkpoint
docs: melhore explicação de fase de escavação
refactor: simplifique lógica de orquestração
test: adicione testes para Scout
chore: atualize dependências
```

---

## ✅ Checklist antes de enviar PR

- [ ] Testei localmente (se aplicável)
- [ ] Código em português ou com comentários em português
- [ ] Documentação atualizada
- [ ] Nenhuma dependência nova adicionada (discuta primeiro)
- [ ] Commits com mensagens claras
- [ ] Sem tokens, senhas ou dados sensíveis
- [ ] Respeitei a estrutura existente

---

## 🔍 Processo de revisão

1. **Code review** — Vamos revisar o código
2. **Testes** — Rodaremos testes se necessário
3. **Feedback** — Podemos pedir ajustes
4. **Merge** — Após aprovação, vamos fazer merge

---

## 📞 Dúvidas ou sugestões?

- **Abra uma issue** — Para dúvidas, bugs ou sugestões
- **Discussões** — Para ideias maiores ou brainstorms
- **Pull requests** — Envie suas mudanças!

---

## 📄 Licença

Ao contribuir, você concorda que suas contribuições serão licenciadas sob a mesma licença MIT do projeto.

---

**Obrigado por contribuir para melhorar Reversa! 🚀**
