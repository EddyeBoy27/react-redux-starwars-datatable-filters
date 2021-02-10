# Boas vindas ao repositório do Projeto de Starwars Redux!

## O que foi desenvolvido

Um projeto em React utilizando Redux para controle de estado. A aplicação consiste de uma tabela com informações acerca de todos os planetas existentes no universo fictício da série _Star Wars_. A tabela é alimentada com dados retornados de uma [API](https://swapi.co/documentation) real. Há, também, vários filtros que permitirão a quem usa selecionar e encontrar com facilidade a informação desejada.

---

## Requisitos do projeto

### 1 - Fazer uma requisição para o endpoint `/planets` da API de Star Wars e preencher uma tabela com os dados retornados, com exceção dos da coluna `residents`

A tabela deve ser renderizada por um componente chamado `<Table />`. Os dados recebidos da API devem ser salvos num campo chamado `data` do `store` e é daí que a tabela deve lê-los. A requisição deve ser feita num componente separado do componente da tabela.

### 2 - Sua página deve ter um campo de texto que filtra a tabela para somente exibir planetas cujos nomes incluam o texto digitado

Ele deve atualizar a tabela com os planetas que se encaixam no filtro à medida que o nome é digitado, sem ter que apertar um botão para efetuar a filtragem. Por exemplo, se digitar "Tatoo", o planeta "Tatooine" deve ser exibido. Você deve usar **Redux** para fazer o gerenciamento do estado da aplicação e o texto digitado deve ser salvo num campo `filters: [{ name }]`. Por exemplo:

```javascript
{
  filters: [
    {
      name: 'Tatoo',
    }
  ]
}
```

### 3 - Sua página deve ter um filtro para valores numéricos

Ele funcionará com três seletores:

  - O primeiro deve abrir um dropdown que permita a quem usa selecionar uma das seguintes colunas: `population`, `orbital_period`, `diameter`, `rotation_period` e `surface_water`.
  - O segundo deve determinar se a faixa de valor será `Maior que`, `Menor que` ou `Igual a` o numero que virá a seguir.
  - O terceiro deve ser uma caixa de texto que só aceita números.

A combinação desses três seletores deve filtrar os dados da tabela de acordo com a coluna correspondente e com os valores escolhidos. Por exemplo:
  - A seleção `population | maior que | 100000` - Seleciona somente planetas com mais de 100000 habitantes.
  - A seleção `diameter | menor que | 8000` - Seleciona somente planetas com diâmetro menor que 8000.

Você deve usar **Redux** para fazer o gerenciamento do estado da aplicação. No `store`, esses valores devem ser salvos nos campos `filters [{ numericValues: { column, comparison, value } }]`. Por exemplo:

```javascript
{
  filters: [
    {
      numericValues: {
        column: 'population',
        comparison: 'maior que',
        value: '100000',
      }
    }
  ]
}
```

### 4 - Sua página deverá ser carregada com somente um filtro de valores numéricos

Caso um filtro seja totalmente preenchido, um novo filtro de valores numéricos deve ser carregado. Este novo filtro não deve incluir quaisquer colunas que já tenham sido selecionadas em filtros de valores numéricos anteriores. Caso todas as colunas já tenham sido inclusas em filtros anteriores, não deve ser carregado um novo filtro. Você deve usar **Redux** para fazer o gerenciamento do estado da aplicação.

Por exemplo: O primeiro filtro tem as seguintes seleções: `population | maior que | 100000`. Um segundo filtro deve aparecer após essas seleções serem todas feitas e, no primeiro dropdown deste segundo filtro, a opção `population` deve estar ausente. Se no segundo filtro fosse selecionado `diameter | menor que | 8000`, o estado ficaria assim:

```javascript
{
  filters: [
    {
      numericValues: {
        column: 'population',
        comparison: 'maior que',
        value: '100000',
      }
    },
    {
      numericValues: {
        column: 'diameter',
        comparison: 'menor que',
        value: '8000',
      }
    }
  ]
}
```


### 5 - Cada filtro de valores numéricos deve ter um ícone de `X` que, ao ser clicado, o apaga e desfaz suas filtragens dos dados da tabela

A coluna que este filtro selecionava deve passar a ficar disponível nos dropdowns dos demais filtros já presentes na tela. Você deve usar **Redux** para fazer o gerenciamento do estado da aplicação.

### 6 - As colunas da tabela devem ser ordenáveis de forma ascendente ou descendente

A informação acerca da ordenação das colunas deve ser armazenada nos campos `filters: [{ column: 'Name', order: 'ASC'}]`, o campo column representa o nome da coluna a ordenar e a ordem representa a ordenação, sendo 'ASC' ascendente e 'DESC' descendente. Por padrão, a tabela começa ordenada pela coluna 'Name' em ordem ascendente. Por exemplo:

```javascript
{
  filters: [
    {
      column: 'Name',
      order: 'ASC',
    }
  ]
}
```

Cada requisito mostra em seu exemplo somente os campos do estado relacionados àquele requisito. O resultado final acumulará campos dos vários exemplos.

---
