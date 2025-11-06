# Tradução Português-BR para ModernWMS

Este diretório contém o arquivo de tradução para Português do Brasil (pt-BR).

## Arquivo

- **pt-br.json**: Tradução completa da interface do ModernWMS para Português-BR

## Estrutura do Arquivo

O arquivo está organizado em módulos:

```
{
  "base": {
    "commodityCategorySetting": {...},
    "commodityManagement": {...},
    "companySetting": {...},
    "customer": {...},
    "freightSetting": {...},
    "ownerOfCargo": {...},
    ...
  },
  "login": {...},
  "system": {...},
  "router": {...},
  ...
}
```

## Como Editar

1. Abra o arquivo `pt-br.json`
2. Localize a chave que deseja traduzir
3. Modifique apenas o valor (texto à direita), nunca a chave
4. Salve o arquivo
5. Recompile o frontend: `npm run build`

## Exemplo

```json
{
  "customer_name": "Nome do Cliente"  // ✅ Correto
  "customer_name": "Client Name"      // ❌ Errado (não traduzido)
  "nome_cliente": "Nome do Cliente"   // ❌ Errado (chave modificada)
}
```

## Contribuindo

Se você encontrar erros de tradução ou termos que podem ser melhorados:

1. Edite o arquivo pt-br.json
2. Faça commit: `git commit -m "fix: Corrige tradução de [termo]"`
3. Push: `git push origin master`

## Terminologia

Termos técnicos de logística usados:

- **SKU**: Unidade de Manutenção de Estoque
- **ASN**: Aviso de Remessa Antecipada
- **WMS**: Sistema de Gerenciamento de Armazém
- **Picking**: Separação
- **Packing**: Embalagem
- **Inbound**: Entrada/Recebimento
- **Outbound**: Saída/Expedição

---

**Última atualização**: 06/11/2025
