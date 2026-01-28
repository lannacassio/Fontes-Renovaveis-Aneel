# Estudo de Caso

## Análise sobre a atualização das fontes energéticas brasileiras
Autor: Cássio Lanna

## Índice

[1. Resumo](#resumo)

[2. Tarefa de negócios](#tarefa-de-negócios)

[3. Dados](#dados)

[4. Processamento e Limpeza](#processamento-e-limpeza)

[5. Análise e Visualização](#análise-e-visualização)

[6. Dashboard](#dashboard)

[7. Conclusão e Recomendação](#conclusão-e-recomendação)

[8. Possíveis escolhas para análise mais aprofundada](#possíveis-escolhas-para-análise-mais-aprofundada)

## Resumo

O mercado de Geração Distribuída (GD) no Brasil atingiu 43,09 milhões de kW instalados, distribuídos em 3,86 milhões de unidades consumidoras (jan/2026). Este estudo analisa a base histórica da [ANEEL](https://dadosabertos.aneel.gov.br/) (2009-2026) para identificar padrões de adoção, desigualdades regionais e oportunidades de expansão.
O cenário consiste na análise de dados na demanda de atualização da matriz energética brasileira.

   **Principais Descobertas**:
    
    . Os 5 estados:São Paulo, Minas Gerais, Paraná, Rio Grande do Sul, Mato Grosso possuem ~51% de toda potência energética do país.
    . Sul e Sudeste lideram apesar do Nordeste ter maior potencial solar.
    . Pessoa Física (PF) domina em volume das instalações, mas Pessoa Jurídica (PJ) concentra potência média 6x maior (~48kW vs ~8kW).
    . Apenas 341 instalações em condomínios verticais (<0,01% do mercado).

## Tarefa de Negócios

A ANEEL regulamenta a Geração Distribuída desde 2012 (RN 482), com marco regulatório atualizado pela Lei 14.300/2022. Este projeto busca responder:

    . Quais regiões e perfis de consumidor impulsionam a transição energética?
    . Existe correlação entre potencial solar natural e adoção real?
    . Quais barreiras impedem a universalização do acesso à GD?
    . Como as distribuidoras estão performando na habilitação de conexões?

## Dados

| Característica | Especificação |
| :--- | :--- |
| **Fonte** | ANEEL - Sistema de Geração Distribuída (BIG Brasil) |
| **Arquivo** | [`empreendimento-geracao-distribuida.csv`](https://dadosabertos.aneel.gov.br/dataset/relacao-de-empreendimentos-de-geracao-distribuida)|
| **Dicionário**| [`dm-geracao-distribuida-relacao-de-empreendimentos`](https://github.com/lannacassio/Fontes-Renovaveis-Aneel/blob/main/Arquivos_ANEEL/dm-geracao-distribuida-relacao-de-empreendimentos.pdf)|
| **Período** | Jun/2009 a Jan/2026 (16 anos) |
| **Tamanho original** | 3.913.121 registros, 33 colunas (1,3GB) |
| **Tamanho final** | 3.863.030 registros, 18 colunas |
| **Atualização** | 28/01/2026 |

## Metodologia

**Stack Tecnológico:**:

   . **Limpeza & Análise**: Python 3.13 
   
   . **Visualização**: Matplotlib, Seaborn, Plotly, Power BI (Dashboard Executivo)
   
   . **Versionamento**: Git/GitHub

## Processamento e Limpeza

  **Ações Realizadas**:

  * Eliminação de redundâncias: Removidas 15 colunas não essenciais;
  
  * Tratamento de valores nulos:
  
     * Sigla do Agente: preenchida com sigla extraída do nome da empresa;
     
     * Municípios vazios: exclusão das linhas;
     
     * Dados categóricos: substituição pela moda;
     
     * Dados numéricos: substituição pela mediana;
     
  * Remoção de duplicatas: Registros de atualização histórica consolidados;
  
  * Padronização: Renomeação de colunas para fácil entendimento;
  
  * Filtro temporal: Exclusão de registros anteriores a 2009 (inconsistências históricas).


* Toda a **documentação e script** do trabalho está [aqui](https://github.com/lannacassio/Fontes-Renovaveis-Aneel/blob/main/Arquivo_Python/analise_aneel.ipynb).

>O arquivo csv limpo se encontra [aqui](https://drive.google.com/drive/folders/1b2dd77UNPztNKXTBFmChH3theqQYz3nY?usp=sharing)

## Análise e Visualização

Foram analisados os dados de aproximadamente 3.8 milhões de registros de atualizações no conjunto de dados final. Para observar tendências diferenciadas, foram desenvolvidas visualizações diretamente no Power BI.

### Potência por Região

</head>
<body>
       <table>
              <tr>
                     <td><img src= "https://github.com/lannacassio/Fontes-Renovaveis-Aneel/blob/main/Imagens/regiao.png"></td>
              </tr>
       </table>
</body>
</html>

**Percepções**

* Sudeste detém 33,9% de toda a potência instalada, podendo ser um indicativo de combinação de poder aquisitivo e alta tarifa energética impulsiona adoção;
* Apesar do Nordeste ter maior irradiância solar, o Sul tem mais potência instalada, sugerindo que fatores econômicos/técnicos superam o potencial natural;
*  Baixa penetração do Norte (8,2%) pode indicar desafios logísticos ou defasagem regulatória na Amazônia.


### Potência em relação a Estado e Cidade


![Estado](https://github.com/lannacassio/Fontes-Renovaveis-Aneel/blob/main/Imagens/potencia_estado.png?raw=true) ![Cidades](https://github.com/lannacassio/Fontes-Renovaveis-Aneel/blob/main/Imagens/top_10_cidades.png?raw=true)


| Posição | Cidade | Potencia (kW) | Posição do Estado | Caracteristica |
| :--- | :--- | :--- | :--- | :--- |
| 1ª | Brasília | 521.998 | 21ª | Capital federal, área territorial disponível |
| 2ª | Cuiabá | 422.692 | 5ª | Polo agroindustrial |
| 3ª | Campo Grande | 407.660 | 8ª | Centro-Oeste |
| 10ª | São Paulo | 196.461 | 1ª | Anomalia urbana |


**Percepções**

* Paraná  e Rio Grande do Sul superam expectativas, indicando alta adesão no Sul apesar da menor insolação;
* Predominância do Centro-Oeste sugere correlação com alta insolação e espaço territorial disponível;
* Desigualdade entre São Paulo e Roraima evidencia necessidade de políticas regionais diferenciadas;
* A cidade de São Paulo demanda investigação sobre gargalos regulatórios ou espaciais na capital;
* A cidade de Manaus, apesar de ser a 9ª cidade com maior potência instalada, possui a geração de aproximadamentes 76% de todo o seu estado;
* Diferença entre 1º e 10º colocado das cidades demonstra alta concentracao em poucos municípios.


### Total de Unidades e Média de kW por Instalação

</head>
<body>
       <table>
              <tr>
                     <td><img src= "https://github.com/lannacassio/Fontes-Renovaveis-Aneel/blob/main/Imagens/consumidor_unidades_kw.png"></td>
              </tr>
       </table>
</body>
</html>

| Tipo | Clientes | Unidades | Potencia(%) | Potência Média (kW) | Perfil |
| :--- | :--- | :--- | :--- | :--- |:--- |
| PF | 3.544.754 | 4.911.502 | 64,5% | 7.84 | Residencial compacto |
| PJ | 318.306 | 2.004.425 | 35,4% | 47.98 | Comercial/Industrial |


**Percepções**

* Apesar das unidades adquiridas por PF ser 2 mais numerosa, PJ concentra potência média significativa;
* Média e 8 kW da PF indica projetos mais compactos, tornando uma possibilidade de escolha residencial, enquanto os de PJ dão indicações de modelos comerciais/industriais;
* Diferença de escala pode justificar análises diferenciadas de viabilidade econômica por segmento.


### Potência Instalada por Estado e Tipo de Consumidor

</head>
<body>
       <table>
              <tr>
                     <td><img src= "https://github.com/lannacassio/Fontes-Renovaveis-Aneel/blob/main/Imagens/tipo_consumidor_estado.png"></td>
              </tr>
       </table>
</body>
</html>

**Percepções**

*  Estados industrializados (São Paulo, Minas Gerais, Rio de Janeiro) têm maior participação PJ;
*  Mato Grosso, Goiás e Mato Grosso do Sul com alta PF refletem adoção rural/familiar;
*  Diferença de perfil sugere necessidade de políticas comerciais distintas por estado.




### Classe de Consumidor por Estado

</head>
<body>
       <table>
              <tr>
                     <td><img src= "https://github.com/lannacassio/Fontes-Renovaveis-Aneel/blob/main/Imagens/clase_consumidor_estado.png"></td>
              </tr>
       </table>
</body>
</html>

**Percepções**

* Classe residencial como motor da transição energética distribuída;
* Mato Grosso do Sul, Mato Grosso e Goiás com alto percentual rural confirmam tendência de microgeração no campo.


### Quantidade por Modalidade

</head>
<body>
       <table>
              <tr>
                     <td><img src= "https://github.com/lannacassio/Fontes-Renovaveis-Aneel/blob/main/Imagens/qtd_modalidade.png"></td>
              </tr>
       </table>
</body>
</html>


| Modalidade | Unidades | Potencia Média (kW) | Total(%) | Descrição |
| :--- | :--- | :--- | :--- |:--- |
| Geracao na propria UC | 3.108.064 | ~9,94 | 80,456% | Sistema no mesmo endereço do consumo |
| Auto consumo remoto | 737.774 | ~13,23 | 19,098% | Geração em local diferente, mesma concessionária |
| Compartilhada | 16.881 | ~142,36 | 0,436% | Múltiplos beneficiários de mesma usina |
| Condomínio | 341 | ~12,91 | 0,008% | Geração em áreas comuns de edifícios |


**Percepções**

* Volume significativo de autoconsumo remoto sugere maturidade do mercado para modelos sem geração local;
* Sistema de instalação "rooftop" próprio ainda é o padrão de negócio;
* Apenas 341 instalações em condomínios indica barreira regulatória ou técnica a ser investigada.



### Volume de Conexões por Ano (Transição de Sistema)

</head>
<body>
       <table>
              <tr>
                     <td><img src= "https://github.com/lannacassio/Fontes-Renovaveis-Aneel/blob/main/Imagens/transi%C3%A7%C3%A3o_anual.png"></td>
              </tr>
       </table>
</body>
</html>


|Periodo | Novos Clientes | Potência Instalada (kW) | Crescimento(%) |
| :--- | :--- |:--- | :--- |
|2009-2012 | 123 | 1.514,91 | 0% |
|2013-2016 | 7.248 | 79.553,55 |5.792,68% |
|2017-2020 | 383.662 | 5;036.593,70 |5.193,35% |
|2020-2024 | 2.737.346 | 30.407.352,38 |613,48% |
|2025 | 734.678 | 7.569.013,63 |-73,16% |


**Percepções**

* Anos de 2018-2024 representam fase de rápida disseminação tecnológica;
* Anos de 2021-2022 mostram alto crescimento ao ano, período de transição energética acelerada;
* Queda 2025 requer investigação para entender se ocorreu mudança regulatória.


## Dashboard

Para análises interativas detalhadas, desenvolvi um dashboard em Power BI segmentado em três visões:

**Visão Panorâmica**

    . KPIs: 43,09 Mi kW totais, 3,86 Mi unidades
   
    . Ranking de distribuidoras: CEMIG (MG), COPEL (PR) e CPFL (SP) lideram em adesão
   
    . Distribuição por tipo de geração (UFV domina com >99%)

**Visão Regional**

    . Mapa de calor: Concentração no Sudeste e Sul
   
    . Análise por estado: Cross-data de classe consumidor vs. tarifa
   
    . Top distribuidoras: Performance por região de concessão

**Visão de Tendências**
  
    . Comparativo de instalação: Modalidade dos consumidores
   
    . Projeção: Indicadores de crescimento mês a mês
   
    . Comparativo Consumidor: Comparação dos consumidores e a tensão instalada
   
Baixar [Dashboard](https://github.com/lannacassio/Fontes-Renovaveis-Aneel/tree/main/Arquivo_Power_BI) Completo ([PDF](https://github.com/lannacassio/Fontes-Renovaveis-Aneel/tree/main/Arquivo_Power_BI))
(Desenvolvido em Power BI Desktop - dados atualizados jan/2026)


# Conclusão e Recomendação

* Há uma dominância da energia solar, enquanto há pouco investimento nas demais escolhas.
* O volume de investimento é liderado por Pessoas Físicas, que corresponde a aproximadamente 65% da potência total instalada.
* A região Sudeste lidera o rank com maior capacidade instalada.
* A "Geração na própria Unidade Consumidora" é a modalidade mais madura, mas o Autoconsumo Remoto já demonstra uma fatia significativa de mercado, indicando uma descentralização da geração.
* **Recomendações**:
    * Empresas de instalação devem priorizar o seguimento PJ(Pessoa Jurídica), dado sua representatividade financeira e possibilidade maior da potência média.
    * Municípios com alta incidência solar e baixa densidade de usinas, representam uma nova frente de vendas, especialmente fora do eixo Minas-São Paulo.
    * O alto volume de conexões residiciais exige um maior monitoramente das distribuidoras para evitar sobrecargas, abrindo espaço para soluções de armazenamento de energia.
    * Focar em nichos de segmentos emergentes como instalação em Condomínos, modelo pouco explorado.
    * Criar políticas diferenciadas para Norte e Nordeste (menor poder aquisitivo, maior potencial solar).

#  Possíveis escolhas para análise mais aprofundada

Para uma análise mais profunda e detalhada seria ideal algumas informações: 
* Estimar tempo de retorno do investimento por estado (considerando insolação + tarifa local)
* Cruzar tarifas de energia por distribuidora com velocidade de adoção da GD.
* Conseguir informações se há incentivos regionais para aderir às energias renováveis.
* Entender se há uma relação entre o PIB regional e a utilização de fontes renováveis.
* Fazer uma análise sobre fatores externos, como pandemia, influenciaram a aderência da transição energética.
* Criar modelos temporais para estimar o crescimento da geração nos próximos dois anos.
* Entender se algo influencia a pouca aderência da região Norte ao implementar as fontes renováveis.
 
