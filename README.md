# Simulação de Ecossistemas em C++ e OpenGL

Este repositório apresenta uma coleção de projetos dedicados à simulação de ecossistemas, explorando a interação entre espécies e o ambiente, além de destacar a importância do equilíbrio ecológico. Cada projeto é uma representação visual e computacional de dinâmicas naturais, utilizando C++ e OpenGL para modelagem e animação.

## Projeto 1: Predador e Presa

No primeiro projeto, implementamos uma simulação onde três elementos principais interagem entre si:

- **Predador**: Representado por um quadrado laranja, busca capturar presas para sobreviver.  
  <img src="https://github.com/user-attachments/assets/3a80dcc7-a057-424e-875c-fc5d9b135741" alt="fox" width="100"/>

- **Presa**: Representada por um quadrado branco, tenta evitar o predador enquanto procura abrigo e alimentação.  
  <img src="https://github.com/user-attachments/assets/7b0bf253-186b-464d-a888-e298ef33c073" alt="sheep" width="100"/>

- **Arbusto**: Representado por um quadrado verde, atua como alimento para as presas e ajuda a manter o equilíbrio do ambiente.  
  <img src="https://github.com/user-attachments/assets/7dd7bbbb-f9da-4379-8580-cefbd8276478" alt="plant" width="100"/>

### Objetivo
Demonstrar o impacto da relação entre predadores e presas em um ecossistema, com ênfase no equilíbrio necessário para que ambas as populações possam coexistir de forma sustentável.

### Confira uma demonstração do projeto em ação!

![Screencast from 2024-10-12 12-57-54](https://github.com/user-attachments/assets/d02b5099-1b02-460d-ace5-8689310e2782)

## Funcionamento das reproduções:

Cada função é responsável por criar uma nova geração de indivíduos baseando-se em atributos de seus "pais", adicionando variações genéticas (mutação) e garantindo que as condições do ambiente sejam respeitadas.

### 1. **Função `gerar_filho_predador`**
   - **Objetivo**: Criar um novo predador (`predadores[i]`) a partir de dois predadores selecionados como "pais".
   - **Validação**: 
     - Garante que os índices fornecidos (`pai`, `mae`, `i`) estão dentro dos limites do vetor `predadores`.
     - Verifica se os predadores "pais" estão vivos antes de prosseguir.
   - **Processo de criação**:
     - **Crossover**: Combina atributos dos pais (velocidade e alcance de visão) tirando a média.
     - **Mutação**: Adiciona pequenas variações aleatórias nos atributos de velocidade e alcance de visão.
     - Define energia inicial e posição do novo predador com base na posição da mãe.
   - **Impacto nos pais**: Reduz a energia dos pais devido ao custo de reprodução.


### 2. **Função `gerar_filho_presa`**
   - **Objetivo**: Criar uma nova presa (`presas[i]`) a partir de dois indivíduos selecionados como "pais".
   - **Validação**:
     - Verifica se os índices estão dentro dos limites do vetor `presas`.
     - Garante que os pais estão vivos.
   - **Processo de criação**:
     - **Crossover**: Combina velocidade e alcance de visão dos pais por meio de média.
     - **Mutação**: Adiciona pequenas variações aleatórias nos atributos de velocidade e alcance de visão.
     - Define energia inicial e posiciona o novo indivíduo nas coordenadas da mãe.
   - **Impacto nos pais**: Deduz energia dos pais pelo custo de reprodução.


### 3. **Função `gerar_arbustinho`**
   - **Objetivo**: Criar um novo arbusto (`arbustos[i]`) a partir de um arbusto "pai".
   - **Validação**:
     - Certifica que o índice do arbusto e do novo filho estão dentro dos limites do vetor `arbustos`.
     - Garante que o arbusto pai está vivo.
   - **Processo de criação**:
     - **Posição do novo arbusto**:
       - **10% de chance**: Atribui uma posição completamente aleatória no mapa.
       - **90% de chance**: Atribui uma posição próxima ao arbusto pai, com variação limitada para manter a proximidade.
       - Garante que a nova posição está dentro dos limites do mapa.
     - Define energia inicial e marca o novo arbusto como vivo.
   - **Impacto no pai**: Reduz a energia do arbusto pai após a reprodução.


### Considerações gerais
1. **Crossover e mutação**:
   - As funções implementam mecanismos simples de herança genética, como a média dos atributos dos pais (crossover) e a adição de variações aleatórias (mutação), promovendo diversidade na população.
   
2. **Validação e segurança**:
   - Verificações garantem que as operações sejam realizadas dentro dos limites e evitem acessar índices inválidos ou entidades não vivas.

3. **Sustentabilidade da reprodução**:
   - A energia dos pais é reduzida como um custo pela reprodução, o que pode influenciar suas chances de sobrevivência no ambiente simulado.

Essas funções são fundamentais para simular a dinâmica de populações em um ecossistema, incorporando conceitos básicos de genética e ecologia.
