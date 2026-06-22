---
title: Azure での AI アプリとエージェントの開発を開始する
permalink: index.html
layout: home
---
これらのハンズオン演習は、[Microsoft AI スキル ナビゲーター](https://aiskillsnavigator.microsoft.com/explore/search/learningpath-c1207ab7fef2e855e1cebac091002b0b82d99a80c0b10d9bc1b34cdf25be7c5f)のトレーニング コンテンツを補完するように設計されています。

演習を完了するには、Microsoft Azure のサブスクリプションが必要です。 [https://azure.microsoft.com](https://azure.microsoft.com) で無料試用版にサインアップできます。

<hr>

{% assign labs = site.pages | where_exp:"page", "page.url contains '/Instructions/Exercises'" %}
{% for activity in labs  %}
{% if activity.lab.islab == true %}
{% if activity.lab.title %}

### [{{ activity.lab.title }}]({{ site.github.url }}{{ activity.url }})

{% if activity.lab.level %}**レベル**: {{activity.lab.level}} \| {% endif %}{% if activity.lab.duration %}**期間**: {{activity.lab.duration}}{% endif %}

{% if activity.lab.description %}
*{{activity.lab.description}}*
{% endif %}
<hr>
{% endif %}
{% endif %}
{% endfor %}
