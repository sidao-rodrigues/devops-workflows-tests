# Guia do Workflow Universal

## 🛡️ IMPORTANTE: Proteção da Branch Main

**A branch `main` está protegida contra pushes diretos!**

### ✅ **Para alterações na main:**
```bash
# 1. Partir da main atualizada
git checkout main
git pull origin main

# 2. Criar nova branch
git checkout -b feature/minha-alteracao

# 3. Fazer alterações, commit e push
git add .
git commit -m "Minha alteração"
git push origin feature/minha-alteracao

# 4. Abrir Pull Request no GitHub para main
# 5. Aguardar aprovação e merge via PR
```

### ❌ **O que NÃO fazer:**
```bash
git checkout main
git push origin main  # 🚫 SERÁ BLOQUEADO!
```

## Como testar o workflow universal

### 1. Testando com qualquer branch

```bash
# Criar qualquer branch (não há restrições)
git checkout -b teste-universal
# ou
git checkout -b feature/minha-feature
# ou
git checkout -b fix/meu-fix
# ou
git checkout -b hotfix/urgente
# ou
git checkout -b develop

# Fazer uma alteração
echo "// Teste do workflow universal" >> src/index.js

# Commit e push
git add .
git commit -m "Testa workflow universal"
git push origin nome-da-branch
```

### 2. O que acontece automaticamente

✅ **Para qualquer branch**, o workflow irá:

1. **Setup**: Configurar Node.js 20.x
2. **Verificação**: Checar instalação do Node.js e npm
3. **Dependências**: Instalar dependências se existir package.json
4. **Versão**: Verificar informações do projeto
5. **Testes**: Executar `npm test`
6. **Build**: Executar `npm run build`
7. **Estrutura**: Validar estrutura do projeto
8. **Branch específico**: Executar validações específicas do tipo de branch
9. **Notificação**: Exibir resultado final

### 3. Verificando resultados

1. Acesse o repositório no GitHub
2. Vá para a aba "Actions"
3. Você verá o workflow "Universal CI/CD" executando
4. Clique no workflow para ver os detalhes da execução

### 4. Scripts de teste local

Antes de fazer push, você pode testar localmente:

```bash
# Testar scripts individualmente
npm test
npm run build
npm start

# Verificar estrutura do projeto
ls -la
ls -la src/
```

## 🎯 Tipos de Branch Detectados

O workflow reconhece automaticamente:

### 🆕 Feature Branches (`feature/*`)
```bash
git checkout -b feature/nova-funcionalidade
```
- Executa validações para novas funcionalidades
- Logs identificam como "Feature branch"

### 🔧 Fix Branches (`fix/*`)
```bash
git checkout -b fix/correcao-bug
```
- Executa validações de correção
- Adiciona verificações de segurança
- Logs identificam como "Fix branch"

### 🏠 Main/Master Branches
```bash
git checkout main  # ou master
```
- Executa validações de produção
- Logs identificam como "Main branch"

### 🚧 Development Branches (`develop/*`, `dev/*`)
```bash
git checkout -b develop
```
- Executa validações de desenvolvimento
- Logs identificam como "Development branch"

### 🔀 Outras Branches
```bash
git checkout -b qualquer-nome
```
- Executa validações padrão
- Logs identificam como "Generic branch"

## ⚡ Vantagens do Workflow Universal

- **Simplicidade**: Um único arquivo de workflow
- **Flexibilidade**: Funciona com qualquer nome de branch
- **Eficiência**: Usa apenas Node.js 20.x
- **Inteligência**: Detecta tipo de branch automaticamente
- **Robustez**: Funciona com ou sem dependências
- **Clareza**: Logs detalhados e informativos
