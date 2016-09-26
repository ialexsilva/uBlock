[![Build](https://travis-ci.org/gorhill/uBlock.svg?branch=master)](https://travis-ci.org/gorhill/uBlock)
[![Crowdin](https://d322cqt584bo4o.cloudfront.net/ublock/localized.png)](https://crowdin.com/project/ublock)
[![License](https://img.shields.io/badge/License-GPLv3-blue.svg)](https://github.com/gorhill/uBlock/blob/master/LICENSE.txt)

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
            <a href="https://github.com/gorhill/uBlock/blob/master/README.md#ublock-origin">
            English,          <a href="https://github.com/fang5566/uBlock/blob/master/README.md#ublock-origin">
            Chinese (中文),   </a><a href="https://github.com/delightbot/uBlock/blob/master/README.md#ublock-origin">
            Korean (한국어),<a/>
            Português (Brasil)
      </sup>
</sup>
</p>


**Um bloqueador eficiente para varios navegadores. Rápido e leve.**

* [Documentação](#documentação)
* [Finalidade & Informações Gerais](#finalidade)
* [Desempenho e Eficiência](#desempenho)
  * [Memória](#memória)
  * [CPU](#cpu)
  * [Bloqueio](#bloqueio)
  * [Testes Rápidos](#testes-rápidos)
* [Instalação](#instalação)
  * [Chromium](#chromium)
  * [Firefox](#firefox--firefox-para-android)
  * [Microsoft Edge](#microsoft-edge)
* [Histórico de Lançamentos](#histórico-de-lançamentos)
* [Política de Privacidade](https://github.com/gorhill/uBlock/wiki/Privacy-policy)
* [Wiki](https://github.com/gorhill/uBlock/wiki)

## Documentação

 Modo básico | Modo usuário avançado
:----------:|:------------------:
[Interface de usuário](https://github.com/gorhill/uBlock/wiki/Quick-guide:-popup-user-interface) | [Um firewall de apontar e clicar que pode ser configurado em uma base site por site](https://github.com/gorhill/uBlock/wiki/Dynamic-filtering:-quick-guide) 
<a href="https://github.com/gorhill/uBlock/wiki/Quick-guide:-popup-user-interface"><img src="https://raw.githubusercontent.com/gorhill/uBlock/master/doc/img/popup-1.png" /></a><br><sup>.<br>.</sup> | <a href="https://github.com/gorhill/uBlock/wiki/Dynamic-filtering:-quick-guide"><img src="https://cloud.githubusercontent.com/assets/585534/9293685/378d18f0-4402-11e5-9255-8ed3fdbfa957.png" /></a><br><sup>Configure como quiser:<br>a imagem mostra scripts de terceiros e frames bloqueados por padrão em toda parte</sup>

## Finalidade

uBlock Origin (ou uBlock₀) não é somente um *bloqueador de anúncios*; é um bloqueador de uso geral. O uBlock₀ bloqueia anúncios através do suporte da [sintaxe de filtro do Adblock Plus](https://adblockplus.org/en/filters). uBlock₀ [estende](https://github.com/gorhill/uBlock/wiki/Filter-syntax-extensions) a sintaxe que é projetada para funcionar com regras e filtros personalizados. Além disso, o modo avançado permite uBlock₀ funcione em [modo bloquear-padrão](https://github.com/gorhill/uBlock/wiki/Dynamic-filtering:-default-deny), modo que irá fazer [todos pedidos de rede de terceiros](https://requestpolicycontinued.github.io/#what-are-cross-site-requests) serem bloqueados por padrão, a menos que seja permitido pelo usuário.

Dito isto, é importante notar que o uso de um bloqueador **NÃO** é [roubar](https://twitter.com/LeaVerou/status/518154828166725632). Não caia nessa ideia. A consequência lógica _final_ de que `bloquear = roubar` é a criminalização do direito inalienável a privacidade.

Anúncios, "invasivos" ou não, são apenas as partes visíveis dos mecanismos de invasão a privacidade entrando no seu navegador quando você visita a maioria dos sites hoje em dia. **O principal objetivo do uBlock₀'s é ajudar os usuários a neutralizar tais mecanismos de invasão a privacidade** — de uma forma que acolhe aqueles usuários que não queiram o uso mais avançado envolvido (como [µMatrix](https://github.com/gorhill/uMatrix)).

_EasyList_, _Peter Lowe's Adservers_, _EasyPrivacy_ e _Malware domains_ são ativadas por padrão quando você instala o uBlock₀. Muitas outras listas estão disponíveis para bloquear rastreadores, analytics e muito mais. Arquivos hosts também são suportados.

Depois de instalar o uBlock₀, você pode facilmente desmarcar qualquer uma das listas pre-selecionada, se você pensa que o uBlock₀ bloqueando muito. Para referência, o Adblock Plus instala somente a lista _EasyList_ por padrão.

## Desempenho

#### Memória

<div align="center">
Em média, uBlock Origin faz com que seu navegador fique mais leve <sup>[1]</sup><br><br>

Chromium<br>
<img src="https://cloud.githubusercontent.com/assets/585534/10074141/15f04128-629c-11e5-9155-177fd4909083.png" /><br><br>

Firefox<br>
<img src="https://cloud.githubusercontent.com/assets/585534/10074130/0577118c-629c-11e5-9902-bf367c6a96c3.png" /><br><br>

</div>

<sup>[1] Detalhes do benchmark disponível na <a href="https://github.com/gorhill/uBlock/wiki/Firefox-version:-benchmarking-memory-footprint">versão do Firefox: benchmarking consumo de memória</a>.</sup><br>

#### CPU

<p align="center">
uBlock₀ também usa poucos recursos de CPU<br>
<img src="https://raw.githubusercontent.com/gorhill/uBlock/master/doc/benchmarks/cpu-usage-overall-chart-20141226.png" /><br>
<sup>Detalhes do benchmark disponível <a href="https://github.com/gorhill/uBlock/blob/master/doc/benchmarks/cpu-usage-overall-20141226.ods">nesta planilha do LibreOffice</a>.</sup>
</p>

#### Bloqueio

<p align="center">
Ser leve e eficiente não significa que está bloqueando menos<br>
<img src="https://raw.githubusercontent.com/gorhill/uBlock/master/doc/benchmarks/privex-201502-16.png" /><br>
<sup>Para detalhes do benchmark, veja 
<a href="https://github.com/gorhill/uBlock/wiki/uBlock-and-others%3A-Blocking-ads%2C-trackers%2C-malwares">uBlock₀ e outros: Bloqueadores de anúncios, rastreadores, malwares</a>.
</p>

#### Testes Rápidos

- [Index](http://raymondhill.net/ublock/tests.html)
- [Componentes da página web](http://raymondhill.net/ublock/tiles1.html)
- [Popups](http://raymondhill.net/ublock/popup.html)
- [Páginas de teste ABP](https://testpages.adblockplus.org/)

## Instalação

Sinta-se livre para ler [sobre as permissões necessárias da extensão](https://github.com/gorhill/uBlock/wiki/About-the-required-permissions).

#### Chromium

Você pode instalar a ultima versão [manualmente](https://github.com/gorhill/uBlock/tree/master/dist#install), da [Chrome Store](https://chrome.google.com/webstore/detail/ublock-origin/cjpalhdlnbpafiamejdnhcphjbkeiagm), ou da [Opera store](https://addons.opera.com/en-gb/extensions/details/ublock/).

Espera-se que uBlock Origin seja compatível com todos os navegadores baseados no Chromium.

**Importante:** Navegadores baseados no Chromium não retransmite [conexões websocket](https://en.wikipedia.org/wiki/WebSocket) Isso pode ser corrigido através da instalação da extensão companheira do uBO. [uBO-WebSocket](https://github.com/gorhill/uBO-WebSocket).

#### Firefox / Firefox para Android

[Site de Complementos do Firefox](https://addons.mozilla.org/addon/ublock-origin/). Há também uma versão de desenvolvimento, se você quiser testar uBlock Origin com as últimas alterações: visite a página de [_Histórico de versões do uBlock Origin_](https://addons.mozilla.org/addon/ublock-origin/versions/beta)

uBlock Origin é compatível com [SeaMonkey](http://www.seamonkey-project.org/), [Pale Moon](https://www.palemoon.org/), e possivelmente outros navegadores baseados no Firefox.

A versão do uBlock Origin para o Firefox tem [uma funcionalidade extra](https://github.com/gorhill/uBlock/wiki/Inline-script-tag-filtering) atualmente ainda não está disponível para os navegadores baseados no Chromium -- que apresenta uma grande ajuda para frustrar as tentativas de muitos sites de contornar os bloqueadores.

Também de interesse: [Implantando o uBlock Origin para o Firefox com CCK2 e diretiva de grupo.](http://decentsecurity.com/ublock-for-firefox-deployment/).

##### Debian/Ubuntu

Agradecimentos ao colaborador do Debian [Sean Whitton](https://wiki.debian.org/SeanWhitton), os usuários do Debian 9 ou posterior ou Ubuntu 16.04 ou posterior pode simplesmente instalar usando
`apt-get install xul-ext-ublock-origin`.

#### Microsoft Edge

Versão em desenvolvimento por [@nikrolls](https://github.com/nikrolls): <https://github.com/nikrolls/uBlock-Edge#edge>.

#### Nota para usuários de todos navegadores

Para beneficiar da eficiência mais elevada do uBlock Origin's, é aconselhavel que você não use outros bloqueadores ao mesmo tempo (como o AdBlock ou Adblock Plus). uBlock₀ vai funcionar [tão bem ou melhor](#blocking) do que a maioria dos bloqueadores de anúncios populares.

## Histórico de Lançamentos

Visite a [página de lançamentos](https://github.com/gorhill/uBlock/releases) para ver o histórico de lançamentos e os destaques de cada lançamento.

## Sobre

[Manifesto do uBlock Origin's](MANIFESTO.md).

Gratuito e de código aberto. Feito de usuários para usuários. Não aceitamos doações.

Sem as listas predefinidas de filtros, esta extensão não é nada. 
Por isso, se você nunca contribuiu com alguma coisa, pense nas pessoas que trabalham duro
para manter as listas de filtro que você está usando, que foram disponibilizadas para usar
tudo de graça.

Você pode contribuir ajudando a traduzir uBlock₀ [no Crowdin](https://crowdin.net/project/ublock).

## Licença

[GPLv3](https://github.com/gorhill/uBlock/blob/master/LICENSE.txt).
