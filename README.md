# devops-workflows-tests

Este projeto demonstra um workflow de CI/CD para branches com prefixo `feature/*`.

## 🚀 Workflow de CI/CD

### 📋 Workflow 1: Feature Branch CI/CD
O workflow será automaticamente acionado quando:
- Fizer push para uma branch com prefixo `feature/*`
- Abrir um Pull Request de uma branch `feature/*`

### 📋 Workflow 2: Auto PR to Develop
Após o sucesso do CI/CD, automaticamente:
- ✅ Cria um Pull Request da branch `feature/*` para `develop`
- ❌ Se o CI/CD falhar, não cria PR e notifica sobre a falha

### ✅ Validações Executadas

1. **Setup do Ambiente**: Node.js 20
2. **Instalação de Dependências**: `npm install`
3. **Lint Check**: Verificação de código (se disponível)
4. **Testes**: Execução de `npm test`
5. **Build**: Execução de `npm run build`
6. **Verificação de Startup**: Teste se a aplicação inicia corretamente

### 🤖 Automação de Pull Requests

Após sucesso no CI/CD:
- **Auto-criação de PR**: Cria automaticamente PR para `develop`
- **Verificações inteligentes**: Não duplica PRs existentes
- **Criação de branch**: Cria `develop` se não existir
- **Notificações claras**: Feedback sobre sucesso/falha

### 🎯 Scripts Disponíveis

```bash
npm test    # Executa os testes
npm run build    # Executa o build
npm start   # Inicia a aplicação
```

### 📋 Status do Workflow

- ✅ **CI/CD Sucesso**: Todos os checks passaram + PR automática para `develop`
- ❌ **CI/CD Falha**: Um ou mais checks falharam - PR não será criada
- 🤖 **Auto-PR**: Pull Request criada automaticamente após CI/CD bem-sucedido

## 🔧 Como Testar Localmente

```bash
# Instalar dependências
npm install

# Executar testes
npm test

# Executar build
npm run build

# Iniciar aplicação
npm start
```


##prompt
Ótimo, agora considere o caso em que se o job executar com sucesso, será aberto um Pull Request para a branch release/v-x.y.z

Obs.: Onde o valor de v-x.y.z será o valor que estará no package incrementado o valor de y (no caso a minor).

Ou seja, será realizado os passos:
Criar uma PR para a branch com a release/v-x.y.z;



