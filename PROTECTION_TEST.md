# Teste da Proteção da Branch Main

## ⚠️ Simulação de Tentativa de Push Direto na Main

Se alguém tentar fazer push direto na main, o workflow irá:

### 1. **Detectar a tentativa**
```yaml
if: github.event_name == 'push' && (github.ref == 'refs/heads/main' || github.ref == 'refs/heads/master')
```

### 2. **Executar job de bloqueio**
```bash
🚫 ==================================
❌ PUSH DIRETO NA MAIN BLOQUEADO!
==================================
🛡️ Por segurança, pushes diretos na branch main/master não são permitidos.

📋 Para fazer alterações na main, siga este processo:
1. 🌿 Crie uma nova branch: git checkout -b feature/minha-alteracao
2. 💾 Faça suas alterações e commit
3. 📤 Push da branch: git push origin feature/minha-alteracao
4. 🔄 Abra um Pull Request no GitHub
5. ✅ Após aprovação, merge via Pull Request
==================================
```

### 3. **Falhar o workflow com exit 1**

## ✅ Como Testar a Proteção

### Teste 1: Push em branch normal (deve funcionar)
```bash
git checkout -b test-branch
echo "teste" > test.txt
git add test.txt
git commit -m "Teste em branch normal"
git push origin test-branch
# ✅ Deve executar o workflow normalmente
```

### Teste 2: Pull Request para main (deve funcionar)
```bash
# Após o teste 1, abra um PR de test-branch para main
# ✅ Deve executar o workflow com validações de produção
```

### Teste 3: Tentativa de push direto na main (deve bloquear)
```bash
git checkout main
echo "alteracao" > file.txt
git add file.txt
git commit -m "Tentativa de push direto"
git push origin main
# ❌ Deve ser bloqueado pelo workflow
```

## 🔧 Configuração Atual

- ✅ Workflow configurado para bloquear pushes diretos na main
- ✅ Pull Requests para main são permitidos
- ✅ Todas as outras branches funcionam normalmente
- ✅ Mensagens claras de orientação
- ✅ Jobs separados para bloqueio e CI/CD normal

## 📊 Status dos Triggers

| Evento | Branch | Resultado |
|--------|--------|-----------|
| push | qualquer (exceto main) | ✅ Executa CI/CD normal |
| push | main | ❌ Executa job de bloqueio |
| pull_request | qualquer → qualquer | ✅ Executa CI/CD normal |
| pull_request | qualquer → main | ✅ Executa CI/CD com validações de produção |
