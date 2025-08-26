# Guia de Teste dos Workflows

## Como testar os workflows criados

### 1. Testando workflow de feature branch

```bash
# Criar e mudar para uma branch feature
git checkout -b feature/test-workflow

# Fazer uma pequena alteração
echo "// Teste de feature" >> src/index.js

# Commit e push
git add .
git commit -m "Adiciona teste de feature workflow"
git push origin feature/test-workflow
```

### 2. Testando workflow de fix branch

```bash
# Criar e mudar para uma branch fix
git checkout -b fix/test-workflow

# Fazer uma pequena correção
echo "// Fix implementado" >> src/index.js

# Commit e push
git add .
git commit -m "Implementa fix de teste"
git push origin fix/test-workflow
```

### 3. Verificando resultados

1. Acesse o repositório no GitHub
2. Vá para a aba "Actions"
3. Você verá os workflows executando automaticamente
4. Clique em cada workflow para ver os detalhes da execução

### 4. Scripts de teste local

Antes de fazer push, você pode testar localmente:

```bash
# Testar scripts
npm test
npm run build

# Verificar se tudo está funcionando
npm start
```

## Estrutura dos Workflows

### Feature Branch CI
- ✅ Checkout do código
- ✅ Setup do Node.js (versões 18.x e 20.x)
- ✅ Instalação de dependências
- ✅ Verificação da versão
- ✅ Execução de testes
- ✅ Processo de build
- ✅ Validação de artefatos

### Fix Branch CI
- ✅ Todas as etapas do Feature Branch CI
- ✅ Verificações de segurança adicionais
- ✅ Notificações específicas para fixes

### General CI/CD
- ✅ Validação para branches principais (main/develop)
- ✅ Testes e build simplificados
