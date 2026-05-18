<!--

version:    0.0.1

comment:    digitalUNIVERSITY template for micromodules.

link:       ./du-style.css

link:       https://cdn.jsdelivr.net/npm/swiper@12/swiper-bundle.min.css

script:     https://cdn.jsdelivr.net/npm/swiper@12/swiper-bundle.min.js

script:     https://cdn.jsdelivr.net/npm/tabs@0.2.0/index.min.js

script:   https://cdnjs.cloudflare.com/ajax/libs/Sortable/1.15.0/Sortable.min.js

@onload
const targetTheme = document.getElementById("lia-theme-color-blue");
    if (targetTheme) {
        targetTheme.click();
    }
@end 

@duQuote: <!-- class="lia-quote__text duQuote" -->

@duSwiper
<script>
document.querySelectorAll(".mySwiper").forEach(function(swiperContainer) {
  
  if (swiperContainer.swiper) return;

  const paginationEl = swiperContainer.querySelector(".swiper-pagination");

  const swiperInstance = new Swiper(swiperContainer, {
    pagination: {
      el: paginationEl,
      clickable: true,
    },
  });

  const btnNext = swiperContainer.querySelector('.swiper-button-next');
  const btnPrev = swiperContainer.querySelector('.swiper-button-prev');

  if (btnNext) {
    btnNext.addEventListener('click', function() {
      swiperInstance.slideNext();
    });
  }

  if (btnPrev) {
    btnPrev.addEventListener('click', function() {
      swiperInstance.slidePrev();
    });
  }

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

@duSimpleSort
  @simpleSort(@uid,@0,@1)
@end

@simpleSort

<div class="simple-sort"  id="quiz-@0">
  <div class="simple-sort-choices-container" >
  </div>
</div>

  <script>
    (function(){
      if (window['@0'] == true)
        return;
      window['@0'] = true
      let quizId = '@0';
      const container = document.querySelector(`#quiz-${quizId}`);

      let choicesContainer = container.querySelector('.simple-sort-choices-container');
      
      const correctAnswers = '@2'.split('|');
      
      const initialOrder = '@1'.split('|');
      choicesContainer.innerHTML = initialOrder.map(item => 
        `<div class="simple-sort-choice lia-code lia-code--inline lia-btn  lia-btn--outline" >${item}</div>`
      ).join('');
      var sortable = new Sortable(choicesContainer, {
        animation: 150,
        filter: '.filtered',
        pull: false
      });
    })();
  </script>

<!-- data-solution-button='off' -->
  [[!]]
  <script>
    let quizId = '@0';
    let container = document.querySelector(`#quiz-${quizId}`);

    const correctAnswers = '@2'.split('|');

    let choicesContainer = container.querySelector('.simple-sort-choices-container');
    const choices = Array.from(choicesContainer.querySelectorAll('.simple-sort-choice'));
    const currentOrder = choices.map(choice => choice.textContent.trim());
    
    const isCorrect = currentOrder.length === correctAnswers.length && 
                    currentOrder.every((answer, index) => answer === correctAnswers[index]);
    
    if (isCorrect) {
      for (let choice of choices) {
        choice.classList.add("filtered")
        choice.setAttribute("disabled",true)
      }
      choicesContainer.setAttribute("disabled",true)
    } 
    isCorrect == true
  </script>
@end

-->

# Swiper

<div class="swiper mySwiper">
<div class="swiper-wrapper">

<div class="swiper-slide">
Slide 1
===

Lorem ipsum dolor sit amet, consetetur sadipscing elitr, sed diam nonumy eirmod tempor invidunt ut labore et dolore magna aliquyam erat, sed diam voluptua. At vero eos et accusam et justo duo dolores et ea rebum. Stet clita kasd gubergren, no sea takimata sanctus est Lorem ipsum dolor sit amet. Lorem ipsum dolor sit amet, consetetur sadipscing elitr, sed diam nonumy eirmod tempor invidunt ut labore et dolore magna aliquyam erat, sed diam voluptua. At vero eos et accusam et justo duo dolores et ea rebum. Stet clita kasd gubergren, no sea takimata sanctus est Lorem ipsum dolor sit amet.
</div>

<div class="swiper-slide">
Slide 2
===

Lorem ipsum dolor sit amet, consetetur sadipscing elitr, sed diam nonumy eirmod tempor invidunt ut labore et dolore magna aliquyam erat, sed diam voluptua. At vero eos et accusam et justo duo dolores et ea rebum. Stet clita kasd gubergren, no sea takimata sanctus est Lorem ipsum dolor sit amet. Lorem ipsum dolor sit amet, consetetur sadipscing elitr, sed diam nonumy eirmod tempor invidunt ut labore et dolore magna aliquyam erat, sed diam voluptua. At vero eos et accusam et justo duo dolores et ea rebum. Stet clita kasd gubergren, no sea takimata sanctus est Lorem ipsum dolor sit amet. Lorem ipsum dolor sit amet, consetetur sadipscing elitr, sed diam nonumy eirmod tempor invidunt ut labore et dolore magna aliquyam erat, sed diam voluptua. At vero eos et accusam et justo duo dolores et ea rebum. Stet clita kasd gubergren, no sea takimata sanctus est Lorem ipsum dolor sit amet.  

Duis autem vel eum iriure dolor in hendrerit in vulputate velit esse molestie consequat, vel illum dolore eu feugiat nulla facilisis at vero eros et accumsan et iusto odio dignissim qui blandit praesent luptatum zzril delenit augue duis dolore te feugait nulla facilisi. Lorem ipsum dolor sit amet, consectetuer
</div>

<div class="swiper-slide">
Slide 3
===

Lorem ipsum dolor sit amet, consetetur sadipscing elitr, sed diam nonumy eirmod tempor invidunt ut labore et dolore magna aliquyam erat, sed diam voluptua. At vero eos et accusam et justo duo dolores et ea rebum. Stet clita kasd gubergren, no sea takimata sanctus est Lorem ipsum dolor sit amet. Lorem ipsum dolor sit amet, consetetur sadipscing elitr, sed diam nonumy eirmod tempor invidunt ut labore et dolore magna aliquyam erat, sed diam voluptua. At vero eos et accusam et justo duo dolores et ea rebum. Stet clita kasd gubergren, no sea takimata sanctus est Lorem ipsum dolor sit amet.
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
@duTabs

# Quote

@duQuote
> Eine erste Zeile.
> 
> Eine zweite Zeile.

# Sorter
<!--
persistent: true
-->

Ordnen Sie die Elemente in umgekehrter Reihenfolge an:
---

@duSimpleSort(1|2|3,3|2|1)