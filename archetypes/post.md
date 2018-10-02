---
title: "{{ replace .Name "-" " " | title }}"
date: {{ .Date }}
draft: true

author: "{{- if isset .Site.Params "author" -}} {{- .Site.Params.author -}} {{- end -}}"
tags: []
cover: ""
---
