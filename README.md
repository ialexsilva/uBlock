[<img src="https://travis-ci.org/gorhill/uBlock.svg?branch=master" height="18">](https://travis-ci.org/gorhill/uBlock)
[![Crowdin](https://d322cqt584bo4o.cloudfront.net/ublock/localized.png)](https://crowdin.com/project/ublock)

***
<h1 align="center">
<sub>
<img  src="https://raw.githubusercontent.com/gorhill/uBlock/master/doc/img/icon38@2x.png"
      height="38"
      width="38">
</sub>
uBlock Origin
</h1>
<p align="center">
<sup> <!-- Pronounciation -->
      pronunciado <i>you-block origin</i> (<code>/ˈjuːˌblɒk/</code>) — <i>you</i>(você) decide o que executa no seu navegador.
</sup>
<br>
<sup> <!-- Languages -->
      <img src="https://raw.githubusercontent.com/gorhill/uBlock/master/doc/img/languageicon-36.png" width="18" height="18">
      <sup>
            <a href="https://github.com/gorhill/uBlock/blob/master/README.md#-µblock">
            English,          <a href="https://github.com/fang5566/uBlock/blob/master/README.md#-µblock">
            Chinese (中文),   </a><a href="https://github.com/delightbot/uBlock/blob/master/README.md#ublock">
            Korean (한국어),<a/>
            Português (Brasil)
      </sup>
</sup>
</p>


**Uma bloqueador eficiente para varios navegadores. Rápido, potente e leve.**

* [Finalidade & Informação Geral](#philosophy)
* [Documentação](#documentation)
* [Performance e Eficiência](#performance)
  * [Memória](#memory)
  * [CPU](#cpu)
  * [Bloqueio](#blocking)
  * [Testes Rápidos](#quick-tests)
* [Instalação](#installation)
  * [Chromium](#chromium)
  * [Firefox](#firefox--firefox-for-android)
  * [Safari](#safari)
* [Histórico de Lançamentos](#release-history)
* [Política de Privacidade](https://github.com/gorhill/uBlock/wiki/Privacy-policy)
* [Wiki](https://github.com/gorhill/uBlock/wiki)

## Finalidade

uBlock Origin (ou uBlock₀) não é somente um *ad blocker*; é um bloqueador de uso geral. uBlock₀ bloqueia anúncios através do suporte de [Adblock Plus sintaxe de filtro](https://adblockplus.org/en/filters). uBlock₀ [estende](https://github.com/gorhill/uBlock/wiki/Filter-syntax-extensions) a sintaxe é projetada para funcionar com regras e filtros personalizados. Além disso, o modo avançado permite uBlock₀ funcionar em [modo default-deny](https://github.com/gorhill/uBlock/wiki/Dynamic-filtering:-default-deny), modo que irá fazer [todos pedidos de rede de terceiros](https://requestpolicycontinued.github.io/#what-are-cross-site-requests) serem bloqueados por padrão, a menos que seja permitido pelo usuário.

Dito isto, é importante observar que o uso de um bloqueador é de **NÃO** [roubar](https://twitter.com/LeaVerou/status/518154828166725632). Não caia nessa ideia. A consequência lógica _final_ de que `bloquear = roubar` é a criminalização do direito inalienável à privacidade.

Anúncios, "intrusivo" ou não, são apenas as partes visíveis dos mecanismos de invasão a privacidade entrando no seu navegador quando você visita a maioria dos sites hoje em dia. **uBlock₀'s o principal objetivo é ajudar os usuários a neutralizar tais mecanismos para invadir a privacidade** — in a way that welcomes those users who don't wish to use more technical, involved means (como [µMatrix](https://github.com/gorhill/uMatrix)).

_EasyList_, _Peter Lowe's Adservers_, _EasyPrivacy_ e _Malware domains_ são ativadas por padrão quando você instala o uBlock₀. Muitas outras listas estão disponíveis para bloquear rastreadores, analytics e muito mais. Arquivos hosts também são suportados.

Depois de instalar o uBlock₀, você pode facilmente desmarcar qualquer uma das listas predefinidas, se você acha que o uBlock₀ bloqueia muito. Para referência, o Adblock Plus instala somente _EasyList_ por padrão.

A propósito, parece que eu ainda preciso dissipar outro mito: Que eu vi em [muitos](https://np.reddit.com/r/AskReddit/comments/35s2je/whats_a_product_that_everybody_uses_but_nobody/cr7h8l6) [lugares](https://twitter.com/1v1MeInBed/status/611658444244951040) [ultimamente](https://np.reddit.com/r/explainlikeimfive/comments/363569/eli5_how_come_adblockublock_doesnt_let_the_ad/crafo5p?context=3) a seguinte afirmação:

> ublock bloqueia anúncios exatamente como adblock plus, mas aciona a API anúncios para simular que tenha visto

Completamente falso. uBlock Origin não "aciona" nenhuma "API de anúncios" (seja lá o que for). Ele [impede que pedidos de rede sejam feitas](https://github.com/gorhill/uBlock/wiki/Does-uBlock-block-ads-or-just-hide-them%3F) de acordo com as listas de filtros, para que seu navegador não se conectar a servidores remotos, período.

## Documentação

[Guia rápido: interface de usuário](https://github.com/gorhill/uBlock/wiki/Quick-guide:-popup-user-interface)

<a href="https://github.com/gorhill/uBlock/wiki/Quick-guide:-popup-user-interface"><img src="https://raw.githubusercontent.com/gorhill/uBlock/master/doc/img/popup-1.png"/></a>

Para uso avançado, leia sobre [filtragem dinâmica](https://github.com/gorhill/uBlock/wiki/Dynamic-filtering:-quick-guide) e muito mais na [uBlock₀'s wiki](https://github.com/gorhill/uBlock/wiki).

## Performance

#### Memória

<div align="center">
Em média, o uBlock₀ <b>realmente</b> faz com que seu navegador fique mais leve <sup>[1]</sup><br><br>

Chromium <sup>[2]</sup><br>
<img src="https://raw.githubusercontent.com/gorhill/uBlock/master/doc/benchmarks/mem-usage-overall-chart-20141224.png" /><br><br>

Firefox<br>
<img src="https://raw.githubusercontent.com/gorhill/uBlock/master/doc/benchmarks/mem-usage-overall-chart-20150205.png" /><br><br>

</div>

<sup>[1] Detalhes do benchmark disponível na <a href="https://github.com/gorhill/uBlock/wiki/Firefox-version:-benchmarking-memory-footprint">versão do Firefox: benchmarking consumo de memória</a>.</sup><br>

<sup>[2] Nota importante: Existe atualmente um [bug no Chromium v39 até v41 que causa um vazamento de memória toda vez que a janela popup da extensão é aberta](https://code.google.com/p/chromium/issues/detail?id=441500). Isso afeta <i>todas</i> extensões. Tenha isso em mente quando medir o consumo de memória do Chromium. Nos benchmarks, Eu evitei a abertura dos popups</sup><br>

#### CPU

<p align="center">
uBlock₀ também usa poucos recursos de CPU<br>
<img src="https://raw.githubusercontent.com/gorhill/uBlock/master/doc/benchmarks/cpu-usage-overall-chart-20141226.png" /><br>
<sup>Detalhes do benchmark disponível <a href="https://github.com/gorhill/uBlock/blob/master/doc/benchmarks/cpu-usage-overall-20141226.ods">nesta planilha do LibreOffice</a>.</sup>
</p>

#### Bloqueio

<p align="center">
Ser leve e eficiente não significa bloquear menos<br>
<img src="https://raw.githubusercontent.com/gorhill/uBlock/master/doc/benchmarks/privex-201502-16.png" /><br>
<sup>Para detalhes do benchmark, veja 
<a href="https://github.com/gorhill/uBlock/wiki/uBlock-and-others%3A-Blocking-ads%2C-trackers%2C-malwares">uBlock₀ e outros: Bloqueadores de anúncios, rastreadores, malwares</a>.
</p>

#### Testes Rápidos

- [Index](http://raymondhill.net/ublock/tests.html)
- [Web page components](http://raymondhill.net/ublock/tiles1.html)
- [Popups](http://raymondhill.net/ublock/popup.html)
- [ABP Test Pages](https://testpages.adblockplus.org/)

## Instalação

Sinta-se livre para ler [sobre as permissões necessárias da extensão](https://github.com/gorhill/uBlock/wiki/About-the-required-permissions).

#### Chromium

Você pode instalar a ultima versão [manualmente](https://github.com/gorhill/uBlock/tree/master/dist#install), da [Chrome Store](https://chrome.google.com/webstore/detail/ublock-origin/cjpalhdlnbpafiamejdnhcphjbkeiagm), ou da [Opera store](https://addons.opera.com/en-gb/extensions/details/ublock/).

#### Firefox / Firefox para Android

[Firefox Add-ons web site](https://addons.mozilla.org/firefox/addon/ublock-origin/), ou instalar manualmente baixando a última versão do arquivo [uBlock0.firefox.xpi](https://github.com/gorhill/uBlock/releases) e arrastando e soltando o arquivo `xpi` baixado na página de add-on.

Do interesse: [Implantando o uBlock Origin para o Firefox com CCK2 e diretiva de grupo.](http://decentsecurity.com/ublock-for-firefox-deployment/).

#### Safari

Não há suporte do uBlock Origin para o Safari.

Mais você pode instalar [chrisaljoudi/uBlock](https://github.com/chrisaljoudi/uBlock), que tem suporte oficial para o Safari.

#### Nota para os usuários de todos navegadores

Para beneficiar da eficiência mais elevada do uBlock Origin's, é aconselhavel que você não use outros bloqueadores ao mesmo tempo (como o AdBlock ou Adblock Plus). uBlock₀ vai funcionar [tão bem ou melhor](#blocking) do que a maioria dos bloqueadores de anúncios populares.

## Histórico de Lançamentos

Veja a [página de lançamentos](https://github.com/gorhill/uBlock/releases) para ver o histórico de lançamentos e destaques de cada lançamento.

## Sobre

[Manifesto do uBlock Origin's](MANIFESTO.md).

Gratuito. Código Aberto. De usuários para usuários. Não aceitamos doações.

Sem as listas predefinidas de filtros, esta extensão não é nada. 
Por isso, se você nunca contribuiu com alguma coisa, pense nas pessoas que trabalham duro
para manter as listas de filtro que você está usando, que foram disponibilizadas para usar
tudo de graça.

Você pode contribuir ajudando a traduzir uBlock₀ [no Crowdin](https://crowdin.net/project/ublock).

## Licença

[GPLv3](https://github.com/gorhill/uBlock/blob/master/LICENSE.txt).
