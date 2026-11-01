# Legend keyboard-focus reproduction

Public issue: https://github.com/carbon-design-system/carbon-charts/issues/2148

These screenshots use the actual local DonutChart and shipped SCSS, with synthetic Alpha/Beta values4and6. No external service requests or private browsing content are involved. Both fresh charts have center value10, identical slice geometry and the same focused legend checkbox. No filtering actions occur before capture. Only pixels around the focus indicator differ.

Source base: `4baa87bb1b5aba5e1a16b3a7bd8cf9c548afd894`; repaired code: `f8e8700f892df2a04eba2b44d4fabff458c828e7`.

Minimal configuration (load the corresponding version's @carbon/charts stylesheet):

```js
import {DonutChart} from '@carbon/charts';
new DonutChart(holder, {
  data: [{group:'Alpha',value:4},{group:'Beta',value:6}],
  options: {theme:'white',height:'360px',width:'600px',animations:false,
    toolbar:{enabled:false}}
});
```

Tab from a preceding button into the first legend checkbox. The original WebKit auto-outline paints a pale halo; the repaired version uses the Carbon focus token and a2px outward outline. Forced colors use CanvasText because the checkbox already opts out of automatic color adjustment.

`before.png` and `after.png` were captured with headless WebKit26.5 on macOS; they are not Safari.app or Windows screenshots. `validation.json` distinguishes rendered style fixtures, full-chart browser cases, and the coverage limits. Screenshots do not replace regression tests or establish general accessibility conformance.
