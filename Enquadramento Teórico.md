## Modelos e Estatísticas


## FaceNet

[**FaceNet**](https://en.wikipedia.org/wiki/FaceNet#:~:text=FaceNet%20is%20a%20facial%20recognition,of%20researchers%20affiliated%20with%20Google.) é um sistema de reconhecimento facial desenvolvido por Florian Schroff, Dmitry Kalenichenko e James Philbin, um grupo de pesquisadores afiliados a Google. . O sistema foi apresentado pela primeira vez em [2015 IEEE Conferência sobre Visão Computacional e Reconhecimento de Padrões](https://www.cv-foundation.org/openaccess/content_cvpr_2015/papers/Schroff_FaceNet_A_Unified_2015_CVPR_paper.pdf).

### Embeddings

Este algoritmo utiliza o conceito de *embeddings* (vetor de números) para conseguir diferenciar pessoas.

De uma forma superficial:
- Se tirarmos 10 fotos suas (de frente, de lado, rindo, sério), o FaceNet deve gerar quase os **mesmos números** para todas elas.
    
- Se tirarmos uma foto de outra pessoa, os números devem ser **muito diferentes**.

O resultado é que o reconhecimento facial vira um problema de **Geometria**:

- Rostos similares = Pontos próximos no espaço.
    
- Rostos diferentes = Pontos distantes.

### Triplet Loss

Usa um método de treino chamado **Triplet Loss** (Perda de Trio).

Durante o treino, a rede não olha para uma foto de cada vez. Ela olha para **três** fotos simultaneamente:

1. **Ancora (Anchor):** A foto de referência (ex: Foto A do João).
    
2. **Positivo (Positive):** Outra foto da _mesma_ pessoa (ex: Foto B do João).
    
3. **Negativo (Negative):** Uma foto de uma _pessoa diferente_ (ex: Foto da Maria).
    

**O objetivo do treino:** A rede ajusta os seus pesos matemáticos para garantir que a distância entre a **Âncora** e o **Positivo** seja _menor_ que a distância entre a **Âncora** e o **Negativo**.

Ela repete isso milhões de vezes até aprender a ignorar iluminação, pose e idade, focando apenas na identidade.

### MTCNN (Multi-task Cascaded Convolutional Networks)

O FaceNet não tem capacidade de identificar caras por isso se não houver pré processamento estaremos a comparar também o ambiente (não pretendido).

O MTCNN varre a imagem, encontra o quadrado onde está o rosto e, crucialmente, encontra 5 pontos (olhos, nariz, boca).

## Modificar o FaceNet para Classificação

Até agora, estávamos a usar o FaceNet no modo **Metric Learning** (Comparação):

- **Entrada:** Foto.
    
- **Saída:** Vetor de 128 números.
    
- **Decisão:** Calculamos a distância matemática.
    

O que você quer fazer agora é **Classification** (Classificação):

- **Entrada:** Foto.
    
- **Saída:** Probabilidade (Ex: 99% Pedro, 1% João).
    
- **Decisão:** A própria rede diz quem é.

### 2. A Arquitetura: Como modificar o FaceNet

Para fazer isso, precisamos "operar" o cérebro do FaceNet.

1. **Congelar o "Corpo" (Backbone):** Pegamos no InceptionResnetV1 pré-treinado (vggface2). Não queremos estragar o que ele já sabe sobre o que é uma sobrancelha ou um nariz. Então, "congelamos" esses pesos.
    
2. **Cortar a "Cabeça":** Removemos a última camada que gera os vetores (embeddings).
    
3. **Colocar uma Nova "Cabeça":** Adicionamos uma camada linear simples (Dense/Fully Connected) que tem as **saídas**  (Pedro e João).


|                           | Vantagens                                                          | Desvantagens                                                                         |
| ------------------------- | ------------------------------------------------------------------ | ------------------------------------------------------------------------------------ |
| Classificação (Sua ideia) | Muito preciso com muitas fotos. A resposta é instantânea (0 ou 1). | **Inflexível.** Se entrar uma 3ª pessoa ("Maria"), você tem de re-treinar a rede.    |
| Embeddings (Anterior)     | Flexível. Se entrar a Maria, basta adicionar 1 foto dela ao banco. | Pode ser menos preciso se a iluminação variar muito e não tivermos um bom threshold. |



```mermaid
graph LR
    A[Início] --> B(Processo)

```



