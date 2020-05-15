---
layout: default
title: 오픈뱅킹 공통업무 API
parent: Fintech
nav_order: 1
---

# 오픈뱅킹 공통업무 API 사용하기
{: .no_toc }

개발실습
{: .fs-6 .fw-300 }
잔액조회
{: .label .label-green }
거래내역조회
{: .label .label-green } 
계좌실명조회
{: .label .label-green }
입금이체
{: .label .label-green }
출금이체
{: .label .label-green }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## 정의 및 구조 설명

![](/assets/images/fintech/bankingApi/banking1.png)
```yaml
오픈뱅킹을 사용함으로서 여러 은행을 한번에 접근하여 오픈 API의 금융 서비스를 테스트 해보거나 상용화 할 수 있다.
```

<dl>
    <dt>오픈뱅킹 </dt>
    <dd>
    핀테크기업이 금융서비스를 편리하게 개발할 수 있도록 은행의 금융서비스를 표준화된 형태로 제공하는 인프라를 말하며, 오픈 API와 테스트베드로 구성
    </dd>
    <dt>오픈 API </dt>
    <dd>핀테크기업이 직접 응용프로그램과 서비스를 개발할 수 있도록 공개된 프로그램 도구로서, 7개의 서비스 API와 인증/관리 API 제공</dd>
    <dt>테스트베드</dt>
    <dd>개발된 서비스가 금융전산망에서 정상적으로 작동하는지 시험해 볼 수 있는 인프라</dd>
</dl>



## 회원가입 및 설정

먼저 금융결제원 테스트베드 사이트에 접속하여 회원가입을 합니다.

[금융결제원 테스트베드 사이트](https://developers.open-platform.or.kr){: .btn }


![](/assets/images/fintech/bankingApi/banking2.png)


![](/assets/images/fintech/bankingApi/banking3.png)


![](/assets/images/fintech/bankingApi/banking4.png)
```yaml

```

![](/assets/images/fintech/bankingApi/banking5.png)

오픈API 명세서를 다운로드 합니다.

[오픈뱅킹공동업무 오픈API 명세서](https://developers.openbanking.or.kr/guide/sdkdownload/2016077){: .btn }


## 오픈 API OAuth 인증

![](/assets/images/fintech/bankingApi/banking6.png)

```yaml
사용자 인증(3-legged)
클라이언트는 오픈플랫폼에 접속하여 API를 사용하기 윟여, 가장 먼저 사용자 인증(로그인)을 수행하여야 합니다.
사용자 인증은 클라이언트가 사용자의 오픈플랫폼 회원정보를 얻기 위한 절차이며, 사용자는 오픈플랫폼에 회원가입이 되어있어야 합니다.
(사용자는 최초 사용자 인증 시에, 팝업된 오픈플랫폼 로그인 페이지에서 즉시 회원가입을 수행할 수도 있습니다.) 동 절차는 OAuth 2.0의
Authorization Code Grant 절차를 준용하여 개발되었으며, 클라이언트는 사용자의 동의를 먼저 획득한 후에 이어서 오픈플랫폼 서버로부터
접근 토큰(Acess Token)을 획득하여, 토큰의 유효기간 내에서 언제든지 사용자 회원정보에 접근할 수 있습니다.
```

## Aux links

```yaml
# Aux links for the upper right navigation
aux_links:
  "Just the Docs on GitHub":
    - "//github.com/pmarsceill/just-the-docs"
```

## Heading anchor links

```yaml
# Heading anchor links appear on hover over h1-h6 tags in page content
# allowing users to deep link to a particular heading on a page.
#
# Supports true (default) or false/nil
heading_anchors: true
```

## Footer content

```yaml
# Footer content appears at the bottom of every page's main content
footer_content: "Copyright &copy; 2017-2019 Patrick Marsceill. Distributed by an <a href=\"https://github.com/pmarsceill/just-the-docs/tree/master/LICENSE.txt\">MIT license.</a>"
```

## Color scheme

```yaml
# Color scheme currently only supports "dark" or nil (default)
color_scheme: "dark"
```
<button class="btn js-toggle-dark-mode">Preview dark color scheme</button>


<script type="text/javascript" src="{{ absolute_url }}"></script>

See [Customization]({{ site.baseurl }}{% link docs/customization.md %}) for more information.

## Google Analytics

```yaml
# Google Analytics Tracking (optional)
# e.g, UA-1234567-89
ga_tracking: UA-5555555-55
```
