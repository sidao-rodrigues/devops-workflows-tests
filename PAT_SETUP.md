# 🔑 Configuração de Personal Access Token (PAT)

## ❓ Por que usar PAT?

O `GITHUB_TOKEN` padrão tem limitações de segurança que impedem a criação automática de Pull Requests. Um Personal Access Token (PAT) pode contornar essas limitações.

## 🚀 Como Configurar

### 1. **Criar Personal Access Token**

1. Acesse: https://github.com/settings/tokens
2. Clique em **"Generate new token"** → **"Generate new token (classic)"**
3. Configure as permissões:
   - ✅ `repo` (Full control of private repositories)
   - ✅ `workflow` (Update GitHub Action workflows)
4. Defina um nome descritivo: `devops-workflows-pr-automation`
5. Defina expiração conforme sua política
6. Clique em **"Generate token"**
7. **COPIE O TOKEN** (só aparece uma vez!)

### 2. **Adicionar Secret no Repositório**

1. Vá para: `Settings` → `Secrets and variables` → `Actions`
2. Clique em **"New repository secret"**
3. Name: `PAT_TOKEN`
4. Value: Cole o token gerado
5. Clique em **"Add secret"**

## 🎯 Como Funciona

### **Com PAT configurado:**
```yaml
# O workflow tentará criar PR automaticamente
✅ Criação automática de PR
🎉 Sucesso total da automação
```

### **Sem PAT (fallback):**
```yaml
# O workflow fornecerá instruções manuais
📋 Instruções detalhadas para criar PR
🔗 Links diretos para criação
```

## ⚡ Benefícios do PAT

- ✅ **Automação Completa**: PRs criados automaticamente
- ✅ **Fallback Inteligente**: Funciona sem PAT também
- ✅ **Segurança**: Token com escopo limitado
- ✅ **Flexibilidade**: Pode ser revogado a qualquer momento

## 🔒 Segurança

- Use tokens com **escopo mínimo** necessário
- Configure **expiração** adequada
- **Revogue** tokens não utilizados
- **Não compartilhe** tokens em código

## 🧪 Teste

Após configurar, faça um push em uma branch `feature/*` e verifique se o PR é criado automaticamente!
