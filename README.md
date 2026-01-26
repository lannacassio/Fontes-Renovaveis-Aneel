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
* [**Dashboard**]
* Antes da limpeza, todo o dataset possuia  linhas 3.913.121 linas e 33 colunas.
* **Processo de limpeza:** No processo de limpeza foram feitas:
  * Eliminação de 15 colunas que não são necessárias para a análise;
  * Coluna SigAgente que continha valor vazio foi substituido pela Sigla da empresa contida na coluna NomAgente;
  * Linhas em que tinha o município vazio foram excluídas;
  * Valores vazios foram substituídos da seguinte forma: moda para valores qualitativos e mediana para valores quantitativos;
  * Dados duplicados foram eliminados
  * As colunas tiveram nomes alterados para melhor entendimento;
  * As linhas que continham a data inferior a 2010 foram eliminadas.

>Após a limpeza e consolidação dos dados em uma tabela foram obtidas 3.863.030 linhas e 18 colunas

## Análise e Visualização



# Conclusão e Recomendação

#  Possíveis escolhas para análise mais aprofundada

Para uma análise mais profunda e detalhada seria ideal algumas informações: 

* Conseguir informações se há incentivos regionais para aderir às energias renováveis.
* Entender se há uma relação entre o PIB regional e a utilização de fontes renováveis.
* Fazer uma análise sobre fatores externos, como pandemia, influenciaram a aderência da transição energética.
* Criar modelos temporais para estimar o crescimento da geração nos próximos dois anos.
 
