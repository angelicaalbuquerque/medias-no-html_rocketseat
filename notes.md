## Videos:

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

## Audio:

Muito semelhante à tag video.

```html
<audio controls loop muted autoplay>
  <source src="../assets/audio/Louie Zong - hello world.mp3" type="audio/mp3" />
  <p>Este browser não suporta áudio.</p>
</audio>
```

Através do JavaScript, entretanto, conseguimos fazer controles muito avançados com áudios. Além de que também conseguimos conseguir de outro local o áudio, como SoundCloud.

## Iframes:

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
