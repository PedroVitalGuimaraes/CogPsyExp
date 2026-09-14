# Sound Context & Personality on Memory

A browser-deployable cognitive psychology experiment built with **OpenSesame** and deployed to participants via a **Mindprobe/JATOS** server. It investigated how auditory contexts and personality traits shape word memorization and recognition. Originally developed for my Psychology Master's dissertation at University of Porto (FPCEUP).

This repository hosts a [Demo](https://jatos.mindprobe.eu/publix/HtaLYctpiUo) of the experiment: a shortened, English-translated build intended to showcase the experimental design and technical implementation.

## Experiment Overview

1. **Memorization tasks** - 4 sets of 5 words, each accompanied by a different sound condition (silence, music, office, home).
2. **Personality questionnaire (TIPI)** - a Ten-Item Personality Inventory, presented on a 1-7 scale.
3. **Recognition tasks** - previously seen words are mixed with new distractor words; participants judge old/new (`S` / `N` keys) and, for recognized items, identify the original sound context (`M` = music, `C` = home, `E` = office, `S` = silence).
4. **Sociodemographic questionnaire** - brief background questions.

The full dissertation study ran two complete memorization–recognition cycles with counterbalanced sound-condition ordering. This demo runs a **single abbreviated cycle** to illustrate the paradigm.

## Script
**OpenSesame's Graphical Interface**

The trial structure, timing, stimulus presentation, and response collection are all defined through built-in item types (`sequence`, `sketchpad`, `sampler`, `loop`, `keyboard_response`).

**Inline JavaScript**

- **Free-text and numeric response capture** - the questionnaires need participants to type multi-character answers rather than pressing a single key. Since OpenSesame's native `keyboard_response` item is built around single-keypress events, the `process_input_sd` and `process_input_ti` scripts manually accumulate keystrokes into a growing string, handle `backspace` to delete the last character, and detect `enter` to submit the response.

- **Variable initialization** - small `init_sd` / `init_ti` scripts reset the response buffer (`vars.multichar_response`) before each question loop begins, ensuring old input doesn't leak into the next question.

## Tech Stack & References

- **Experiment builder:** [OpenSesame](https://osdoc.cogsci.nl/) 4.1.0a6

Mathôt, S., Schreij, D., & Theeuwes, J. (2012). OpenSesame: An open-source, graphical experiment builder for the social sciences. *Behavior Research Methods*, 44(2), 314–324. [doi:10.3758/s13428-011-0168-7](https://doi.org/10.3758/s13428-011-0168-7)

- **Deployment:** [JATOS](https://www.jatos.org/) — Just Another Tool for Online Studies

Lange, K., Kühn, S., & Filevich, E. (2015). "Just Another Tool for Online Studies" (JATOS): An easy solution for setup and management of web servers supporting online studies. *PLoS ONE*, 10(6), e0130834.
[doi:10.1371/journal.pone.0130834](https://doi.org/10.1371/journal.pone.0130834)
- **Personality Questionnaire:** TIPI - Ten-Item Personality Inventory

Nunes, A., Limpo, T., Lima, C.F., & Castro, S. L. (2018). Short scales for the assessment  of personality traits: Development and validation of the Portuguese Ten-Item Personality Inventory (TIPI).
Frontiers in Psychology, 9(461). [doi:10.3389/fpsyg.2018.00461](https://doi.org/10.3389/fpsyg.2018.00461)
- **Dissertation:**

Guimarães, P. V. (2022). ***O papel moderador da extroversão no efeito da música na memória episódica***. [Dissertação de Mestrado, Universidade do Porto]. Repositório Aberto da Universidade do Porto.
[doi:10.34626/ethm-n129](https://doi.org/10.34626/ethm-n129)
