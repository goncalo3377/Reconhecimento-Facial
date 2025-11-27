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

