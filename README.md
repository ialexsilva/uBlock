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
      pronunciado como <i>you-block origin</i> (<code>/ˈjuːˌblɒk/</code>) — <i>you</i>(você) decide o que executa no seu navegador.
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

## Filosofia

uBlock Origin (ou uBlock₀) não é um *ad blocker*; é um bloqueador de uso geral. uBlock₀ bloqueia anúncios através do suporte de [Adblock Plus sintaxe de filtro](https://adblockplus.org/en/filters). uBlock₀ [estende](https://github.com/gorhill/uBlock/wiki/Filter-syntax-extensions) a sintaxe and is designed to work with custom rules and filters. Furthermore, advanced mode allows uBlock₀ to work in [default-deny mode](https://github.com/gorhill/uBlock/wiki/Dynamic-filtering:-default-deny), which mode will cause [all 3rd-party network requests](https://requestpolicycontinued.github.io/#what-are-cross-site-requests) to be blocked by default, unless allowed by the user.

That said, it's important to note that using a blocker is **NOT** [theft](https://twitter.com/LeaVerou/status/518154828166725632). Don't fall for this creepy idea. The _ultimate_ logical consequence of `blocking = theft` is the criminalisation of the inalienable right to privacy.

Ads, "unintrusive" or not, are just the visible portions of privacy-invading apparatus entering your browser when you visit most sites nowadays. **uBlock₀'s main goal is to help users neutralize such privacy-invading apparatus** — in a way that welcomes those users who don't wish to use more technical, involved means (such as [µMatrix](https://github.com/gorhill/uMatrix)).

_EasyList_, _Peter Lowe's Adservers_, _EasyPrivacy_ and _Malware domains_ are enabled by default when you install uBlock₀. Many more lists are readily available to block trackers, analytics, and more. Hosts files are also supported.

Once you install uBlock₀, you may easily un-select any of the pre-selected filter lists if you think uBlock₀ blocks too much. For reference, Adblock Plus installs with only _EasyList_ enabled by default.

By the way, looks like I still need to dispel that other myth: I've seen in [many](https://np.reddit.com/r/AskReddit/comments/35s2je/whats_a_product_that_everybody_uses_but_nobody/cr7h8l6) [places](https://twitter.com/1v1MeInBed/status/611658444244951040) [lately](https://np.reddit.com/r/explainlikeimfive/comments/363569/eli5_how_come_adblockublock_doesnt_let_the_ad/crafo5p?context=3) the following assertion:

> ublock blocks ads just like adblock plus, but triggers the ads API to think it got viewed

Completely false. uBlock Origin does not "trigger" any "ads API" (whatever that is). It [prevents network requests from being made](https://github.com/gorhill/uBlock/wiki/Does-uBlock-block-ads-or-just-hide-them%3F) according to filter lists so that your browser does not connect to remote servers, period.

## Documentação

[Quick guide: popup user interface](https://github.com/gorhill/uBlock/wiki/Quick-guide:-popup-user-interface)

<a href="https://github.com/gorhill/uBlock/wiki/Quick-guide:-popup-user-interface"><img src="https://raw.githubusercontent.com/gorhill/uBlock/master/doc/img/popup-1.png" /></a>

For advanced usage, read about [dynamic filtering](https://github.com/gorhill/uBlock/wiki/Dynamic-filtering:-quick-guide) and more on [uBlock₀'s wiki](https://github.com/gorhill/uBlock/wiki).

## Performance

#### Memória

<div align="center">
On average, uBlock₀ <b>really</b> does make your browser run leaner. <sup>[1]</sup><br><br>

Chromium <sup>[2]</sup><br>
<img src="https://raw.githubusercontent.com/gorhill/uBlock/master/doc/benchmarks/mem-usage-overall-chart-20141224.png" /><br><br>

Firefox<br>
<img src="https://raw.githubusercontent.com/gorhill/uBlock/master/doc/benchmarks/mem-usage-overall-chart-20150205.png" /><br><br>

</div>

<sup>[1] Details of the benchmark available at <a href="https://github.com/gorhill/uBlock/wiki/Firefox-version:-benchmarking-memory-footprint">Firefox version: benchmarking memory footprint</a>.</sup><br>

<sup>[2] Important note: There is currently a [bug in Chromium v39 to v41 which causes a new memory leak each time the popup UI of an extension is opened](https://code.google.com/p/chromium/issues/detail?id=441500). This affects <i>all</i> extensions. Keep this in mind when measuring Chromium's memory usage. In the benchmarks, I avoided opening the popups completely.</sup><br>

#### CPU

<p align="center">
uBlock₀ is also easy on the CPU<br>
<img src="https://raw.githubusercontent.com/gorhill/uBlock/master/doc/benchmarks/cpu-usage-overall-chart-20141226.png" /><br>
<sup>Details of the benchmark available in <a href="https://github.com/gorhill/uBlock/blob/master/doc/benchmarks/cpu-usage-overall-20141226.ods">this LibreOffice spreadsheet</a>.</sup>
</p>

#### Blocking

<p align="center">
Being lean and efficient doesn't mean blocking less<br>
<img src="https://raw.githubusercontent.com/gorhill/uBlock/master/doc/benchmarks/privex-201502-16.png" /><br>
<sup>For details of benchmark, see 
<a href="https://github.com/gorhill/uBlock/wiki/uBlock-and-others%3A-Blocking-ads%2C-trackers%2C-malwares">uBlock₀ and others: Blocking ads, trackers, malwares</a>.
</p>

#### Testes Rápidos

- [Index](http://raymondhill.net/ublock/tests.html)
- [Web page components](http://raymondhill.net/ublock/tiles1.html)
- [Popups](http://raymondhill.net/ublock/popup.html)
- [ABP Test Pages](https://testpages.adblockplus.org/)

## Instalação

Feel free to read [about the extension's required permissions](https://github.com/gorhill/uBlock/wiki/About-the-required-permissions).

#### Chromium

You can install the latest version [manually](https://github.com/gorhill/uBlock/tree/master/dist#install), from the [Chrome Store](https://chrome.google.com/webstore/detail/ublock-origin/cjpalhdlnbpafiamejdnhcphjbkeiagm), or from the [Opera store](https://addons.opera.com/en-gb/extensions/details/ublock/).

#### Firefox / Firefox for Android

[Firefox Add-ons web site](https://addons.mozilla.org/firefox/addon/ublock-origin/), or install manually by downloading the latest [uBlock0.firefox.xpi](https://github.com/gorhill/uBlock/releases) file, and by dragging the downloaded `xpi` file to your add-on page.

Of interest: [Deploying uBlock Origin for Firefox with CCK2 and Group Policy](http://decentsecurity.com/ublock-for-firefox-deployment/).

#### Safari

There is no support for Safari for uBlock Origin.

Best is that you install [chrisaljoudi/uBlock](https://github.com/chrisaljoudi/uBlock), which has official support for Safari.

#### Nota para os usuários de todos navegadores

To benefit from uBlock Origin's higher efficiency, it's advised that you don't use other inefficient blockers at the same time (such as AdBlock or Adblock Plus). uBlock₀ will do [as well or better](#blocking) than most popular ad blockers.

## Histórico de Lançamentos

See the [releases pages](https://github.com/gorhill/uBlock/releases) for a history of releases and highlights for each release.

## Sobre

[uBlock Origin's manifesto](MANIFESTO.md).

Free. Open source. For users by users. No donations sought.

Without the preset lists of filters, this extension is nothing. So if ever you
really do want to contribute something, think about the people working hard
to maintain the filter lists you are using, which were made available to use by
all for free.

You can contribute by helping translate uBlock₀ [on Crowdin](https://crowdin.net/project/ublock).

## Licença

[GPLv3](https://github.com/gorhill/uBlock/blob/master/LICENSE.txt).
