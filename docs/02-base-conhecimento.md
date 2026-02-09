# Base de Conhecimento

## Dados Utilizados

| Arquivo | Formato | Para que Serve o B_I_J |
|---------|---------|---------------------|
| `historico_atendimento.csv` | CSV | Contextualizar interações anteriores |
| `perfil_investidor.json` | JSON | Personalizar explicações para cada tipo de cliente |
| `produtos_financeiros.json` | JSON | Conhecer os produtos disponiveis para que eles possam ser ensinado aos clientes |
| `transacoes.csv` | CSV | Analisar padrão de gastos do cliente de forma didatica |


---

## Adaptações nos Dados

> Você modificou ou expandiu os dados mockados? Descreva aqui.



---

## Estratégia de Integração

### Como os dados são carregados?
> Descreva como seu agente acessa a base de conhecimento.

duas possibilidade3s, injetar arquivos direto no prompt ou via codigo
```python
import pandas as pd
import json

# CSVs
historico = pd.read_csv('data/historico_atendimento.csv')
transacoes = pd.read_csv('data/transacoes.csv')

# JSONs
with open('data/perfil_investidor.json', 'r', encoding='utf-8') as f:
    perfil = json.load(f)

with open('data/produtos_financeiros.json', 'r', encoding='utf-8') as f:
    produtos = json.load(f)



[ex: Os JSON/CSV são carregados no início da sessão e incluídos no contexto do prompt]
```
### Como os dados são usados no prompt?
> Os dados vão no system prompt? São consultados dinamicamente?
 
[Sua descrição aqui]


## Exemplo de Contexto Montado

> Mostre um exemplo de como os dados são formatados para o agente.

```
Dados do Cliente:
- Nome: João Silva
- Perfil: Moderado
- Saldo disponível: R$ 5.000

Últimas transações:
- 01/11: Supermercado - R$ 450
- 03/11: Streaming - R$ 55
...
```
