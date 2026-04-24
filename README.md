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
target_risco_defasagem = 1 → aluno em risco de defasagem futura  
target_risco_defasagem = 0 → aluno sem risco
Criada a partir da defasagem no período seguinte:
• O modelo prevê se o aluno estará em situação de defasagem no próximo ano.

## 🧪 Estrutura do Repositório
Datathon_FIAP/
├── .streamlit/
├── app/
│   └── app.py
├── data/
│   ├── processed/
│   └── raw/
├── models/
│   └── model.joblib
├── notebooks/
│   ├── 00_data_preparation.ipynb
│   ├── 01_eda.ipynb
│   └── 02_modeling.ipynb
├── storytelling/
│   └── Datathon_FIAP.pptx
├── README.md
├── requirements.txt
