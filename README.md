# devops-workflows-tests

Este projeto demonstra a implementação de um workflow universal de CI/CD usando GitHub Actions que funciona para qualquer branch.

## 🚀 Workflow Implementado

### Universal CI/CD (`universal-ci.yml`)
- **Trigger**: Push ou Pull Request para **qualquer branch** (`**`)
- **Node.js**: Versão 20.x (única versão, otimizada)
- **Validações**:
  - ✅ Verificação da instalação do Node.js
  - ✅ Instalação inteligente de dependências (se existirem)
  - ✅ Verificação da versão do projeto
  - ✅ Execução dos testes
  - ✅ Processo de build
  - ✅ Validação da estrutura do projeto
  - ✅ Ações específicas por tipo de branch

### 🌿 Detecção Inteligente de Branch
O workflow identifica automaticamente o tipo de branch e executa validações específicas:

- **`feature/*`**: Validações para novas funcionalidades
- **`fix/*`**: Validações de correção + verificações de segurança
- **`main/master`**: Validações de produção
- **`develop/dev`**: Validações de desenvolvimento
- **Outras branches**: Validações padrão

## 📦 Scripts NPM

- `npm test`: Executa os testes do projeto
- `npm run build`: Realiza o build do projeto
- `npm start`: Inicia a aplicação

## 🔧 Como usar

1. Crie qualquer branch:
   ```bash
   git checkout -b minha-nova-branch
   # ou
   git checkout -b feature/nova-funcionalidade
   # ou
   git checkout -b fix/correcao-bug
   ```

2. Faça suas alterações e commit:
   ```bash
   git add .
   git commit -m "Minhas alterações"
   ```

3. Faça push da branch:
   ```bash
   git push origin minha-nova-branch
   ```

4. O workflow será executado automaticamente para **qualquer branch** e você poderá acompanhar o progresso na aba "Actions" do GitHub.

## ✅ Características do Workflow Universal

- 🌍 **Funciona para qualquer branch** - não há restrições
- ⚡ **Otimizado** - usa apenas Node.js 20.x
- 🧠 **Inteligente** - detecta o tipo de branch automaticamente
- 🔧 **Flexível** - funciona com ou sem dependências
- 📊 **Informativo** - logs detalhados e notificações claras
- 🚀 **Rápido** - sem cache desnecessário para projetos simples

## 📋 Status do Workflow

O workflow `Universal CI/CD` será executado automaticamente quando:
- Você fizer push para **qualquer branch**
- Você abrir um Pull Request de **qualquer branch** para **qualquer branch**

Todas as execuções incluem notificações detalhadas de sucesso e falha para facilitar o acompanhamento.