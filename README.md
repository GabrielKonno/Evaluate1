# Projeto de Análise e Modelagem de Dados

## Descrição

Este projeto aborda o ciclo completo de análise de dados, incluindo leitura, limpeza e exploração dos dados, integração de diferentes fontes, modelagem e avaliação inicial do desempenho do modelo. O objetivo é prever o sucesso de campanhas com base em variáveis disponíveis no conjunto de dados, utilizando um classificador de árvore de decisão.

## Estrutura do Projeto

1. **Leitura e Carregamento dos Dados**  
   - Carregamento dos arquivos de dados principais (`DataPrepFinal.csv`, `campaign.csv`, `invested.csv`) para um ambiente de trabalho em Python.
   - Pré-visualização dos dados e análise inicial das colunas e tipos.

2. **Limpeza e Preparação dos Dados**  
   - Remoção de colunas não relevantes ao modelo.
   - Limpeza de dados:
     - Ajustes em colunas numéricas e de data usando regex para padronizar formatos.
     - Conversão de variáveis monetárias e datas para tipos apropriados (`int64` para valores monetários e `datetime` para datas).
   - Criação de variáveis derivadas, como o tempo de duração da campanha (`time_range`), calculado com base na data de lançamento e prazo final.

3. **Integração dos Dados**  
   - Junção dos dados de múltiplas fontes:
     - Integração dos dados das campanhas (`campaign.csv`) e das contribuições (`invested.csv`).
     - Utilização de variáveis dummy para tratar colunas categóricas e transformação de variáveis de localização em valores binários para facilitar o processamento.

4. **Exploração de Dados e Tratamento das Variáveis**  
   - Análise de variáveis categóricas e conversão para variáveis numéricas (dummy variables) usando `pandas.get_dummies`.
   - Transformação da coluna `state` para valores binários (`1` para campanhas bem-sucedidas e `0` para campanhas não bem-sucedidas).

5. **Modelagem dos Dados**  
   - Separação entre variável-alvo (`state`) e variáveis preditoras.
   - Divisão dos dados em conjuntos de treino e teste, com uma proporção de 80% para treino e 20% para teste.
   - Treinamento de um modelo de árvore de decisão (`DecisionTreeClassifier`) para previsão de sucesso das campanhas.

6. **Avaliação e Ajustes no Modelo**  
   - Avaliação inicial do modelo de árvore de decisão e cálculo da acurácia no conjunto de teste.
   - Observação de inconsistências e refatoração do modelo ao remover a variável `usd_pledged_real`, que não estaria disponível em cenários de previsão real.

## Tecnologias e Bibliotecas Utilizadas

- **Pandas** e **NumPy** para manipulação e limpeza dos dados.
- **Scikit-Learn** para divisão dos dados, modelagem e avaliação.
- **Google Colab** como ambiente de desenvolvimento e execução do projeto.

## Como Executar o Projeto

1. Clone o repositório:
   ```bash
   git clone https://github.com/seu_usuario/seu_repositorio.git
   cd seu_repositorio
   ```
2. Instale as dependências:
   ```bash
   pip install -r requirements.txt
   ```
3. Adicione os arquivos de dados (`DataPrepFinal.csv`, `campaign.csv`, `invested.csv`) ao diretório do projeto.
4. Execute o código `evaluation_prático.py` em um ambiente de Jupyter Notebook ou Google Colab para replicar o fluxo de trabalho.

## Observações e Próximos Passos

Durante a avaliação do modelo, foi identificada uma possível interferência da variável `usd_pledged_real` nos resultados de acurácia. Para futuras melhorias:
- Reavaliar o pipeline de dados considerando o `Business Understanding` para garantir a consistência das variáveis.
- Testar outros modelos e ajustes de hiperparâmetros.
- Considerar o impacto de variáveis adicionais que estejam disponíveis para previsões reais.
