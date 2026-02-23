<!--

version:  0.0.1

comment:    digitalUNIVERSITY template for courses.

link:       https://cdn.jsdelivr.net/npm/swiper@12/swiper-bundle.min.css

script:     https://cdn.jsdelivr.net/npm/swiper@12/swiper-bundle.min.js

script:     https://cdn.jsdelivr.net/npm/tabs@0.2.0/index.min.js

@onload
const targetTheme = document.getElementById("lia-theme-color-blue");
    if (targetTheme) {
        targetTheme.click();
    }
@end 

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

# Template
