---
layout: default
title: 오픈뱅킹 공통업무 API
parent: Fintech
nav_order: 1
---

# 오픈뱅킹 공통업무 API 사용하기
{: .no_toc }

오픈뱅킹 공통업무 API를 사용한 잔액조회, 거래내역조회, 계좌실명조회, 입금이체, 출금이체 개발실습
{: .fs-6 .fw-300 }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## 회원가입


금융결제원 테스트베드 사이트에 접속하여 회원가입을 합니다.

[금융결제원 테스트베드 사이트](https://developers.open-platform.or.kr){: .btn }


## 구조 설명

![](/assets/images/fintech/bankingApi/open1.png)


```yaml
# Open API를 사용함으로서 여러 은행을 한번에 접근할 수 있다.
logo: "/assets/images/just-the-docs.png"
```

## Search

```yaml
# Enable or disable the site search
# Supports true (default) or false
search_enabled: true

# Enable support for hyphenated search words:
search_tokenizer_separator: /[\s/]+/

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
