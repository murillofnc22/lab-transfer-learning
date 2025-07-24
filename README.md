# Resumo do notebook `transfer_learning.ipynb`

O notebook implementa **Transfer Learning** utilizando um modelo pré-treinado (`ResNet18`) da biblioteca **Torchvision** para realizar classificação de imagens. As principais etapas realizadas foram:

---

## 1. Importação de bibliotecas

Foram importadas bibliotecas como:

- `torch`, `torch.nn`, `torch.optim`, `torchvision`
- `matplotlib.pyplot`, `numpy`, `time`
- Módulos auxiliares para manipulação de imagens e diretórios

---

## 2. Configuração do dataset

- Utilizou-se o dataset de **hymenoptera** (abelhas e formigas).
- Estrutura do diretório com subpastas separadas para `train` e `val`.
- Foram aplicadas transformações nas imagens:
  - **Treinamento**: `RandomResizedCrop`, `RandomHorizontalFlip`, normalização
  - **Validação**: `Resize`, `CenterCrop`, normalização

---

## 3. Carregamento dos dados

- Usou-se `torchvision.datasets.ImageFolder` para carregar as imagens.
- Os datasets foram carregados com `DataLoader` com `batch_size` fixo e `shuffle=True` no treino.

---

## 4. Visualização dos dados

- Algumas imagens do conjunto de treino foram visualizadas com seus rótulos correspondentes.

---

## 5. Transfer Learning com Fine-Tuning

- Carregamento do modelo pré-treinado `ResNet18`.
- Substituição da camada final (`fc`) para uma saída com 2 classes.
- Treinamento completo do modelo com:
  - Função de perda: `CrossEntropyLoss`
  - Otimizador: `SGD`
  - Scheduler para decaimento da taxa de aprendizado
- Avaliação do modelo no conjunto de validação com predições visuais.

---

## 6. Feature Extraction (congelando os pesos)

- Novamente utilizou-se o `ResNet18` pré-treinado.
- Todos os parâmetros do modelo foram congelados (sem gradiente).
- Apenas a última camada foi treinada.
- Repetição do processo de treinamento e avaliação.

---

## Conclusão

O notebook demonstrou duas abordagens comuns de **transfer learning**:
1. **Fine-tuning**: re-treinar todo o modelo.
2. **Feature extraction**: treinar apenas a última camada, mantendo o restante congelado.

Ambas as abordagens foram aplicadas ao dataset de formigas e abelhas, com sucesso visualizado nas predições.
