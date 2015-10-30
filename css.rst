.. -*- coding: utf-8; -*-
.. include:: HEADER.rst

======
 CSS.
======
.. contents::

Adding CSS to HTML.
===================

Include in head tag::

  <html>
    <head>
      <link href="path-to.css" rel="stylesheet" type="text/css">
    </head>
    ...
  <html>

or::

  <head>
   <style type="text/css">
     h1 {border-width: 1; border: solid; text-align: center}
   </style>
  </head>

To change style in specific tag use::

  <b style="color: blue; font-family: ariel">Welcome!</b>

Selectors.
==========
::

  tag {}
  .class {}
  #id {} для id разрешены символы
  * {} - любой элемент

  tag tag1 {} - выбор tag1, у которых есть предок tag
  tag > tag {} - выбор дочернего элемента
  tag + tag {} - выбор соседних элементов
  tag ~ tag {} - выбор любого соседа

  [attr] {}
  [attr1][attr2] {}
  [attr="..."] {}
  [attr~="..."] {} - присутствует слово ... в поле атрибута
  [attr*="..."] {} - присутствует набор символов ... в поле атрибута
  [attr^="..."] {} - начинается с ... в поле атрибута
  [attr$="..."] {} - заканчивается на ... в поле атрибута
  tag [attr|="..."] {}

  :link - не посещенные ссылки
  :visited - посещенные ссылки
  :active - нажатие на левую клавишу мыши на элементе
  :hover - назначать при наведении
  :focus - при фокусировке элемента
  :first-child - первый подэлемент
  :last-child - последний подэлемент

  :first-line
  :first-letter - выбрать первую букву (не приминимо к inline элементам)
  :before{content:"..."}, ставит перед контентом элементов строку xxx (можно
  использовать счетчики)
  :after{} - тоже, что и before, только ставит текст после контента тега

See:

 * http://www.w3.org/TR/CSS2/selector.html
 * http://www.w3.org/TR/css3-selectors/#selectors

CSS include statement.
======================
::

  @import url("common.css");

Default style for HTML elements.
================================

 * http://www.w3.org/TR/CSS2/sample.html

Emacs.
======
::

  $ sudo apt-get install css-mode

Graphical editor.
=================
::

  $ sudo apt-get install cssed

CSS browser support.
====================

  * http://www.quirksmode.org/css/contents.html
  * http://en.wikipedia.org/wiki/Comparison_of_layout_engines_%28CSS%29
  * http://www.css3.info/modules/selector-compat/

CSS compilers.
==============

  http://lesscss.org/
                LESS extends CSS with dynamic behavior such as variables,
                mixins, operations and functions.
  http://sass-lang.com/
                Sass is the most mature, stable, and powerful professional grade
                CSS extension language in the world.

CSS frameworks.
===============

  http://getbootstrap.com/
                Sleek, intuitive, and powerful mobile first front-end framework
                for faster and easier web development.
  http://bootswatch.com/
                Free themes for Bootstrap.
  http://960.gs/
                Grid framework.
  http://purecss.io/
                A set of small, responsive CSS modules that you can use in every
                web project.
  http://foundation.zurb.com/
                The most advanced responsive front-end framework in the world.


