Classificador de Câncer de pele e pigmentações

Sobre o projeto

Este projeto visa tornar mais prático a identificação de manifestações de câncer de pele, visto que em muitos consultórios os mesmos são observados e diagnosticados por um médico apenas, abrindo espaço para subjetividade.

O modelo é treinado para identificar 7 tipos de lesões e cancros, entre eles:

- Melanoma
- Nevos (manchas benignas)
- Dermatofibroma
- Queratose pigmentada benigna
- Bowen pigmentado
- Lesões vasculares
- Carcinoma basocelular


Dataset

Para o projeto foi utilizado o dataset [HAM-10000](https://www.kaggle.com/datasets/kmader/skin-cancer-mnist-ham10000), que contém 10000 imagens de tipos diferentes de lesões dermatológicas, criado para um desafio do ISIC (International Skin Imaging Collaboration) em 2018

![dataset kaggle] (Skin-cancer-classifier/dataset kaggle.png)

Como é possível observar, 67% do dataset é composto por nevos benignos, tornando-o a classe predominante no dataset com 6705 imagens.

![]

Relacionando a metadata com o arquivo CSV foi possível criar uma relação entre as labels, relação esta validada em um [artigo da biblioteca nacional de medicina dos EUA](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC7445643/).

![]

Devido a desigualdade de amostras de Nevos, foi necessário realizar oversampling no dataset para balanceá-lo, o que aumentou o número de imagens de 10000 para mais de 30000.

A arquitetura para extração de características foi o Inception-V3, para utilizá-la foi necessário reformatar todo o dataset para o formato 75x75x3 pois é o formato mínimo que a arquitetura suporta, foram realizados testes com resoluções maiores porém acabavam por esgotar a memória do meu ambiente.

Para o classificador foi utilizado uma camada densa de 512 nodos seguida de uma camada de 7 nodos ativada por softmax para atribuir o resultado à alguma label.

Ao treinar o modelo com 10 epochs o resultado foi 98% de accuracy no dataset de treino e 97% no dataset de validação

![]

Alguns falsos positivos foram encontrados caso a imagem retratasse um melanoma, com o modelo interpretando-os como lesões vasculares ou ceratose benigna

![]
Testes com imagens de fora do dataset

Após realizar testes com o dataset de testes e validação, pedi para um conhecido que estava realizando exames para que pudesse me fornecer as imagens obtidas no laboratório para que eu pudesse realizar testes no modelo.




![]
