# Geração Automática de Legendas para Imagens (Image Captioning)

Este projeto implementa um sistema de geração automática de legendas para imagens utilizando técnicas de aprendizado profundo. A abordagem combina encoders de redes neurais convolucionais pré-treinadas com decoders baseados em LSTM, GRU e Transformer. O desempenho é comparado utilizando a métrica BLEU.

---

## 1. Introdução

A tarefa de *image captioning* tem como objetivo gerar descrições textuais coerentes para imagens. Este trabalho utiliza:

- Encoder baseado em CNN pré-treinada (EfficientNetV2-S ou MobileNetV3-Large)
- Decoder baseado em LSTM, GRU ou Transformer
- Dataset Flickr8k, com 8.000 imagens e cinco legendas por imagem

O objetivo central é comparar diferentes arquiteturas de decodificação, analisando desempenho, fluência e coerência das legendas geradas.

---

## 2. Metodologia

A implementação do sistema envolve três etapas principais.

### 2.1 Pré-processamento das legendas

- Conversão para minúsculas  
- Remoção de pontuação  
- Tokenização  
- Padding das sequências  
- Construção do vocabulário

### 2.2 Processamento das imagens

- Redimensionamento  
- Normalização  
- Aplicação dos transforms oficiais de cada modelo pré-treinado

### 2.3 Dataset e DataLoader

- Uso do dataset Flickr8k  
- Associação de imagens às suas legendas  
- Preparação dos lotes para treinamento e validação

---

## 3. Encoder com EfficientNetV2-S

Nesta etapa são apresentados:

- Download e organização do dataset  
- Preparação das legendas  
- Implementação do Dataset e DataLoader  
- Padronização das sequências  
- Implementação do encoder EfficientNetV2-S  
- Implementação dos três decoders:
  - Decoder LSTM
  - Decoder GRU
  - Decoder Transformer  
- Processo de treinamento  
- Avaliação com BLEU  
- Amostras de legendas geradas

---

## 4. Encoder com MobileNetV3-Large

Implementação equivalente à anterior, substituindo apenas o encoder.

Inclui:

- Reimplementação dos decoders  
- Treinamento com MobileNetV3-Large  
- Comparação das perdas  
- Exemplos de legendas  
- Avaliação com BLEU

---

## 5. Métrica de Avaliação: BLEU

A métrica BLEU é utilizada para comparar as legendas geradas pelos modelos com as legendas reais do dataset.  
Ela considera *n-grams*, penaliza repetições e mede precisão semântica.

---

## 6. Resultados

### 6.1 LSTM
- Legendas simples e bem estruturadas  
- Bom controle de contexto a curto prazo  
- Treinamento estável  

### 6.2 GRU
- Treinamento mais rápido  
- Resultados comparáveis ao LSTM  
- Menor número de parâmetros  

### 6.3 Transformer
- Legendas mais completas  
- Captura melhor dependências de longo alcance  
- Exige mais recursos computacionais  

### 6.4 Comparação EfficientNetV2-S vs. MobileNetV3-Large
- EfficientNetV2-S produziu melhores representações e maior BLEU  
- MobileNetV3-Large é mais leve e rápida, mas com leve queda de desempenho  

---

## 7. Conclusão

O trabalho demonstra que:

- A combinação EfficientNetV2-S + Transformer produziu o melhor desempenho geral.  
- LSTM e GRU são alternativas mais rápidas e com resultados satisfatórios.  
- MobileNetV3-Large é adequada para ambientes com restrição computacional, mas apresenta menor precisão.  

A arquitetura escolhida influencia fortemente a qualidade das legendas geradas e o custo computacional do sistema.

---

## 8. Conteúdo do Notebook

O notebook inclui:

- Implementação completa da pipeline  
- Gráficos de evolução da loss  
- Amostras de legendas geradas  
- Cálculo do BLEU  
- Comparação entre modelos e encoders

