# Estudo de Caso

## Análise sobre a atualização das fontes energéticas brasileiras
Autor: Cássio Lanna

## Índice

[1. Introdução](#introdução)

[2. Tarefa de negócios](#tarefa-de-negócios)

[3. Dados](#dados)

[4. Processmento e Limpeza](#processamento-e-limpeza)

[5. Análise e Visualização](#análise-e-visualização)

[6. Conclusão e Recomendação](#conclusão-e-recomendação)

[7. Possíveis escolhas para análise mais aprofundada](#possíveis-escolhas-para-análise-mais-aprofundada)

## Introdução

O cenário consiste na análise de dados na demanda de atualização da matriz energética brasileira.

Os dados foram obtidos pelo site da [ANEEL](https://dadosabertos.aneel.gov.br/) (Agência Nacional de Energia Elétrica), uma empresa brasileira que regula e fiscaliza o setor elétrico, garantindo o fornecimento energético com qualidade e preço justo ao fiscalizar a geração, transmissão, distribuição e comercialização. Também sendo responsável como mediadora entre os consumidores e empresas.

## Tarefa de Negócios

    . Mapear o Panorama Nacional: Identificar que o mercado atingiu.
    . Segmentar o Perfil de Investimento.
    . Identificar Polos com maior atualização da fonte energética.
    . Analisar a Dinâmica Operacional e Temporal.
    . Auditar a Infraestrutura Tarifária.

## Dados

* [Dados históricos](https://dadosabertos.aneel.gov.br/dataset/relacao-de-empreendimentos-de-geracao-distribuida) se encontra no arquivo empreendimento-geracao-distribuida disponível em **csv** retirado no dia 24/01/2026.
* [Dicionário](https://github.com/lannacassio/Fontes-Renovaveis-Aneel/blob/main/Arquivos_ANEEL/dm-geracao-distribuida-relacao-de-empreendimentos.pdf) do banco de dados, contendo a versão 2.3 atualizada em 17/11/2025.
* **Intervalo dos dados para análise**: junho de 2009 a janeiro de 2026 (1,3G).
* O Conjunto de dados possui registros individuais sobre a alteração da fonte energéticas dos locais, incluindo a data, tipo de fonte energética, localização, latitude, longitude, distribuidoras responsável pela transferência, beneficiários, potência instaladas e quantas unidades foram contratadas.

## Processamento e Limpeza


* Os dados foram baixados para o HD local para manipulação e análise usando o **Python**;
* Toda a **documentação e script** do trabalho está [aqui](https://github.com/lannacassio/Fontes-Renovaveis-Aneel/blob/main/Arquivo_Python/analise_aneel.ipynb).
* [**Dashboard**](https://github.com/lannacassio/Fontes-Renovaveis-Aneel/tree/main/Arquivo_Power_BI)
* Antes da limpeza, todo o dataset possuia  linhas 3.913.121 linas e 33 colunas.
* **Processo de limpeza:** No processo de limpeza foram feitas:
  * Eliminação de 15 colunas que não são necessárias para a análise;
  * Coluna SigAgente que continha valor vazio foi substituido pela Sigla da empresa contida na coluna NomAgente;
  * Linhas em que tinha o município vazio foram excluídas;
  * Valores vazios foram substituídos da seguinte forma: moda para valores qualitativos e mediana para valores quantitativos;
  * Dados duplicados foram eliminados
  * As colunas tiveram nomes alterados para melhor entendimento;
  * As linhas que continham a data inferior a 2010 foram eliminadas.

>Após a limpeza e consolidação dos dados em uma tabela foram obtidas 3.863.030 linhas e 18 colunas.

>O arquivo csv limpo se encontra [aqui](https://drive.google.com/drive/folders/1b2dd77UNPztNKXTBFmChH3theqQYz3nY?usp=sharing)

## Análise e Visualização

Foram analisados os dados de aproximadamente 3.8 milhões de registros de atualizações no conjunto de dados final. Para observar tendências diferenciadas, foram desenvolvidas visualizações diretamente no Power BI.

### kW instalados por Tipo de Geração

</head>
<body>
       <table>
              <tr>
                     <td><img src= "https://github.com/lannacassio/Fontes-Renovaveis-Aneel/blob/main/Imagens/tipo_gera%C3%A7%C3%A3o.png"></td>
              </tr>
       </table>
</body>
</html>

**Percepções**
* A energia solar se encontra em primeiro lugar em escolha de fontes renováveis, possuindo aproximadamente 99% do mercado.
* Apesar de escolhas como energia eólica, termelétrica e hidrelétrica, juntas não representam aproximadamente 1% da atualização da fonte energética.

### kW instalados por Tipo de Consumidor

</head>
<body>
       <table>
              <tr>
                     <td><img src= "https://github.com/lannacassio/Fontes-Renovaveis-Aneel/blob/main/Imagens/tipo_consumidor.png"></td>
              </tr>
       </table>
</body>
</html>

**Percepções**
* Pessoa Física(PF) foi responsável pela maior parte da mudança de matriz, detendo aproximadamente 64% das atualizações.
* Apesar de Pessoas Jurídicas(PJ) em muitas vezes possuirem maior capital, detém menor índice de alteração.

### Estados com maior kW instalados

</head>
<body>
       <table>
              <tr>
                     <td><img src= "https://github.com/lannacassio/Fontes-Renovaveis-Aneel/blob/main/Imagens/estado.png"></td>
              </tr>
       </table>
</body>
</html>

**Percepções**
*

### kW instalados por Região

</head>
<body>
       <table>
              <tr>
                     <td><img src= "https://github.com/lannacassio/Fontes-Renovaveis-Aneel/blob/main/Imagens/Regi%C3%A3o.png"></td>
              </tr>
       </table>
</body>
</html>

**Percepções**
*

### Modalidade do Consumo dos kW

</head>
<body>
       <table>
              <tr>
                     <td><img src= "https://github.com/lannacassio/Fontes-Renovaveis-Aneel/blob/main/Imagens/modalidade.png"></td>
              </tr>
       </table>
</body>
</html>

**Percepções**
*

### Atualização das fontes energéticas ao longo do tempo

</head>
<body>
       <table>
              <tr>
                     <td><img src= "https://github.com/lannacassio/Fontes-Renovaveis-Aneel/blob/main/Imagens/mes_ano.png"></td>
              </tr>
       </table>
</body>
</html>

**Percepções**
*

# Conclusão e Recomendação

* Há uma dominância da energia solar, enquanto há pouco investimento nas demais escolhas.
* O volume de investimento é liderado por Pessoas Físicas, que corresponde a aproximadamente 65% da potência total instalada.
* A região Sudeste lidera o rank com maior capacidade instalada.
* A "Geração na própria Unidade Consumidora" é a modalidade mais madura, mas o Autoconsumo Remoto já demonstra uma fatia significativa de mercado, indicando uma descentralização da geração.
* **Recomendações**:
    * Empresas de instalação devem priorizar o seguimento PJ(Pessoa Jurídica), dado sua representatividade financeira e possibilidade maior da potência média.
    * Municípios com alta incidência solar e baixa densidade de usinas, representam uma nova frente de vendas, especialmente fora do eixo Minas-São Paulo.
    * O alto volume de conexões residiciais exige um maior monitoramente das distribuidoras para evitar sobrecargas, abrindo espaço para soluções de armazenamento de energia.

#  Possíveis escolhas para análise mais aprofundada

Para uma análise mais profunda e detalhada seria ideal algumas informações: 

* Conseguir informações se há incentivos regionais para aderir às energias renováveis.
* Entender se há uma relação entre o PIB regional e a utilização de fontes renováveis.
* Fazer uma análise sobre fatores externos, como pandemia, influenciaram a aderência da transição energética.
* Criar modelos temporais para estimar o crescimento da geração nos próximos dois anos.
* Entender se algo influencia a pouca aderência da região Norte ao implementar as fontes renováveis.
 
