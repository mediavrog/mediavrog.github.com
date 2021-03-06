---
layout: single
title: 'Internet Explorer parsing: Listen und nicht-listen-Elemente'
published: true
comments: true
date: 2007-05-14 06:05:33
tags:
    - dom
    - parsing
    - xhtml
categories:
    - internetexplorer
permalink: /blog/2007/05/14/browser/internetexplorer/internet-explorer-parsing-1-listen-und-nicht-listen-elemente
image: 
    thumb: ie.jpg
comment_list:
  - date: 2016-06-30 00:51:00
    name: "Maik"
    message: "First!"
    url: "http://mediavrog.net"
---
> In einem kleinen Ajax-Projekt mit dyn. Nachladen von Komboboxen sorgte ein unerklärlicher Fehler dafür, dass im IE 
> (6.0 und 7) ab einem bestimmten Schritt der Wert eines hidden-Fields nicht mehr mit übergeben wurde.

Nach einigem Stöbern und Kontrolle meiner Anwendung per MS Script Debugger stellte ich fest, dass das hidden-Field ab einem bestimmten Schritt aus der DOM verschwand. Auslöser dieses Problems war fehlerhaftes XHTML-Markup. Anscheinend parst der IE ein Element, welches sich in einer Liste befindet, aber selbst von keinem Listenelement umgeben wird in das vorhergehende Listenelement.

## Ein Beispiel

```html
<ul>
    <li></li>
    <input />
</ul>
```

## Das Resultat

```html
<ul>
    <li><div><input /></div></li>
</ul>
```