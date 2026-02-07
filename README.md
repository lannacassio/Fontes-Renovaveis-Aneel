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

[9. Feedback](#feedback)

## Resumo

O mercado de Geração Distribuída (GD) no Brasil atingiu 43,09 milhões de kW instalados, distribuídos em 3,86 milhões de clientes (dez/2025). Este estudo analisa a base histórica da [ANEEL](https://dadosabertos.aneel.gov.br/) (2009-2025) para identificar padrões de adoção, desigualdades regionais e oportunidades de expansão.
O cenário consiste na análise de dados na demanda de atualização da matriz energética brasileira.

   **Principais Descobertas**:

   | Métrica | Valor | Destaque |
   | :---| :---| :---|
   | **Potência Total** | 43,09 Mi kW | 5 estados brasileiros possuem ~51% de toda potência instalada |
   | **Unidades Consumidoras** | 3,86 Mi | PF: 71% e PJ: 29% |
   | **Média kW por instalação (PF)** | ~8 kW | Perfil Residencial |
   | **Média kW por instalação (PJ)** | ~48 kW | Perfil comercial/industrial |
   | **Modalidade Dominante** | 80% | Geração na própria UC |
   | **Nicho Menor** | 0,008% | Condomínio (341 unidades) |
   | **Período Analisado** | 2009-2025 | 16 anos |
   | **Crescimento** | 2020-2024 | Período de Grande Expansão |


    
    . Os 5 estados:São Paulo, Minas Gerais, Paraná, Rio Grande do Sul, Mato Grosso possuem ~51% de toda potência energética do país.

## Tarefa de Negócios

A ANEEL regulamenta a Geração Distribuída desde 2012 (RN 482), com marco regulatório atualizado pela Lei 14.300/2022. Este projeto busca responder:

    . Quais regiões e estados concentram a maior potência instalada de geração distribuída renovável?
    . Onde ocorre o maior crescimento ao longo do tempo: regiões consolidadas ou regiões emergentes?
    . O crescimento da geração distribuída está concentrado ou se descentralizando no território nacional?
    . Quem impulsiona a expansão da GD: pessoa física ou pessoa jurídica?
    . Quais classes de consumo apresentam maior dinamismo na adoção de fontes renováveis?
    . Onde está o maior potencial de crescimento futuro da geração distribuída no Brasil?


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


* Toda a **documentação e script** do trabalho em **Python** está [aqui](https://github.com/lannacassio/Fontes-Renovaveis-Aneel/blob/main/Arquivo_Python/analise_aneel.ipynb).

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
* A cidade de Manaus, apesar de ser a 9ª cidade com maior potência instalada, possui a geração de aproximadamente 76% de todo o seu estado;
* Diferença entre 1º e 10º colocado das cidades demonstra alta concentracao em poucos municípios.


### Crescimento médio (%) Anual


![PotenciaAnual](https://github.com/lannacassio/Fontes-Renovaveis-Aneel/blob/main/Imagens/media_crescimento_regiao.png?raw=true)


| Região | Crescimento Anual da Potência (%) | Base Inicial de Potência (kW) | 
| :--- | :--- | :--- |
| Nordeste | 6,33 % | 6 |
| Sul | 2.52 % | 14 |
| Centro Oeste | 2,27 % | 4,08 |
| Norte | 2,24 % | 8,2 |
| Sudeste | 1,54 % | 188,65 |



**Percepções**

* O Nordeste está em uma fase de expansão acelerada;
* Apesar do Sudeste possuir a maior quantidade de potência, ela é a região com o menor crescimento anual, indicando maturidade do mercado;
* Regiões com menor base atual apresentam maiores taxas de crescimento


  

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
| Pessoa Física| 3.544.754 | 4.911.502 | 64,5% | 7.84 | Residencial compacto |
| Pessoa Jurídica| 318.306 | 2.004.425 | 35,4% | 47.98 | Comercial/Industrial |


**Percepções**

* Apesar das unidades adquiridas por Pessoa Física ser mais numerosa, Pessoa Jurídica concentra potência média significativa;
* Média de 8 kW da Pessoa Física indica projetos mais compactos, tornando uma possibilidade de escolha residencial, enquanto os de Pessoa Jurídica dão indicações de modelos comerciais/industriais;
* Diferença de escala pode justificar análises diferenciadas de viabilidade econômica por segmento.



### Evolução da Potência Instalada e Potência Média (%) : PF vs PJ


</head>
<body>
       <table>
              <tr>
                     <td><img src= "https://github.com/lannacassio/Fontes-Renovaveis-Aneel/blob/main/Imagens/evolucao_consumidor.png"></td>
                     <td><img src= "https://github.com/lannacassio/Fontes-Renovaveis-Aneel/blob/main/Imagens/cresc_medio_pfpj.png"></td>
              </tr>
       </table>
</body>
</html>



**Percepções**

* PF apresenta crescimento exponencial sustentado; PJ exibe padrão de linearidade;
* Aumento médio anual PF: 313% vs. PJ: 62% — diferença de 5x na taxa de crescimento tendencial;

### Crescimento Médio Anual (%) da Classe de Consumo

</head>
<body>
       <table>
              <tr>
                     <td><img src= "https://github.com/lannacassio/Fontes-Renovaveis-Aneel/blob/main/Imagens/cresc_medio_classe.png"></td>
              </tr>
       </table>
</body>
</html>

| Classe_consumidor |	Aumento_media_potencia_anual(%) |
| :--- | :--- |
| Comercial |	1,59 % |
| Consumo | Próprio |	2,41 % |
| Iluminação pública | 2,46 % |
| Industrial | 1,90 % |
| Poder Público | 5,91 % |
| REBR | 3,367 % |
| Residencial | 2,19 % |
| Rural | 1,63 % |
| Serviço Público | 1,05 % |


**Percepções**

*  Apesar do pouco investimento, o poder Público lidera com 5,91% ao ano;
*  Iluminação pública (2,46%) e Consumo Próprio (2,41%) praticamente empatados, ambos refletem urbanização e autogeração distribuída crescendo em ritmo similar;
*  Diferença de 4,86 pontos percentuais entre Poder Público (5,91%) e Serviço Público (1,05%). Apesar de ambos serem esferas governamentais, apresentam dinâmicas opostas




### Evolução do Índice de Concentração da Geração Distribuida

</head>
<body>
       <table>
              <tr>
                     <td><img src= "https://github.com/lannacassio/Fontes-Renovaveis-Aneel/blob/main/Imagens/hhi.png"></td>
              </tr>
       </table>
</body>
</html>

    . HHI < 1000 - Mercado Descentralizado
    . HHI > 1000 | HHI < 1800 - Concentração Moderado
    . HHI > 1800 - Mercado Centralizado

  
**Percepções**

* Oscilações brutais 2009-2014, indicando mercado em caos competitivo com entrada e saída massiva de clientes;
* Curva descendente contínua de 2017-2025: de 1.422 para 649 — tendência secular de fragmentação e democratização do acesso à geração distribuída;
* Estagnação em torno de 740-790 de 2021 a 2024 — mercado atinge equilíbrio competitivo com barreiras.


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
                     <td><img src= "https://github.com/lannacassio/Fontes-Renovaveis-Aneel/blob/main/Imagens/periodo.png"></td>
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


### Potencial de Crescimento Futuro da Geração Distribuída no Brasil

| Estado | Ano | kW | Evolução Média da Potência (%) | Evolução da Potência Anual (%) | Desenvolvimento ao longo do tempo | Crescimento da Potência |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| Amapá | 2023 | 33714,39 | 762,990584 | 268,797817 | muito alto | baixa |
| Rio Grande do Norte | 2025 | 75643,91 | 147,968595 | 202,717312 | muito alto | baixa |
| Acre | 2021 | 16611,03 | 147,576331 | 178,305108 | alto | baixa |
| Espírito Santo | 2022 | 202847,95 | 320,880988 | 176,663294 | alto | baixa |
| Roraima | 2023 | 20895,01 | 446,974235 | 172,189526 | alto | baixa |
| Distrito Federal | 2022 | 125174,75 | 129,309490 | 141,470672 | alto | baixa |
| Alagoas | 2022 | 88973,53 | 124,058459 | 135,747925 | alto | baixa |
| Amapá | 2021 | 7210,95 | 762,990584 | 123,301076 | alto | baixa |
| Pará | 2021 | 135786,01 | 341,382297 | 120,932986 | alto | baixa |
| Maranhão | 2021	| 114358,06 | 174,525966 | 107,521757 | alto | baixa |
| Amazonas | 2021 | 28943,58 | 176,017555 | 106,918546 | alto | baixa |
| Acre| 2024 | 46728,37 | 147,576331 | 101,973950 | alto | baixa |


**Percepções**

  * Amapá e Acre apresentaram duas vezes, cada um, crescimento consistente ao longo dos últimos anos;
  * Região Norte demonstra boa possibilidade de crescimento futuro;
  * 2021-2022: anos de ignição para maioria dos estados;
  * 2023-2025: consolidação e desaceleração natural — padrão sugere que "muito alto" é fase temporária de adoção precoce, não sustentável indefinidamente.

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

![Demonstração](https://github.com/lannacassio/Fontes-Renovaveis-Aneel/blob/main/Imagens/dash_gif.gif)

   
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
    * O alto volume de conexões residenciais exige um maior monitoramente das distribuidoras para evitar sobrecargas, abrindo espaço para soluções de armazenamento de energia.
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

 # 💬 Feedback
 
 Sua opinião é muito importante! 
- Encontrou algo que pode ser melhorado?
- Quer me dar dicas?
- Cometi um erro?
- Vamos melhorar este projeto juntos? Adoraria ouvir sua opinião!
- O que você faria de diferente?
- Tem alguma ideia de visualização que ficaria incrível aqui?
- Deixe seu comentário na aba de Discussões. Sua opinião é muito importante!

 👉 [**Clique aqui para deixar seu comentário na aba de Discussões**](https://github.com/lannacassio/Fontes-Renovaveis-Aneel/discussions/1)
