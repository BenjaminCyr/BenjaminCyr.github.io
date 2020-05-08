---
classes: wide
title: "The Photoelectric Effect"
categories:
    - Research
tags:
    - Light Injection
    - Physics
bibliography: laser.bib

---
<script src="https://polyfill.io/v3/polyfill.min.js?features=es6"></script>
<script id="MathJax-script" async src="https://cdn.jsdelivr.net/npm/mathjax@3/es5/tex-mml-chtml.js"></script>

## Light-Based Signal Injection


Some of my recent works on LiDAR[^1] and Light Commands[^2] have shown that different sensors are vulnerable to light-based signal injection. By modulating a laser with an external signal, whether that be a digital trigger sequence or an analog signal to change the intensity, these sensors can output data that does not represent the environment. In some systems, this can have consequences that can cause system failure or user exploitation. I'm seeking to prevent attacks like these, and to accomplish this, I'll be looking in depth at the physics of these sensors. I will start by looking at the Photoelectric Effect.

## The Photoelectric Effect

The photoelectric effect is a "phenomenon in which electrically charged particles are released from or within a material when it absorbs electromagnetic radiation"[^3]. 

### The History
The effect was discovered in 1887 by Heinrich Rudolf Hertz and Wilhelm Hallwachs when they noticed that when ultraviolet light changed the voltage when sparks occurred between two metal electrodes. Further study was performed by Philipp Lenard in 1902 where it was linked to the negatively charged electrons, and the energy of the electrons increased with the color (frequency) of the light. This was surprising, as Maxwell's wave model of light predicted that the electron energy would increase with intensity, not frequency. In 1905, Albert Einstein presented his theories on the Photoelectric Effect in one of his papers[^4], which was heavily influenced by the idea of "light quanta" or photons from Max Planck's 1901 work[^5]. Since the photoelectric effect could not fit into any of the previous theories of light, it helped support the modern theory of the wave-particle duality of light. 

### The Math
In Einstein's paper, he presented one of the fundamental equations of the photoelectric effect. The maximum kinetic energy $K_{max}$ of an ejected electron is

$$K_{max} = hf - \varphi$$

where $$h$$ is Planck's constant ($$6.626{\times}10^{-34} J{\cdot}s$$), $$f$$ is the frequency of the injected light (Hz), and $$\varphi$$ is the work function of the material (J). Every material has a different work function, as it corresponds to the amount of energy it takes to free an electron from the atom. The work function is affected by crystalline structure and temperature, but for most cases it can be considered a constant. This equation is important because it shows that the photoelectric effect will not occur unless the incident light is at a high enough energy (frequency) to overcome the work function. The minimum frequency is called the threshold frequency, and is denoted as $$f_0$$.

So let's just take the case of silicon. From the experimental results in the work by Alexander Novikov[^6] the work function ($$\varphi$$) of doped silicon is ~5eV for p-type silicon and ~4.5eV for n-type silicon (an electronvolt is equal to ~$$1.602{\times}10^{-19} J$$, so less energy is needed for the n-type silicon). So the minimum threshold frequency of light would need to be

$$f_0 = \frac{\varphi}{h}$$

$$f_0 = \frac{4.5eV * 1.602{\times}10^{-19}J}{6.626{\times}10^{-34} J{\cdot}s}$$

$$f_0 \approx 1088 THz$$

This makes $$f_0$$ an ultraviolet frequency, with a wavelength of 

$$\lambda = \frac{c}{f_0} \approx 275.5 nm$$

## Conclusion

In order to the the photoelectric effect in silicon, ultraviolet radiation or higher is necessary. Since most of the experiments on light-based signal injection have been performed with infrared or visible light, this makes the photoelectric effect an unlikely candidate for the phenomenon we are seeing, as this light does not have enough energy to free electrons from the atomic bands. Yet, there is another effect that shows more promise, where the photon energy does not need to be as high: the photovoltaic effect. I'll be investigating this physical phenomenon next.



[^1]: Yulong Cao, Chaowei Xiao, Benjamin Cyr, Yimeng Zhou, Won Park, Sara Rampazzi, Qi Alfred Chen, Kevin Fu, and Z. Morley Mao. 2019. Adversarial Sensor Attack on LiDAR-based Perception in Autonomous Driving. In Proceedings of the 2019 ACM SIGSAC Conference on Computer and Communications Security (CCS ’19). Association for Computing Machinery, New York, NY, USA, 2267–2281. DOI:[https://doi.org/10.1145/3319535.3339815](https://doi.org/10.1145/3319535.3339815){:target="_blank"}
  
[^2]: [https://lightcommands.com/](https://lightcommands.com/){:target="_blank"}

[^3]: [https://www.britannica.com/science/photoelectric-effect](https://www.britannica.com/science/photoelectric-effect){:target="_blank"}

[^4]: Einstein, Albert. "On a Heuristic Point of View about the Creation and Conversion of Light". Translated by Wikisource. [https://en.wikisource.org/?curid=59468](https://en.wikisource.org/?curid=59468){:target="_blank"}

[^5]: Planck, Max (1901). "Ueber das Gesetz der Energieverteilung im Normalspectrum (On the Law of Distribution of Energy in the Normal Spectrum)". Annalen der Physik. 4 (3): 553. [doi:10.1002/andp.19013090310](doi:10.1002/andp.19013090310){:target="_blank"}.

[^6]: Alexander Novikov, Experimental measurement of work function in doped silicon surfaces, Solid-State Electronics, Volume 54, Issue 1, 2010, Pages 8-13, ISSN 0038-1101, [https://doi.org/10.1016/j.sse.2009.09.005](https://doi.org/10.1016/j.sse.2009.09.005){:target="_blank"}. 
