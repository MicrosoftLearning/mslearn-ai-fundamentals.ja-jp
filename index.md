---
title: Azure での AI アプリとエージェントの開発を開始する
permalink: index.html
layout: home
---
これらの実践的な演習は、[Microsoft Learn](https://learn.microsoft.com/training/paths/get-started-ai-apps-agents/) のトレーニング コンテンツをサポートするように設計されています。

演習を完了するには、Microsoft Azure のサブスクリプションが必要です。 [https://azure.microsoft.com](https://azure.microsoft.com) で無料試用版にサインアップできます。

<hr>

{% assign labs = site.pages | where_exp:"page", "page.url contains '/Instructions/Exercises'" %} {% for activity in labs  %} {% if activity.lab.title %}
### [{{ activity.lab.title }}]({{ site.github.url }}{{ activity.url }})


{% if activity.lab.level %}**レベル**: {{activity.lab.level}} \| {% endif %}{% if activity.lab.duration %}**期間**: {{activity.lab.duration}}{% endif %}

{% if activity.lab.description %} *{{activity.lab.description}}* {% endif %}
<hr>
{% endif %} {% endfor %}