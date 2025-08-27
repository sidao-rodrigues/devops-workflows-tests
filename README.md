# devops-workflows-tests

Este projeto demonstra um workflow de CI/CD para branches com prefixo `feature/*`.

## 🚀 Workflow de CI/CD

O workflow será automaticamente acionado quando:
- Fizer push para uma branch com prefixo `feature/*`
- Abrir um Pull Request de uma branch `feature/*`

### ✅ Validações Executadas

1. **Setup do Ambiente**: Node.js 18.x e 20.x
2. **Instalação de Dependências**: `npm ci`
3. **Lint Check**: Verificação de código (se disponível)
4. **Testes**: Execução de `npm test`
5. **Build**: Execução de `npm run build`
6. **Verificação de Startup**: Teste se a aplicação inicia corretamente

### 🎯 Scripts Disponíveis

```bash
npm test    # Executa os testes
npm run build    # Executa o build
npm start   # Inicia a aplicação
```

### 📋 Status do Workflow

- ✅ **Sucesso**: Todos os checks passaram - branch pronta para review
- ❌ **Falha**: Um ou mais checks falharam - verificar logs e corrigir

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
