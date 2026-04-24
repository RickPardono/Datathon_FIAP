# Datathon_FIAP - Passos Mágicos
## Análise de Dados Educacionais e Predição de Risco de Defasagem
## 📋 Sobre o Projeto
Este projeto foi desenvolvido como parte do Datathon - Fase 5 da Pós Tech em Data Analytics da FIAP, com o objetivo de analisar dados educacionais da ONG Passos Mágicos para:

•  Analisar indicadores educacionais (IAN, IDA, IEG, IAA, IPS, IPP, IPV);

•  Avaliar o desempenho e evolução dos alunos ao longo do tempo;

•  Identificar padrões associados à defasagem educacional;

•  Gerar insights estratégicos para melhoria contínua do programa;

•  Desenvolver um modelo preditivo capaz de antecipar alunos em risco; 

•  Construir uma ferramenta prática para uso operacional (Streamlit).

## 📊 Base de Dados
Base educacional fornecida pela ONG Passos Mágicos (2022–2024)

**Local:** data/raw

Contém informações como:

• Indicadores acadêmicos (IDA, INDE);

• Engajamento (IEG);

• Avaliação psicossocial (IPS);

• Avaliação psicopedagógica (IPP);

• Autoavaliação (IAA);

• Indicador de defasagem (IAN);

• Evolução do aluno (IPV);

• Dados demográficos e institucionais.

## 🔧 Feature Engineering

Foram criadas variáveis derivadas para melhorar a capacidade preditiva:

• Variáveis temporais (valores anteriores dos indicadores – *_prev);

• Variação dos indicadores (deltas);

• Tempo de permanência no programa;

• Score de risco exploratório (EDA);

• Flags de valores ausentes.

## 🎯 Variável Alvo (Target)
A variável alvo foi construída com base na evolução da defasagem ao longo do tempo:

• defasagem_futuro: obtida com shift(-1) por aluno  

• target_risco_defasagem = 1 → quando há piora (defasagem_futuro < 0)  

• target_risco_defasagem = 0 → caso contrário 

O modelo prevê se o aluno estará em situação de defasagem no próximo ano.

## 🧪 Estrutura do Repositório
<img width="601" height="399" alt="Captura de tela 2026-04-24 135317" src="https://github.com/user-attachments/assets/23f95ebb-a268-4e9f-87f1-cb9f268ab29e" />

## 🧹 Preparação da Base de Dados (notebook /00_data_preparation.ipynb)

• Padronização dos nomes das colunas;

• Consolidação das três planilhas em uma base única;

• Correção de problemas de tipagem de dados;

• Tratamento de valores especiais ;

• Padronização de variáveis categóricas;

• Criação de variáveis derivadas de fase, defasagem e IAN.

A base final tratada foi salva em: data/processed/base_tratada.csv

## 🔍 Análise Exploratória (notebook/01_eda.ipynb)

• Análise dos indicadores educacionais;

• Evolução do desempenho ao longo do tempo;

• Relação entre engajamento, desempenho e evolução;

• Avaliação da defasagem educacional (IAN);

• Análise de correlação entre variáveis;

• Identificação de padrões e insights.

## 🤖 Modelagem Preditiva (notebook/02_modeling.ipynb)

### 🧱 Pré-processamento dos dados

Foi construído um pipeline utilizando ColumnTransformer para garantir consistência entre treino, teste e aplicação em produção.

Principais etapas:

• Imputação de valores ausentes;

• Padronização de variáveis numéricas;

• Codificação de variáveis categóricas;

• Tratamento de variáveis ordinais;

• Separação dos dados em treino e teste respeitando a ordem temporal.

### 🔍 Modelos Testados:

• Regressão Logística (baseline);

• Random Forest;

• XGBoost.

### 🏆 Modelo Final Selecionado:

XGBoost

O modelo final foi escolhido com base no melhor desempenho preditivo, apresentando:

• Melhor equilíbrio entre precisão e recall na identificação de alunos em risco;

• Capacidade de capturar padrões não lineares;

• Melhor identificação de alunos em risco.

Foi realizada a Validação Cruzada Temporal e Otimização com GridSearch

### 🔥 Resultados do Modelo:

• AUC: 0.85

• Accuracy: 78%

• Precision: 71%

• Recall: 77%

### 📌 Modelo salvo em:
models/model.joblib

## 🌐 Aplicação Web – Streamlit

Aplicação interativa desenvolvida para simulação de risco educacional:

• Inserção de dados do aluno;

• Cálculo automático da probabilidade de risco;

• Interface amigável para uso operacional;

• Apoio à tomada de decisão em tempo real;

• A aplicação transforma o modelo analítico em uma solução prática para uso no dia a dia da ONG.

Link da aplicação: 

## 🎥 Vídeo de Apresentação
Link do vídeo

## 📊 Storytelling

Apresentação analítica e gerencial disponível em:

storytelling/Datathon_FIAP.pptx

## 🚀 Como Executar o Projeto Localmente
🔹 1. Pré-requisitos:

• Python 3.11

• pip atualizado

• Git instalado

🔹 2. Clonar o repositório:

git clone https://github.com/SEU_USUARIO/Datathon_FIAP.git

cd Datathon_FIAP

🔹 3. Criar ambiente virtual:

python -m venv venv

Ativar:

**No Windows:**

venv\Scripts\activate

**No Mac/Linux:**

source venv/bin/activate

🔹 4. Instalar dependências:

pip install -r requirements.txt

🔹 5. Executar a aplicação:

streamlit run app/app.py

## 👤 Autor do Projeto

Ricardo Pardono

rm365874

**Contato:** rpardono@gmail.com
