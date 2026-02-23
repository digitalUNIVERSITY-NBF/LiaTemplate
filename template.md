<!--

version:    0.0.1

comment:    digitalUNIVERSITY template for micromodules.

link:       https://cdn.jsdelivr.net/gh/digitalUNIVERSITY-NBF/LiaTemplate@6c172624a1db9d2442f9b98e989f28fbac55ed43/du-style.css

link:       https://cdn.jsdelivr.net/npm/swiper@12/swiper-bundle.min.css

script:     https://cdn.jsdelivr.net/npm/swiper@12/swiper-bundle.min.js

script:     https://cdn.jsdelivr.net/npm/tabs@0.2.0/index.min.js

@onload
const targetTheme = document.getElementById("lia-theme-color-blue");
    if (targetTheme) {
        targetTheme.click();
    }
@end 

@duQuote: <!-- class="lia-quote__text duQuote" -->

@duSwiper
<script>
var swiper = new Swiper(".mySwiper", {
  pagination: {
    el: ".swiper-pagination",
    clickable: true,
  },
});

const btnNext = document.querySelector('.swiper-button-next');
const btnPrev = document.querySelector('.swiper-button-prev');

btnNext.addEventListener('click', function() {
  swiper.slideNext();
});

btnPrev.addEventListener('click', function() {
  swiper.slidePrev();
});

</script>
@end

@duTabs
<script>
if (!window.duTabsInitialized) {
  window.duTabsInitialized = true;

  document.addEventListener('click', (e) => {
    const clickedTab = e.target.closest('[role="tab"]');
    if (!clickedTab) return;

    const tabContainer = clickedTab.closest('.tabs');
    if (!tabContainer) return;

    const tabs = tabContainer.querySelectorAll('[role="tab"]');
    const panels = tabContainer.querySelectorAll('[role="tabpanel"]');

    tabs.forEach(t => {
      t.setAttribute('aria-selected', 'false');
      t.setAttribute('tabindex', '-1');
    });

    panels.forEach(p => p.hidden = true);

    clickedTab.setAttribute('aria-selected', 'true');
    clickedTab.setAttribute('tabindex', '0');

    const id = clickedTab.getAttribute('aria-controls');
    const panelToShow = document.getElementById(id);
    if (panelToShow) {
        panelToShow.hidden = false;
    }
  });
}
</script>
@end

-->

# Swiper

<div class="swiper mySwiper">
<div class="swiper-wrapper">

<div class="swiper-slide">
Effektivität
===

Effektivität beschreibt die Genauigkeit und Vollständigkeit, mit der ein Benutzer seine Ziele erreicht. Im Kontext von Usability bedeutet dies, dass ein Produkt genau das tut, was es soll, und die Bedürfnisse des Nutzers erfüllt. Effektivität ist meist eine binäre Frage: Kann der Nutzer die Aufgabe erledigen oder nicht? Ein Beispiel wäre ein Fahrkartenautomat, der dem Benutzer die Möglichkeit bietet, schnell und korrekt ein Ticket zu kaufen. Die Effektivität wäre hier hoch, wenn der Benutzer ohne Probleme sein Ziel erreicht.
</div>

<div class="swiper-slide">
Effizienz
===

Effizienz bezieht sich auf die Ressourcen, die der Benutzer aufwenden muss, um seine Ziele zu erreichen. Diese Ressourcen können Zeit, mentale oder physische Anstrengung, Aufmerksamkeit oder auch Kosten sein. Ein Produkt ist effizient, wenn der Benutzer mit minimalem Aufwand sein Ziel erreichen kann. Zurück zum Beispiel des Fahrkartenautomaten: Wenn das Ticket in wenigen Schritten und ohne große Mühe gekauft werden kann, ist die Effizienz hoch. Ist der Prozess hingegen umständlich oder verwirrend, ist die Effizienz gering, selbst wenn das Ziel erreicht wird.
</div>

<div class="swiper-slide">
Zufriedenheit
===

Zufriedenheit beschreibt, wie komfortabel und angenehm der Benutzer das Produkt oder die Anwendung empfindet. Sie ist subjektiver als Effektivität und Effizienz, bezieht sich aber auf das emotionale Empfinden des Benutzers während der Nutzung. Ein benutzerfreundliches Produkt sorgt dafür, dass der Benutzer gerne damit arbeitet, ohne Frustration oder Stress. Zufriedenheit kann durch verschiedene Faktoren beeinflusst werden, wie z.B. die Ästhetik der Benutzeroberfläche, die Einfachheit der Nutzung oder den allgemeinen Komfort bei der Interaktion.
</div>

</div>

<lia-keep>
<div class="swiper-controls">
  <button class="swiper-button-prev lia-btn lia-btn__icon icon icon-arrow-left lia-btn--transparent"></button>
  <div class="swiper-pagination"></div>
  <button class="swiper-button-next lia-btn lia-btn__icon icon icon-arrow-right lia-btn--transparent"></button>
</div>
</lia-keep>

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
