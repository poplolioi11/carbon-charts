# Gauge delta arrow update

Synthetic local data only, rendered in headless Chromium with the actual Carbon Charts GaugeChart and styles. Base main 4baa87bb1b5aba5e1a16b3a7bd8cf9c548afd894, version1.27.25.

Initial delta+5, then update to-7. The original defaultstatusnull clears the polygon selectorclass and appends each new arrow;up/down shapes overlap. The patched version keeps the selectorclass and updates the singleexistingpolygon. The value65% and delta-7% remain unchanged.

The patch was also checked in Firefox/WebKit, with status-enabled and arrow-disabled controls. These images demonstrate one localcase,not a claim of maintaineracceptance or release.
