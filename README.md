Projeto: Modelagem Dimensional - Star Schema (Dados Financeiros)

![Diagrama do Star Schema](imagem/Esquema_estrela.png)

O Desafio e Objetivo
Este projeto tem como objetivo demonstrar a transformação de uma base de dados plana e desnormalizada em um modelo relacional do tipo Star Schema (Esquema em Estrela), otimizado para análises de Business Intelligence no Power BI.

O Ponto de Partida
Originalmente, o modelo contava com apenas uma tabela chamada financias. Essa tabela funcionava como um "tabelão" contendo absolutamente todos os dados misturados: transações, dados dos produtos, faixas de desconto e datas. Embora comum, esse formato gera redundância de dados, dificulta a manutenção e não é performático para o mecanismo do Power BI.

Processo de Modelagem (ETL)
Para transformar essa base única em um modelo estrela robusto, apliquei técnicas de ETL (Extração, Transformação e Carga) via Power Query e modelagem em DAX:

Derivação de Dimensões: A tabela financias original foi utilizada como consulta base para ramificar e criar tabelas de dimensões focadas em contextos específicos.

Garantia de Chaves Únicas: Aplicação de remoção de duplicatas na coluna ID_Produto para garantir a integridade referencial do lado "1" dos relacionamentos (1:*).

Mesclagem de Consultas: Consolidação de atributos espalhados (como Manufacturing Price) diretamente na tabela Dimensão de Produtos.

Inteligência de Tempo: Criação de uma tabela D_Calendario automatizada via DAX (CALENDARAUTO()), permitindo análises temporais ricas (Ano, Mês, Trimestre).

Estrutura do Star Schema
O modelo final possui uma estrutura clara, onde os fatos (eventos) ocorrem no centro e são filtrados pelas dimensões (cadastros):

F_Vendas (Fato): Coração do modelo, armazenando métricas variáveis como Unidades Vendidas, Preço de Venda, Descontos e Lucro.

D_Produtos (Dimensão): Tabela de cadastro único listando o portfólio de produtos e seus custos de manufatura.

D_Descontos (Dimensão): Detalhamento das faixas de descontos e classificações.

D_Calendario (Dimensão): Tabela de datas contínua ligada às datas das transações.

D_Detalhes (Dimensão): Dimensão de apoio contendo segmentações, países e outras características contextuais.

## Tecnologias Utilizadas

Para o desenvolvimento deste projeto, as seguintes ferramentas e linguagens foram aplicadas:

*   **Power BI Desktop:** Ferramenta principal para modelagem, relacionamento e visualização.
*   **Power Query (Linguagem M):** Utilizado no processo de ETL para mesclar tabelas, remover duplicatas, agrupar dados e criar as tabelas dimensão a partir da base original.
*   **DAX (Data Analysis Expressions):** Utilizado para a criação da tabela de datas inteligente (`dCalendario`) e estruturação de medidas e colunas calculadas.
*   **Modelagem Dimensional:** Aplicação de conceitos de Business Intelligence para construção da arquitetura Star Schema. 

### Passos para visualização
1. Faça o clone deste repositório ou baixe o arquivo `.zip` clicando em *Code > Download ZIP*.
2. Extraia os arquivos e localize o arquivo principal do projeto com a extensão `star_Schema_financias.pbix`.
3. Dê um duplo clique no arquivo para abri-lo no Power BI Desktop.
4. Para visualizar o **Star Schema** que foi construído, clique no ícone de **Exibição de Modelo** (o terceiro ícone no menu lateral esquerdo, com formato de diagrama).
5. (Opcional) Caso queira ver as transformações de ETL feitas, clique em **Transformar Dados** na guia Página Inicial para abrir o Power Query.

---
