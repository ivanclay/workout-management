# 🖥️ Instalação do NVM no Windows + Uso de `.nvmrc`

O **NVM for Windows** é uma ferramenta que permite instalar e alternar entre diferentes versões do Node.js facilmente.  
Com o arquivo `.nvmrc`, você pode definir qual versão do Node.js deve ser usada em cada projeto, garantindo consistência entre ambientes.

---

## 📋 Pré-requisitos
- Windows 10 ou superior  
- Permissões de administrador  
- Prompt de Comando, PowerShell ou Git Bash  

---

## 🚀 Instalação

### 1. Baixe o instalador
Acesse o repositório oficial do **NVM for Windows**:  
👉 nvm-windows releases [(NVM Windows)](https://github.com/coreybutler/nvm-windows)

Baixe o arquivo **nvm-setup.exe** da última versão.

---

### 2. Execute o instalador
- Clique duas vezes no `nvm-setup.exe`  
- Escolha o diretório de instalação (padrão: `C:\Program Files\nvm`)  
- Defina também o diretório do Node.js (padrão: `C:\Program Files\nodejs`)  

---

### 3. Verifique a instalação
Abra o terminal e digite:
```bash
nvm version
```
Se aparecer um número de versão, está tudo certo 🎉

---

## 🛠️ Usando o NVM

- **Instalar a última versão do Node.js:**
```bash
nvm install latest
```

- **Instalar uma versão específica:**
```bash
nvm install 18.17.0
```

- **Listar versões instaladas:**
```bash
nvm list
```

- **Alternar entre versões:**
```bash
nvm use 18.17.0
```

---

## 📂 Usando `.nvmrc` em projetos

O arquivo `.nvmrc` serve para indicar qual versão do Node.js deve ser usada em um projeto.  
Basta criar um arquivo chamado `.nvmrc` na raiz do seu repositório com o número da versão desejada:

```bash
echo 18.17.0 > .nvmrc
```

Exemplo de conteúdo do `.nvmrc`:
```
18.17.0
```

---

### 🔄 Como aplicar a versão do `.nvmrc`
No terminal, dentro da pasta do projeto:
```bash
nvm use
```

O NVM vai ler o arquivo `.nvmrc` e automaticamente usar a versão indicada.  

---

## ✅ Dicas finais
- Mantenha o `.nvmrc` versionado no Git para que toda a equipe use a mesma versão.  
- Se precisar atualizar, basta mudar o número dentro do `.nvmrc` e rodar `nvm install` novamente.  
- Isso evita conflitos entre ambientes de desenvolvimento e produção.  

---

## 🤝 Boas práticas para equipes com `.nvmrc`

Quando várias pessoas trabalham no mesmo projeto, manter a mesma versão do Node.js é essencial para evitar erros e inconsistências. O uso do `.nvmrc` facilita essa padronização.

### 📌 Recomendações
- **Versione o `.nvmrc` no Git**  
  Assim, todos os membros da equipe terão acesso à versão correta do Node.js definida para o projeto.

- **Documente no README do projeto**  
  Inclua instruções rápidas para rodar `nvm use` ao entrar no repositório. Isso ajuda novos colaboradores a configurarem o ambiente sem surpresas.

- **Atualize o `.nvmrc` com cuidado**  
  Se precisar mudar a versão do Node.js, comunique a equipe e faça a atualização em conjunto para evitar conflitos.

- **Automatize com scripts**  
  Adicione no `package.json` um script que valide a versão do Node.js antes de rodar o projeto:
  ```json
  {
    "scripts": {
      "check-node": "node -v && echo 'Verifique se a versão corresponde ao .nvmrc'"
    }
  }
  ```

- **Integre ao CI/CD**  
  Configure o pipeline para usar a versão definida no `.nvmrc`, garantindo que o ambiente de produção seja idêntico ao de desenvolvimento.

---

### 🧩 Exemplo de fluxo para novos colaboradores
1. Clone o repositório:
   ```bash
   git clone https://github.com/empresa/projeto.git
   ```
2. Entre na pasta do projeto:
   ```bash
   cd projeto
   ```
3. Use a versão correta do Node.js:
   ```bash
   nvm use
   ```
4. Instale as dependências:
   ```bash
   npm install
   ```

---

Assim, todos os membros da equipe trabalham com a mesma versão do Node.js, evitando problemas de compatibilidade e garantindo um fluxo de desenvolvimento mais suave.  

---

## ⚙️ Integração com CI/CD (GitHub Actions)

Para garantir que o ambiente de integração contínua use a mesma versão do Node.js definida no `.nvmrc`, podemos configurar o pipeline para ler esse arquivo e instalar a versão correta.

### 📄 Exemplo de workflow (`.github/workflows/ci.yml`)

```yaml
name: CI

on:
  push:
    branches: [ main ]
  pull_request:
    branches: [ main ]

jobs:
  build:
    runs-on: ubuntu-latest

    steps:
      - name: Checkout código
        uses: actions/checkout@v4

      - name: Ler versão do Node.js do .nvmrc
        id: node_version
        run: echo "NODE_VERSION=$(cat .nvmrc)" >> $GITHUB_ENV

      - name: Configurar Node.js
        uses: actions/setup-node@v4
        with:
          node-version: ${{ env.NODE_VERSION }}

      - name: Instalar dependências
        run: npm install

      - name: Rodar testes
        run: npm test
```

---

### 🔎 Como funciona
1. O pipeline faz checkout do código.  
2. Lê a versão do Node.js definida no `.nvmrc`.  
3. Usa a action oficial `actions/setup-node` para instalar essa versão.  
4. Instala dependências e roda os testes.  

---

### ✅ Benefícios
- **Consistência total**: o mesmo Node.js usado localmente será usado no CI/CD.  
- **Automação**: não é necessário atualizar manualmente a versão no pipeline, basta alterar o `.nvmrc`.  
- **Escalabilidade**: funciona para múltiplos projetos e equipes sem esforço extra.  

---

Assim, o `.nvmrc` passa a ser a **única fonte de verdade** para a versão do Node.js, garantindo que todos — desenvolvedores e pipelines — estejam alinhados.  

---
