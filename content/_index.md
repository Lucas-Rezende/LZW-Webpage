---
title: File-Compressor-LZW

type: landing

sections:
  - block: markdown
    content:
      title: File-Compressor-LZW
      subtitle: 'Lucas Momede Barreto Rezende, Luiza Sodré Salgado'
      text: >
        <p>Este projeto apresenta a implementação de um compressor de dados baseado no algoritmo LZW (Lempel–Ziv–Welch), sendo capaz de comprimir e descomprimir arquivos através da eliminação de duplicatas, proporcionando uma representação mais compacta do dado original. Para tratar o conceito de duplicatas em um arquivo, também foi usada a estrutura de dados Trie Compacta, a fim de ser usada como dicionário no LZW.

  - block: features3
    content:
      items:
        - name: LZW
          description: LZW (Lempel-Ziv-Welch) é um algoritmo de compressão de dados baseado na leitura e no armazenamento dos padrões de uma sequência.
          icon: compress
          icon_pack: custom
        - name: Trie Compacta
          description: Tries compactas são estruturas que reduzem o número de nós, unindo aqueles que tem prefixos em comum.
          icon: code
          icon_pack: custom
  
  - block: markdown
    content:
      title: Introdução
      text: >
        <p>Para entender melhor a problemática, é importante levar em consideração a relevância de se comprimir um arquivo e qual tipo de compressão usar (Lossless ou Lossy). Sabemos que tanto o armazenamento quanto o tempo são recursos limitados, o que impulsiona a busca por algoritmos mais eficientes para resolver problema. Já para o armazenamento, as técnicas de compressão de dados se tornam essenciais , pois a compressão oferece uma solução eficaz para otimizar o uso do espaço de armazenamento. Nesse sentido, há dois tipos principais de compressão, Lossless e Lossy, a primeira permite que nenhuma informação seja perdida durante o processo, enquanto a segunda remove informação de fato (se considerada desnecessária).<p>
        <br><hr>

  - block: markdown
    content:
      title: Trie Compacta
      text: >
        <p>A implementação da compressão e descompressão de arquivos fez uso da estrutura de dados Compact Trie como um dicionário. A trie foi escolhida por sua capacidade eficiente de armazenar e acessar sequências de símbolos lidas no arquivo, permitindo uma rápida identificação de padrões já encontrados através do método de busca (search). Na implementação, cada nó da trie é representado pela classe Node, que contém uma chave (ou conteúdo), uma marcação indicando se o nó representa o final de uma palavra (campo isEndOfWord), um código associado ao nó (para realizar a substituição durante a compressão) e uma coleção de nós filhos.

  - block: image-gallery
    custom_id: 'minha-galeria'
    content:
      images:
        - filename: node.png

  - block: markdown
    content:
      title:
      text: >
        <p>Em relação a Trie Compacta em si, ela foi implementada utilizando 3 métodos principais: insert, search e cpl. Esses métodos unidos foram responsáveis por, respectivamente, inserir palavras (sequências de bytes) associadas a códigos, realizar buscas para encontrar o código de uma palavra ou prefixo, e calcular o tamanho do prefixo comum entre duas palavras. Além desses, também foram implementados métodos para remover sequências e imprimir a Trie de forma a apresentar melhor a construção dessa estrutura.<hr>

  - block: markdown
    content:
      title: LZW
      text: >
        <p>No contexto desse projeto, o LZW foi o algoritmo de compressão Lossless utilizado. Ele é usado principalmente em arquivos TIFF, GIF, .txt e PDF. A compressão ocorre pelo fato que o LZW é capaz de agrupar símbolos lidos em string e transformá-los em códigos. Cada uma dessas sequências lidas é adicionada ao dicionário i.e a medida que o arquivo é lido, o algoritmo busca no dicionário para substituir sequências repetidas por seus códigos, comprimindo assim os dados. O dicionário inicial é preenchido com os 256 símbolos ASCII e é atualizado conforme novas sequências são encontradas.
        
        
        O LZW tem métodos para compressão (compress), que cria o arquivo comprimido, e descompressão (decompress), que reverte o processo e recupera o arquivo original. Ambos os métodos utilizam um dicionário (ou trie compacta) para mapear sequências de bytes a códigos. O código também permite compressão e descompressão de arquivos com bits não fixos, onde o tamanho dos códigos no dicionário pode crescer até um limite máximo estipulado pelo usuário.
        <br><hr>

  - block: markdown
    content:
      title: Testes práticos
      text: >
        <p>Para validar alguns conceitos do algoritmo, foram feitos alguns testes em imagens .bmp e arquivos .txt e .csv. Todos os arquivos usados para teste estão disponíveis na pasta 'inputs'. Abaixo estão disponíveis alguns casos de teste:
        <br>

  - block: image-gallery
    custom_id: 'minha-galeria'
    content:
      images:
        - filename: analise1.png

  - block: image-gallery
    custom_id: 'minha-galeria'
    content:
      images:
        - filename: analise2.png

  - block: markdown
    content:
      text: >
        <p>Alguns insights importantes que podem ser extraídos dos casos de teste no contexto do algoritmo LZW são: quanto maior a repetição de padrões ou sequências no arquivo, maior tende a ser a eficiência na taxa de compressão. Isso é especialmente evidente nos testes 1 (.bmp) e 5 (.txt), que apresentam padrões repetitivos extensos, permitindo que o dicionário do LZW seja preenchido de forma mais eficiente. Por outro lado, em arquivos mais complexos, que possuem menor repetição, a compressão é reduzida, já que o algoritmo encontra menos oportunidades de reutilizar sequências previamente armazenadas no dicionário.
        <br>

  - block: markdown
    content:
      title: Como utilizar o programa
      text: >
        <p>É possível utilizar tanto o compressor quanto o descompressor baseado no algoritmo LZW, sendo possível usar o número de bits dinâmico ou fixo. Para usá-lo, basta executar o script main.py no terminal, passando o caminho para o arquivo de entrada como argumento. O parâmetro --max_bits permite definir o número máximo de bits para o dicionário (o valor padrão é 12). Ademais, é necessário que o max_bits seja no mínimo 9 para funcionar corretamente.<p>

    design:
      slide_height: ''
      is_fullscreen: true
      loop: false
      interval: 2000
---