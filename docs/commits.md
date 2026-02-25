# 📝 Conventional Commits

O **Conventional Commits** é um padrão para mensagens de commit que facilita a leitura do histórico, automatiza geração de changelogs e melhora a colaboração entre equipes.  
Ele define uma convenção simples e extensível para escrever commits consistentes.

---

## 🚀 Por que usar?
- 📖 Histórico de commits mais claro e organizado  
- 🤖 Geração automática de changelogs  
- 🛠️ Integração com ferramentas de versionamento semântico (semver)  
- 👥 Facilita colaboração em equipe  

---

## 📌 Estrutura da mensagem

Cada commit segue o formato:

```
<tipo>[escopo opcional]: <descrição>
```

### Exemplos:
```bash
feat(auth): adicionar login com Google
fix(api): corrigir erro de validação no endpoint /users
docs(readme): atualizar instruções de instalação
chore: atualizar dependências do projeto
```

---

## 🔑 Tipos mais comuns

| Tipo       | Uso                                                                 |
|------------|---------------------------------------------------------------------|
| **feat**   | Nova funcionalidade                                                 |
| **fix**    | Correção de bug                                                     |
| **docs**   | Alterações na documentação                                          |
| **style**  | Ajustes de formatação (sem impacto no código)                       |
| **refactor** | Refatoração de código sem mudança de comportamento                |
| **test**   | Adição ou alteração de testes                                       |
| **chore**  | Tarefas de manutenção (build, dependências, configs)                |
| **perf**   | Melhorias de performance                                            |

---

## 🎯 Escopo (opcional)
O escopo indica a área afetada pelo commit.  
Exemplo:
```bash
feat(auth): adicionar suporte a JWT
fix(ui): corrigir botão de login
```

---

## 🛠️ Regras práticas
- Use **imperativo** na descrição (ex.: “adicionar”, não “adicionado”).  
- Seja **curto e direto** (máx. ~50 caracteres).  
- Se precisar detalhar, use o corpo do commit:  
  ```bash
  feat(api): adicionar endpoint de relatórios

  - Implementa rota GET /reports
  - Adiciona testes unitários
  - Atualiza documentação da API
  ```

---

## 🤝 Boas práticas em equipe
- Padronize o uso em todos os commits.  
- Configure **commitlint** ou **husky** para validar mensagens automaticamente.  
- Documente no README para que novos colaboradores saibam como contribuir.  

---

## 📦 Ferramentas úteis
- [commitlint](https://commitlint.js.org/) → valida mensagens de commit  
- [husky](https://typicode.github.io/husky/) → hooks de git para automatizar validações  
- standard-version [(github.com in Bing)](https://www.bing.com/search?q="https%3A%2F%2Fgithub.com%2Fconventional-changelog%2Fstandard-version") → gera changelogs e versões automaticamente  

---

## ✅ Exemplo de fluxo
1. Fazer alterações no código  
2. Criar commit seguindo o padrão:
   ```bash
   git commit -m "feat(auth): adicionar login com Google"
   ```
3. Push para o repositório  
4. CI/CD gera changelog automaticamente 🎉  

---
