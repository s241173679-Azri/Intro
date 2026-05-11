---
title-slide: false
bibliography: references.bib
csl: vancouver.csl
citeproc: true
theme: serif
background-color: "#ffffff"
transition: slide
navigationMode: linear
hash: true
---

:::: {.columns}
::: {.column width="50%"}

## Sample slides
#### PlaceHolderName
#### Universiti Malaysia Perlis
#### [placeholder@email.com](mailto:placeholder@email.com)

<audio id="bg-music" src="media/audio/sb.m4a" loop></audio>

<div id="audio-credit"
     style="position: absolute; bottom: 40px; right: 20px; font-size: 0.6em; opacity: 0.6;">
  Music: “Adrift” by Scott Buckley (CC BY 4.0)
</div>

<script>
  document.addEventListener('DOMContentLoaded', () => {
    const audio = document.getElementById('bg-music');
    const credit = document.getElementById('audio-credit');

    // hide credit by default
    credit.style.display = 'none';

    const test = new Audio('media/audio/bgm.mp3');

    test.addEventListener('canplaythrough', () => {
      // bgm.mp3 exists → use it, keep credit hidden
      audio.src = 'media/audio/bgm.mp3';
    }, { once: true });

    test.addEventListener('error', () => {
      // bgm.mp3 missing → sb.m4a will play → show credit
      credit.style.display = 'block';
    }, { once: true });

    document.addEventListener('click', () => {
      if (Reveal.getIndices().h === 0) {
        audio.volume = 0.5;
        audio.play();
      }
    }, { once: true });

    Reveal.on('slidechanged', (event) => {
      if (event.indexh > 0) { audio.pause(); }
      else { audio.play(); }
    });
  });
</script>

:::

::: {.column width="50%"}
![](media/pics/logo1.png)
:::

::::

---

:::: {.columns}
::: {.column width="50%"}
### Slide one
**Key Concepts:**
- Energy conservation per @carnot1824.
- $\Delta U = Q - W$
:::

::: {.column width="50%"}
![](media/pics/sample.png)
:::
::::

---

<span class="slide-title" data-title="My Hidden Slide Name"></span>

![](media/pics/wide.jpeg)

---

:::: {.columns}
::: {.column width="50%"}
### The Master Equation
The fundamental relation of thermodynamics:

$$\Delta U = Q - W$$

The work done $W$ is positive when the system expands against an external pressure.
:::

::: {.column width="50%"}
<video data-src="media/videos/sample.mp4" data-autoplay loop muted width="100%"></video>
:::

::::

---

:::: {.columns}
::: {.column width="50%"}
### Visualizing the Gas Law
**Interactive Model:**

- P, V, and T relationships.
- Use the slider to adjust pressure.
- Observe the phase boundary.
:::

::: {.column width="50%"}
<iframe 
  data-src="media/plots/sample.html" 
  width="100%" 
  height="500px" 
  style="border:none;" 
  scrolling="no">
</iframe>
:::
::::

---

# Bibliography
<div id="refs"></div>

---

:::: {.columns}
::: {.column width="50%"}
### Analyzing Student Attributes
Here's an interactive plot showing the relationship between student height and weight, categorized by sex. This visualization helps us identify any patterns or distributions within the dataset.

**Key observations:**
- Explore how height and weight vary for male and female students.
- Identify potential outliers.
:::

::: {.column width="50%"}
<iframe 
  data-src="media/plots/height_weight_scatter.html" 
  width="100%" 
  height="500px" 
  style="border:none;" 
  scrolling="no">
</iframe>
:::
::::

---

:::: {.columns}
::: {.column width="100%"}
### Key Statistics for PartLength
These statistics provide a summary of the 'PartLength' data for Machine 1 at Temperature 303 and Pressure 100.

- **Mean Part Length:** 49.3168
- **Median Part Length:** 49.2987
- **Standard Deviation of Part Length:** 0.5229

**Interpretation:**
- The mean and median indicate the central tendency of the part lengths.
- The standard deviation measures the spread or variability of the part lengths around the mean. A lower standard deviation suggests more consistent part production.
:::
::::

---

:::: {.columns}
::: {.column width="50%"}
### Control Chart for Part Resistance
This chart displays individual observations of 'Part Resistance' over time for a specific machine and process conditions. The center line represents the average part resistance, while the Upper Control Limit (UCL) and Lower Control Limit (LCL) indicate the boundaries within which the process is considered statistically in control. Points falling outside these limits suggest potential anomalies or shifts in the manufacturing process.

**Analysis:**
- Observe if any data points exceed the UCL or LCL.
- Look for trends or patterns that might indicate a process instability.
:::

::: {.column width="50%"}
<iframe
  data-src="media/plots/xbar_one_chart_resistance.html"
  width="100%"
  height="500px"
  style="border:none;"
  scrolling="no">
</iframe>
:::
::::

---

:::: {.columns}
::: {.column width="100%"}
### Key Statistics for PartResistance
These statistics provide a summary of the 'PartResistance' data for Machine 1 at Temperature 303 and Pressure 100.

- **Mean Part Resistance:** 5.1202
- **Median Part Resistance:** 5.1522
- **Standard Deviation of Part Resistance:** 0.3499

**Interpretation:**
- The mean and median indicate the central tendency of the part resistances.
- The standard deviation measures the spread or variability of the part resistances around the mean. A lower standard deviation suggests more consistent part production.
:::
::::
