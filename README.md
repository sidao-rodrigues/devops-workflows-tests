# devops-workflows-tests

Este projeto demonstra a implementação de workflows de CI/CD usando GitHub Actions para diferentes tipos de branches.

## 🚀 Workflows Implementados

### 1. Feature Branch CI (`feature/*`)
- **Trigger**: Push ou Pull Request para branches com prefixo `feature/`
- **Validações**:
  - Verificação da versão do projeto
  - Execução dos testes
  - Processo de build
  - Validação dos artefatos de build
- **Matrix Strategy**: Testa em Node.js 18.x e 20.x

### 2. Fix Branch CI (`fix/*`)
- **Trigger**: Push ou Pull Request para branches com prefixo `fix/`
- **Validações**:
  - Verificação da versão do projeto
  - Execução dos testes
  - Processo de build
  - Validação dos artefatos de build
  - Verificações de segurança específicas para fixes
- **Matrix Strategy**: Testa em Node.js 18.x e 20.x

### 3. General CI/CD (`main`, `develop`)
- **Trigger**: Push ou Pull Request para branches principais
- **Validações**:
  - Execução dos testes
  - Processo de build
  - Validação geral do projeto

## 📦 Scripts NPM

- `npm test`: Executa os testes do projeto
- `npm run build`: Realiza o build do projeto
- `npm start`: Inicia a aplicação

## 🔧 Como usar

1. Crie uma branch com prefixo `feature/` ou `fix/`:
   ```bash
   git checkout -b feature/nova-funcionalidade
   # ou
   git checkout -b fix/correcao-bug
   ```

2. Faça suas alterações e commit:
   ```bash
   git add .
   git commit -m "Adiciona nova funcionalidade"
   ```

3. Faça push da branch:
   ```bash
   git push origin feature/nova-funcionalidade
   ```

4. O workflow será executado automaticamente e você poderá acompanhar o progresso na aba "Actions" do GitHub.

## ✅ Status dos Workflows

Os workflows irão executar automaticamente quando:
- Você fizer push para branches com prefixo `feature/*` ou `fix/*`
- Você abrir um Pull Request para essas branches
- Você fizer push para `main` ou `develop`

Todos os workflows incluem notificações de sucesso e falha para facilitar o acompanhamento.