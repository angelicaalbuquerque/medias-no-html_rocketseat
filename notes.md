## Videos

Para utilizar vídeos no HTML, utilizamos a tag `<video></video>`, sendo importante o atributo `src` contendo o caminho para o vídeo a ser incorporado.

Con a propriedade `controls`, incluo os controles de play, pause, timeline, audio e outras configs do video.

### E se não funcionar?

Dentro da própria tag de vídeos, podemos colocar um conteúdo informativo. Por exemplo:

```html
<video src="../assets/video/hello-world-video.mp4" controls>
  <p>Este browser não suporta vídeo.</p>
</video>
```

Além disso, podemos alterar as tags `source`. Às vezes, o browser pode estar querendo rodar o vídeo, mas o container não funciona em certo browser.

```html
<video controls>
  <source src="../assets/video/hello-world-video.mp4" type="video/mp4" />
  <p>Este browser não suporta vídeo.</p>
</video>
```

Na documentação oficial da Mozilla, existe um <a href="https://developer.mozilla.org/en-US/docs/Web/Media/Formats">guia de utilização de tipos de vídeo e formatos</a>.

### Serviços de terceiros

Hoje em dia, temos várias plataformas, como Vimeo e YouTube, que já preparam toda a estrutura para hospedarem o vídeo de forma gratuita e apenas gerarem um código ou link para ser inserido à página. A vantagem é não gastar recursos/banda do nosso servidor.

### Outras tags

autoplay: começa tocando o vídeo;<br>
preload="auto": começa a fazer a leitura do vídeo de maneira automatizada, antes da pessoa clicar e começar a baixar; <br>
preload="metadata": só carrega o básico para entender o que tem no vídeo, como por exemplo, tamanho; <br>
preload="none": não carrega nada até clicar no botão; <br>
loop: ao chegar no final do vídeo, tocará o vídeo novamente -- mas isso depende do navegador; <br>
muted: o vídeo começa mutado. <br>
poster: uma imagem que serve como "capa" do vídeo antes dele começar.

## Audio

Muito semelhante à tag video.

```html
<audio controls loop muted autoplay>
  <source src="../assets/audio/Louie Zong - hello world.mp3" type="audio/mp3" />
  <p>Este browser não suporta áudio.</p>
</audio>
```

Através do JavaScript, entretanto, conseguimos fazer controles muito avançados com áudios. Além de que também conseguimos conseguir de outro local o áudio, como SoundCloud.

## Iframes

Inline Frame Element é um elemento que vai trazer conteúdo externo.

```html
<iframe src="" frameborder="0"></iframe>
```

`frameborder` é para falar se vai ter borda ou não no frame e src é a fonte do conteúdo.

Num vídeo incorporado do Youtube, os atributos são geralmente altura, largura, fonte, borda e allow.

```html
<iframe
  width="560"
  height="315"
  src="https://www.youtube.com/embed/Yw6u6YkTgQ4"
  title="YouTube video player"
  frameborder="0"
  allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture"
  allowfullscreen
></iframe>
```

O allow são atributos específicos de configurações da página de onde estamos buscando o conteúdo.

Uma boa prática é incluir também a tag Title para ajudar na Acessibilidade. `title="Vídeo de computador cantando Hello World"`.

Podemos fazer isso (incorporação via iframe) com vídeo, áudio, mapa...

Para mais detalhes sobre Iframes e seus atributos, clique <a href="https://developer.mozilla.org/pt-BR/docs/Web/HTML/Element/iframe">aqui</a>.

## Imagens

Usando a tag `img`, o Emment pelo menos coloca o básico que vamos precisar de imagens, o `src` (que vai apontar onde está a imagem) e o `alt` (se a imagem não é achada por algum motivo, alt vai mostrar um texto alternativo). Por exemplo:

```html
<img
  src="https://source.unsplash.com/random"
  alt="Imagem aleatória do Unsplash"
/>
```

Inserindo mais atributos:

```html
<img
  src="https://source.unsplash.com/random"
  alt="Imagem aleatória do Unsplash"
/>
<a href="https://unsplash.com/">
  <img
    src="https://source.unsplash.com/random"
    alt="Imagem aleatória do Unsplash"
    title="Colocar um título na imagem"
    width="500px"
    height="auto"
  />
</a>
```

### Imagens via CSS

outro jeito de adicionar imagens é via CSS. Por exemplo:

```html
<p
  style="background-image: url(../assets/image/christopher-gower-m_HRfLhgABo-unsplash.jpg);"
>
  Imagem
</p>
```

Mas background-image é utilizado somente para estilo, não é semântico e falta significado. Para isso, o recomendado é utilizar `<figure>`e `<figcaption>`.

### Figure

Uma forma de criar títulos visíveis para as imagens seria inserindo uma tag `<p>` depois da imagem. Entretando, continuaria com o problema de falta de semântica:

```html
<div class="figure">
  <a href="https://unsplash.com/">
    <img
      src="https://source.unsplash.com/random"
      alt="Imagem aleatória do Unsplash"
      title="Colocar um título na imagem"
      width="250px"
      height="auto"
    />
  </a>
  <p>Imagem extraída do Unsplash</p>
</div>
```

Tranformando essa `div` em uma tag `<figure>`, resolve o problema, substituindo ainda a tag `<p>` por `<figcaption>`:

```html
<a href="https://unsplash.com/">
  <figure>
    <img
      src="https://source.unsplash.com/random"
      alt="Imagem aleatória do Unsplash"
      title="Colocar um título na imagem"
      width="250px"
      height="auto"
    />

    <figcaption>Imagem extraída do Unsplash</figcaption>
  </figure>
</a>
```

Assim, o HTML já entende que há uma relação entre a _caption_ e a imagem.

### SVG

É uma marcação, estilo HTML, mas não é para textos e sim para fazermos imagens.

Para entender melhor imagem rasterizada e imagem vetorizada:

- rasterizada: imagem pixelada, construída via pixels.Em cada grid eu tenho um pixel e, assim, a imagem é montada, pixel a pixel. Quanto maior a densidade, mais detalhada é a imagem. <br><br>
- vetorizada: imagem feita via algoritmo, com processamento bem diferente, tendo benefícios e desvantagens.

Benefícios:

- Mais leve;
- Mais detalhada (se der zoom, não vê pixels, mas sim mais detalhes);
- Não perde a qualidade;
- Maior acessibilidade e SEO (já que é todo escrito);
- Pode ser editada via CSS ou atributos.

Desvantagens:

- Pode ser mais complicado de trabalhar;
- Quanto mais complexa a imagem, mais trabalho para o navegador;
- Navegadores mais antigos não possuem suporte a essa tag.

Para fotografias, ainda é melhor utilizar imagens rasterizadas (.png, .jpg, .jpeg).

Apesar de ter programas específicos onde você pode criar arquivos svg, como Illustrator e Figma, você pode escrevê-lo à mão também.

Por exemplo, o svg escrito de um círculo:

```html
<svg
  version="1.1"
  baseProfile="full"
  xmlns="http://www.w3.org/2000/svg"
  width="100"
  height="100">
  <circle
    cx="50"
    cy="50"
    r="40"
    stroke="pink"
    stroke-width="4"
    fill="cyan">
</svg>
```

Algumas desvantagens de deixar o SVG diretamente na página/à mão, são:

- Não ter a possibilidade de cache que os browsers fazem;
- Se tiver que repetir o código, ele ficará muito maior e pesado;

Já algumas vantagens são:

- Redução de chamadas HTTP de fora;
- Possibilidade de estilização direto no canva (espaço de trabalho da imagem).
