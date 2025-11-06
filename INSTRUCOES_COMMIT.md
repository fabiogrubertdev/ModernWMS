# Instruções para Commit e Deploy da Tradução PT-BR

## ✅ Arquivos Modificados

Os seguintes arquivos foram criados/modificados para adicionar suporte ao Português-BR:

1. **`frontend/src/languages/langsJson/pt-br.json`** (NOVO) - Arquivo de tradução completo
2. **`frontend/src/languages/method/index.ts`** (MODIFICADO) - Configuração de carregamento de idiomas
3. **`frontend/src/languages/i18n.ts`** (MODIFICADO) - Configuração do Vue I18n

## 📝 Passo 1: Fazer Commit Local

Execute os seguintes comandos no seu terminal:

```bash
# Navegar até o diretório do projeto
cd /caminho/para/ModernWMS

# Verificar o status (os arquivos já devem estar no staging)
git status

# Criar o commit
git commit -m "feat: Adiciona tradução completa para Português-BR (pt-BR)

- Cria arquivo pt-br.json com todas as traduções
- Atualiza method/index.ts para suportar pt-BR
- Atualiza i18n.ts para detectar navegador em pt-BR
- Adiciona suporte à biblioteca vxe-table em pt-BR"
```

## 🚀 Passo 2: Enviar para o GitHub

```bash
# Enviar para o repositório remoto
git push origin master
```

## 🖥️ Passo 3: Atualizar o Servidor (Google Cloud)

Conecte-se ao seu servidor via SSH e execute:

```bash
# Conectar ao servidor
ssh usuario@seu-servidor-gcp

# Navegar até o diretório do projeto
cd /caminho/para/ModernWMS

# Baixar as atualizações do GitHub
git pull origin master

# Navegar até o frontend
cd frontend

# Instalar dependências (caso necessário)
npm install

# Recompilar o frontend
npm run build

# Copiar os arquivos compilados para o Nginx
# (ajuste o caminho conforme sua instalação)
sudo cp -rf dist/* /etc/nginx/html/

# Reiniciar o Nginx
sudo systemctl restart nginx
```

## 🔍 Passo 4: Testar a Tradução

1. Abra o navegador e acesse seu sistema WMS
2. Faça logout se estiver logado
3. O sistema deve detectar automaticamente o idioma do navegador
4. Se seu navegador estiver em pt-BR, a interface aparecerá em português
5. Você também pode mudar o idioma manualmente nas configurações do sistema

## 📋 Verificação de Idioma no Navegador

Para forçar o sistema a usar Português-BR:

1. **Chrome/Edge**: 
   - Configurações → Idiomas → Adicionar "Português (Brasil)"
   - Mover para o topo da lista

2. **Firefox**:
   - Configurações → Geral → Idioma → Escolher "Português (Brasil)"

3. **Ou via Console do Navegador** (F12):
   ```javascript
   localStorage.setItem('language', 'pt-br')
   location.reload()
   ```

## 🐛 Solução de Problemas

### Problema: Idioma não muda

**Solução 1**: Limpar o localStorage
```javascript
// No console do navegador (F12)
localStorage.clear()
location.reload()
```

**Solução 2**: Verificar se os arquivos foram compilados corretamente
```bash
cd frontend
npm run build
```

### Problema: Erro ao compilar

**Solução**: Verificar se o pacote pt-BR do vxe-table existe
```bash
cd frontend
npm list vxe-table
```

Se não existir o locale pt-BR, o sistema usará o inglês como fallback para a biblioteca vxe-table, mas suas traduções customizadas funcionarão normalmente.

## 📊 Estatísticas da Tradução

- **Arquivo**: pt-br.json
- **Tamanho**: 30KB
- **Linhas**: 772
- **Módulos traduzidos**: 
  - Configurações Básicas (base)
  - Login e Registro
  - Sistema
  - Roteador/Menus
  - Gerenciamento de Armazém
  - Gerenciamento de Estoque
  - Entregas e Expedição
  - Relatórios

## 🔄 Próximos Passos

1. Testar todas as telas do sistema
2. Corrigir traduções que não ficaram adequadas
3. Adicionar traduções faltantes (se houver)
4. Documentar o processo para a equipe

## 📞 Suporte

Se encontrar problemas, verifique:
- Logs do Nginx: `sudo tail -f /var/log/nginx/error.log`
- Logs do backend: `cd backend && dotnet ModernWMS.dll`
- Console do navegador (F12) para erros JavaScript

---

**Data**: 06/11/2025  
**Versão**: 1.0  
**Autor**: Implementação Automatizada
