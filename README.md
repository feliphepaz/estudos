# Estudos
Em minha jornada como desenvolvedor, passei por algumas dificuldades no meu aprendizado referente a alguns conceitos de programação. Para me ajudar, eu comecei a escrever com as minhas próprias palavras o que eu tinha até então entendido de tais assuntos. Esse tipo de técnica me ajudou bastante a fixar alguns métodos do JavaScript, sendo que agora eu já utilizo a maior parte deles no meu dia a dia.

Deixo aqui então como uma simples forma de compartilhar conhecimento 🤓
<br>
<br>

## Promises

Para se criar uma nova promise, precisa chamar o objeto construtor dele. No caso, seria o _New Promise_.

Dentro dessa _New Promise_, é passada uma função com dois parâmetros, que seriam eles o _Resolve_ e o _Reject_.

Caso a condição seja true, usa-se o _Resolve_ para retornar uma função.  Caso seja false, retorna o que tiver dentro de _Reject_.

O que é passado na função desses dois parâmetros já é retornado instantaneamente.  O método _Then_ é utilizado então para respeitar o tempo em que essa promise é resolvida. Por exemplo, se tiver um _setTimeout_  de 2000 dentro de _Resolve_, o _Then_ vai esperar dar 2 segundos para ativar a função.

O que é retornado de _Then_ também é uma promise, ou seja, para trabalhar o que está dentro desse escopo, é necessário usar o return e encadear um novo _Then_. Caso na função não tenha um return, o valor será retornado como undefined.

Junto ao _Then_, também temos outros métodos que é o _Catch_ e o _Finally_. No caso do _Catch_, ele só é ativado quando a promise é rejeitada, mas para economizar código, o _Reject_ também pode ser passado como segundo parâmetro do _Then_.

Já o _Finally_, ele é ativado independente do resultado da promise. Se for resolvida ou rejeitada não importa. Mas deve ser passada como uma função anônima, sem parâmetros.

Dois métodos referentes à promise em si, são o _Promise.all_ e o _Promise.race_. No _all_ é passado uma array com outras promises, e se todas forem resolvidas ou uma delas for rejeitada, a função ocorre. Já no _race_ a primeira que for resolvida ou rejeitada é retornada.
<br>
<br>

## Fetch

O _Fetch_ é um método utilizado para fazer requisições HTTP. Logo, ele só funciona no servidor.

Para  se trabalhar com o conteúdo do _Fetch_, realizamos um _Then_, já que o que é retornado é sempre uma promise. Nesta promise, com o parâmetro _Response_, nos é dado um objeto.

Neste objeto se tem diversos métodos em seu protótipo. Dois desses e os que são mais utilizados são o _Json_ e o _Text_. O _Json_ geralmente é utilizado para captar itens de um objeto e o _Text_ para retornar textos puros.

Ao utilizar um desses métodos, o resultado é novamente uma promise, e dentro de seu value é o que geralmente esperamos acessar. Para fazer tal acesso, o _Then_ é novamente utilizado, nos dando finalmente o conteúdo em si do _Fetch_.

Além do _Json_ e do _Text_, também temos os métodos _Blob_ e _Clone_. O _Blob_ em si não é de muita utilidade, mas usando a propriedade _createObjectURL_ do JavaScript, somos capazes de transformar uma imagem em um link. 

Quando transformamos um _Response_ em um _Text_ ou em um _Json_, não podemos transformar o body novamente, a não ser que clonamos esse body com o método _Clone_, utilizando ele então com esse objetivo.
<br>
<br>

## Async / Await

O Async / Await é uma implementação nova do JavaScript e é conhecida por ser uma _Syntactical Sugar_, ou seja, veio apenas para facilitar a escrita ao trabalhar com promises.

Ao invés de tanto _Then_, a gente pode substituir isso por uma função do qual ela será _Async_. Dentro dessa função geralmente terá duas constantes: a primeira será a do _Fetch_ (_response_), e a segunda no que a gente gostaria de transformar aquela requisição (_resolve_).

A diferença principal aqui é que agora passamos _Await_ nessas duas constantes, para que assim o JavaScript troque o resultado delas pelas promises já resolvidas, acelerando assim o processo e deixando o código mais clean.

Como em uma promise normal a gente tinha os métodos _Then_, _Catch_ e _Finally_, aqui a gente também tem, porém substituímos o _Then_ por _Try_, onde nesse escopo será passada toda a função que gostaríamos que fosse realizada. Se essa função falhar, ele pula pro _Catch_.

Um macete para sempre resolver duas ou mais requisições ao mesmo tempo, é não inserir o _Await_ antes do _Fetch_, e sim,  inserir numa constante criada exclusivamente para aguardar a resposta da promise, pois assim, ele só irá continuar quando o _Fetch_ for finalmente requisitado. 

Vale ressaltar também que o _Await_ deve ser passado apenas antes de uma promise. Caso não seja, o _Await_ será simplesmente ignorado.
<br>
<br>

## HTTP e CORS

O _Fetch_ nos da a possibilidade de mudar o método de requisição que é feita, para isso, devemos passar essas opções como um segundo parâmetro da função.

Dentro dessas opções, temos 4 tipos de métodos: o GET, que é o método padrão e que simplesmente puxa as informações da URL, o POST, que realiza uma nova entrada no json; O PUT que atualiza uma entrada e o DELETE que apaga a entrada selecionada.

Para usar o POST e o PUT é sempre importante também definirmos o body e as headers do que será postado ou atualizado.

Além destas, também temos o HEAD, do qual puxa as headers da requisição, porém, para isso precisamos fazer um _forEach_ pelo _Response_, já que só é possível acessar as headers por um método de iteração.

Dependendo da requisição que realizamos, poderemos nos deparar com um problema de CORS. Este no caso é um acordo de segurança servidor/browser. Ele impede que você injete certos tipos de scripts no seu site, evitando assim possíveis brechas no servidor.

Porém, esta política pode ser violada utilizando proxies ou através de plugins que fazem a liberação do Access-Control-Allow-Origin.
<br>
<br>

## Distâncias no Window

O _innerHeight_ como o nome já diz, é a propriedade que te da a altura da janela naquele momento. Se você diminuir ela, o número também diminui. Geralmente em animações ao scroll, ela é multiplicada por uma porcentagem. Por exemplo: _window.innerHeight_ * 0,6 = resultará em um número que representa 60% da altura da janela. Se quiser achar os outros 40%, basta subtrair.

Além do _innerHeight_, também temos o _outerHeight_, do qual ele não só pega a altura da página, como também leva em conta a barra de endereços. O _innerWidth_ e _outerWidth_ funcionam da mesma forma, mas no caso deste último, ele também considera a dev tools.

O _pageYOffset_ nos da a altura do scroll até o topo. Sendo 0 o topo, e o fundo da página o valor máximo. O _pageXOffset_ também faz isso, mas agora fazendo a mesma função para o eixo X, ou seja, utilizando a vertical como referência. 

O _offsetTop_ ao contrário dos outros métodos daqui, é ligada ao elemento do qual você quer manipular e te da a distância dele pro topo da página. O _offsetLeft_ consiste no mesmo, porém agora nos dando a distância entre o elemento e o canto esquerdo.




