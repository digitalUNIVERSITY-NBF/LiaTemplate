<!--

author:     digitalUNIVERSITY

version:    0.0.1

language:   de

sharing:    false

link:       https://cdn.jsdelivr.net/npm/swiper@12/swiper-bundle.min.css

script:     https://cdn.jsdelivr.net/npm/swiper@12/swiper-bundle.min.js

script:     https://cdn.jsdelivr.net/npm/tabs@0.2.0/index.min.js

@style
.swiper-wrapper{
  padding: 35px;
}

.swiper-slide{
  margin-bottom: 20px;
}

[role="tablist"] {
  display: flex;
  gap: 0px; 
  padding-left: 10px; 
}

[role="tab"] {
  background: rgb(var(--color-background)) !important;
  border: 1px solid #d1d5db;
  border-bottom: none;
  border-radius: 6px 6px 0 0; 
  padding: 10px 20px;
  cursor: pointer;
  position: relative;
  top: 1px; 
}

[role="tab"]:focus {
  outline: none !important;
  box-shadow: none !important;
}

[role="tab"][aria-selected="true"] {
  font-weight: 600;
  border-top: 3px solid rgb(var(--color-highlight)); 
  z-index: 1; 
}

[role="tabpanel"] {
  border: 1px solid #d1d5db;
  padding: 20px;
  border-radius: 5px;
}

[hidden] {
  display: none !important;
}

.duQuote::before{
  content: "❝";
  color: rgb(var(--color-highlight-dark));
  float: left;
  font-size: 2.5rem;
}

.duQuote::after{
  content: "❝";
  color: rgb(var(--color-highlight-dark));
  float: right;
  font-size: 2.5rem;
}

html.lia-variant-dark .duQuote::before {
  color: rgb(from rgb(var(--color-highlight-dark))calc(r*4.8)calc(g*4.8)calc(b*4.8));
}

html.lia-variant-dark .duQuote::after {
  color: rgb(from rgb(var(--color-highlight-dark))calc(r*4.8)calc(g*4.8)calc(b*4.8));
}

/* GENERAL STYLING digitalUNIVERSITY */

blockquote {
  border-radius: 5px;
}

:root {
  --lia-blue: 39,92,144;
}

h1, h2, h3, h4, h5{
  font-family: system-ui, sans-serif !important;
}

div.lia-radio-group.lia-settings-theme-colors, 
lia-settings-editor,
li.nav__item.lia-support-menu__item.lia-support-menu__item--mode,
li.nav__item.lia-support-menu__item.lia-support-menu__item--settings > div > hr:nth-child(4),
.lia-support-menu__item.lia-support-menu__item--share
{
  display: none;
}

.lia-quote
{
  background: #A1D4ED;
  background: linear-gradient(42deg, rgba(161, 212, 237, 1) 0%, rgba(176, 215, 235, 1) 100%) !important;
}

.swiper-button-next:after, 
.swiper-button-prev:after {
  font-size: 20px !important;
  color: var(--lia-blue);
}

.swiper-button-next, 
.swiper-button-prev {
  width: 30px !important;
  height: 30px !important;
}

@end

@duSwiper
<script>
var swiper = new Swiper(".mySwiper", {
  navigation: {
    nextEl: '.swiper-button-next',
    prevEl: '.swiper-button-prev',
  },
  pagination: {
    el: '.swiper-pagination',
  },
});
</script>
@end

@duQuote: <!-- class="lia-quote__text duQuote" -->
-->

# Swiper

<div class="swiper mySwiper">
<div class="swiper-wrapper">

<div class="swiper-slide">
Slide 1
---

Ein **wichtiger** Textbaustein.

</div>

<div class="swiper-slide">
Es folgt eine Auflistung:

- Item 1
- Item 2

    1. Item 3
    2. Item 4
- Item 5
</div>

</div>
<div class="swiper-pagination"></div>
<div class="swiper-button-prev"></div>
<div class="swiper-button-next"></div>
</div>

@duSwiper

# Tabs

<div class="tabs">
<div role="tablist">
<lia-keep>
<button role="tab" aria-selected="true" aria-controls="panel-1" id="tab-1">
Tab 1
</button>
<button role="tab" aria-selected="false" aria-controls="panel-2"  id="tab-2" tabindex="-1">
Tab 2 
</button>
</lia-keep>
</div>

<div id="panel-1" role="tabpanel" aria-labelledby="tab-1">
Überschrift
---

Ein Text
</div>
<div id="panel-2" role="tabpanel" aria-labelledby="tab-2" hidden>

Eine größere Überschrift
===

Ein weiterer Text

</div>
</div>

<script>
const tabs = document.querySelectorAll('[role="tab"]');
const panels = document.querySelectorAll('[role="tabpanel"]');

tabs.forEach(tab => {
  tab.addEventListener('click', (e) => {
    // 1. Deselect all
    tabs.forEach(t => {
      t.setAttribute('aria-selected', false);
      t.setAttribute('tabindex', '-1');
    });

    // 2. Hide all panels
    panels.forEach(p => p.hidden = true);

    // 3. Select clicked tab
    e.target.setAttribute('aria-selected', true);
    e.target.setAttribute('tabindex', '0');

    // 4. Show associated panel
    const id = e.target.getAttribute('aria-controls');
    document.getElementById(id).hidden = false;
  });
});
</script> 

# Quote

@duQuote
> Eine erste Zeile.
> 
> Eine zweite Zeile.
