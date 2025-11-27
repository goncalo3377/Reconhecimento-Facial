Tirar fotos de vários ângulos, e vários ângulos de luz, 2 distância
augmentation (rotações e cores)


### 8 classes (7+1)

| **0** | **Silva Ribeiro**   |
| ----- | ------------------- |
| 1     | Cruz Marcelino      |
| 2     | Granja dos Anjos    |
| 3     | Videira de Oliveira |
| 4     | Correia da Silva    |
| 5     | Rodrigues Alves     |
| 6     | Gollwitzer Lopes    |
| 7     | Desconhecido        |

- [ ] verificar aplicações de labeling
- https://www.youtube.com/watch?v=r0RspiLG260
Utilizar COLAB PARA TREINAR

## Yolo v12

## **VGG-Face, FaceNet** ou **ResNet**
As arquiteturas de CNNs mais utilizadas para alcançar alta precisão incluem:

### 1. FaceNet (Google)

- **Conceito:** A FaceNet não é um modelo de classificação tradicional. Ela usa uma **função de perda Triplet Loss** para treinar a rede a gerar _embeddings_ de 128 (ou 512) dimensões.
    
- **Precisão:** O objetivo é garantir que a distância euclidiana entre os _embeddings_ de rostos da **mesma pessoa** seja **muito pequena**, e a distância entre _embeddings_ de **pessoas diferentes** seja **muito grande**.
    
- **Vantagem:** É extremamente robusta para tarefas de **verificação** (1:1 - esta foto é da mesma pessoa que esta outra foto?) e **identificação** (1:N - quem é esta pessoa no banco de dados?).
    

### 2. DeepFace (Meta/Facebook)

- **Conceito:** Uma das arquiteturas pioneiras de Deep Learning que demonstrou a capacidade de atingir uma precisão quase humana. Utiliza uma CNN profunda com nove camadas de conexões.
    

### 3. VGG-Face / ArcFace / CosFace

- **Conceito:** São variações ou aprimoramentos de arquiteturas CNN mais profundas (como a VGG ou ResNet) que incorporam modificações na **função de perda** (como a _Additive Angular Margin Loss_ ou _ArcFace_) para aumentar a discriminação entre classes (pessoas) no espaço de _embeddings_.
    
- **Vantagem:** Estas arquiteturas são frequentemente o **estado da arte** em _benchmarks_ públicos de reconhecimento facial, pois forçam os _embeddings_ de rostos da mesma pessoa a se agruparem ainda mais, tornando a separação de identidades mais nítida.
https://www.youtube.com/watch?v=i_MOwvhbLdI
## Landmark Detection



## Criar Rede
pytorch, tensor flow