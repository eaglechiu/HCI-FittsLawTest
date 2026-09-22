[English](./README.md) | [繁體中文](./README_zh-TW.md)

# HCI-FittsLawTest

**[Open the Online Experiment](https://eaglechiu.github.io/HCI-FittsLawTest/)**

This Human–Computer Interaction (HCI) experiment studies Fitts' Law and target geometry through marker selection on an interactive map.

Participants locate and click a cyan target marker while one to five gray distractor markers are displayed. The experiment controls movement distance, marker circumradius, and movement direction to examine how target shape affects selection time and misses.

| Experimental factor | Configuration |
| --- | --- |
| Target shape | 8 shapes |
| Circumradius (R) | 30, 50, and 70 px |
| Center-to-center movement distance (A) | 280 and 520 px |
| Movement direction | 0°, 60°, 120°, 180°, 240°, and 300° |
| Recorded trials | 48 conditions × 6 trials per condition = 288 trials |
| Sessions | 2 sessions with 144 trials each |

> **Research interpretation:** The original report treats the data as a within-user pilot study. The 288 repeated measurements do not represent 288 independent participants; the reported p-values are exploratory and cannot be generalized directly to the broader user population. The custom radius-based Index of Difficulty (ID_R) is also not equivalent to the conventional index defined using directional width (W).

## Getting Started

1. Open the [online experiment](https://eaglechiu.github.io/HCI-FittsLawTest/) in a desktop browser. No installation is required.
2. Follow the on-screen instructions, locate the cyan marker, and click it. Each condition begins with an unrecorded warm-up positioning trial, followed by six recorded selections.
3. After completing both sessions, use the page's export function to save the results. Use **Export / Import Progress** when moving progress between browsers or devices.

The site is hosted with GitHub Pages. You can also download the [HTML file](./fitts_interactive_map_6dir.html) and run it locally. Progress is stored in the browser's `localStorage`; export a backup before changing browsers or clearing site data. The downloaded and online versions do not automatically share progress. To transfer it, select `Download Progress Backup` on the original page, then use `Import Progress` on the new page. The map requires sufficient desktop display space to accommodate the maximum movement distance of 520 px.

## Experiment Demo

Watch the interactive map marker selection experiment:

https://github.com/user-attachments/assets/2a0c2c05-e243-43af-ab42-e0e72b4fa22c

## Contents

- [Full Report](#full-report)
- [1. Executive Summary](#1-executive-summary)
- [2. Scenario, Innovation, and Application](#2-scenario-innovation-and-application)
- [3. Experimental Design](#3-experimental-design)
- [4. Results](#4-results)
- [5. Discussion](#5-discussion)
- [6. Limitations](#6-limitations)
- [7. Conclusion](#7-conclusion)
- [Appendix A. Key dataset checks](#appendix-a-key-dataset-checks)

## Files

| Path | Contents |
| --- | --- |
| [`index.html`](./index.html) | GitHub Pages entry point |
| [`fitts_interactive_map_6dir.html`](./fitts_interactive_map_6dir.html) | Six-direction interactive map experiment |
| [`README.md`](./README.md) | English project overview and full report |
| [`README_zh-TW.md`](./README_zh-TW.md) | Traditional Chinese project overview and full report |
| [`assets/report/`](./assets/report/) | Five figures from the original report |

<a id="full-report"></a>

## Full Report

### Effects of Target Geometry on Fitts-Law-Based Selection in an Interactive Map

AI-Assisted Fitts' Law Experiment and Empirical Analysis

| Field | Details |
| --- | --- |
| Course / Assignment | HCI - Fitts' Law Experiment, Part II |
| Scenario | Interactive Monitoring Map marker selection |
| Dataset | 288 recorded trials, two sessions |
| Student | [邱奕高 / 112034011] |
| Date | 2026/09/20 |

### 1. Executive Summary

Research question. When movement distance and nominal marker radius are controlled, does marker geometry contribute additional variation in selection time in an interactive map task?

Main result. The radius-based Fitts model MT = 263.38 + 165.44 ID_R explained 20.0% of trial-level variance (R² = 0.200). Averaging the six repetitions within each Shape × Radius × Distance condition increased R² to 0.494. When marker shape was averaged out and only the six Radius × Distance conditions remained, R² reached 0.949, indicating a strong underlying Fitts-like relationship.

Interpretation. Distance and radius behaved as expected: farther targets were slower and larger targets were faster. Shape and movement direction added systematic variation beyond ID_R, while distractor count (1-5) and session number did not show detectable effects in the current dataset. The experiment therefore supports a map-marker design interpretation rather than a pure two-target Fitts task.

### 2. Scenario, Innovation, and Application

#### 2.1 Scenario

The experiment represents an interactive monitoring map containing multiple geometric markers. On each trial, one marker is highlighted in cyan while one to five distractor markers are displayed in gray. The participant must identify and click the cyan marker as quickly and accurately as possible. The next target is placed at a controlled center-to-center movement distance from the previously selected target.

#### 2.2 Innovation

Conventional Fitts-style tasks primarily manipulate target distance and target size. This experiment adds target geometry as a controlled factor while maintaining a fixed color rule and balanced movement directions. The goal is to test whether different geometric markers with the same nominal radius behave as equally selectable targets.

#### 2.3 Practical application

The findings are relevant to map, dashboard, and monitoring interfaces that use geometric symbols to encode different object or event types. If equal nominal radius does not produce equal selection performance across shapes, interface designers may need shape-specific minimum marker sizes or larger invisible hit areas for geometrically difficult markers.

### 3. Experimental Design

#### 3.1 Independent and dependent variables

| Variable | Levels / definition |
| --- | --- |
| Target shape | 8 shapes: Circle, Hexagon, Rounded Square, Rounded Triangle, Rounded Star, Square, Triangle, Star |
| Nominal radius R | 30, 50, 70 px |
| Movement distance A | 280, 520 px (center-to-center) |
| Movement direction | 0°, 60°, 120°, 180°, 240°, 300°; each appears once per condition |
| Distractors | 1-5 gray markers; approximately balanced across trials |
| Dependent variables | Selection time (MT), misses, click endpoint, endpoint error |

#### 3.2 Radius-based Fitts model

Because the experimental size parameter is the marker circumradius rather than a conventional directional target width, the analysis uses a custom radius-based index of difficulty:

ID_R = log₂(1 + A / R)

The fitted linear model is MT = a + b·ID_R. This should be interpreted as a Fitts-like extension for the present marker geometry experiment, not as a replacement for the conventional width-based Shannon formulation.

#### 3.3 Trial structure and balancing

The full factorial design contained 8 shapes × 3 radius levels × 2 distance levels = 48 experimental conditions. Each condition contained six recorded trials, one in each of the six movement directions. This produced 288 recorded trials. The experiment was split equally across two sessions (144 trials per session) and the data were merged for analysis. Distractor markers used the same radius as the target, targets were always cyan, distractors were gray, and Star/Triangle families retained the incoming-tip orientation rule.

### 4. Results

#### 4.1 Fitts-like regression

| Analysis level | Regression / result | R² |
| --- | --- | --- |
| 288 individual trials | MT = 263.38 + 165.44·ID_R | 0.200 |
| 48 Shape × R × A condition means | Same fitted slope/intercept after balanced averaging | 0.494 |
| 6 R × A means | Shape averaged out | 0.949 |

![Figure 1. Trial-level relationship between radius-based index of difficulty and selection time.](./assets/report/figure-1-trial-regression.png)

*Figure 1. Trial-level relationship between radius-based index of difficulty and selection time.*

![Figure 2. Condition means reduce trial-to-trial noise and reveal a stronger Fitts-like relationship.](./assets/report/figure-2-condition-regression.png)

*Figure 2. Condition means reduce trial-to-trial noise and reveal a stronger Fitts-like relationship.*

#### 4.2 Radius and distance effects

| Factor | Level | Mean MT (ms) |
| --- | --- | --- |
| Radius | 30 px | 889.0 |
| Radius | 50 px | 798.4 |
| Radius | 70 px | 690.7 |
| Distance | 280 px | 734.3 |
| Distance | 520 px | 851.0 |

Increasing radius from 30 to 70 px reduced mean MT by 198.3 ms. Increasing movement distance from 280 to 520 px increased mean MT by 116.7 ms. Both trends are consistent with the expected direction of Fitts-style difficulty.

![Figure 3. Mean selection time decreases with radius and increases with distance.](./assets/report/figure-3-radius-distance.png)

*Figure 3. Mean selection time decreases with radius and increases with distance.*

#### 4.3 Shape effect

| Shape | Mean MT (ms) | SE (ms) |
| --- | --- | --- |
| Circle | 686.5 | 21.3 |
| Hexagon | 708.7 | 24.6 |
| Rounded Square | 770.1 | 28.5 |
| Rounded Triangle | 807.3 | 38.6 |
| Rounded Star | 811.2 | 28.9 |
| Square | 811.4 | 31.2 |
| Triangle | 857.7 | 59.3 |
| Star | 888.5 | 38.9 |

Adding Shape to the ID_R-only model increased R² from 0.200 to 0.285. In the multivariable model, the overall Shape effect was statistically detectable (Type-II ANOVA p = 1.31e-05). Circle had the lowest mean MT (686.5 ms), whereas Star had the highest (888.5 ms). These differences are descriptive within this dataset and should not be generalized to a population from a single-participant pilot.

![Figure 4. Mean selection time by marker shape. Error bars show standard error.](./assets/report/figure-4-shape.png)

*Figure 4. Mean selection time by marker shape. Error bars show standard error.*

#### 4.4 Direction, distractors, and session

| Direction | Trials | Mean MT (ms) |
| --- | --- | --- |
| 0° | 48 | 800.5 |
| 60° | 48 | 786.8 |
| 120° | 48 | 896.2 |
| 180° | 48 | 779.3 |
| 240° | 48 | 741.1 |
| 300° | 48 | 752.2 |

Movement direction was balanced exactly (48 trials per direction) and showed a detectable overall effect (p = 0.0009). This is a useful secondary finding because direction can be controlled statistically without being confounded with shape.

![Figure 5. Mean selection time by movement direction. Each direction contains 48 trials.](./assets/report/figure-5-direction.png)

*Figure 5. Mean selection time by movement direction. Each direction contains 48 trials.*

Distractor count did not show a detectable linear effect after controlling for the other factors (p = 0.593). Session also showed essentially no difference (Session 1 mean = 791.6 ms; Session 2 mean = 793.8 ms; p = 0.913). This supports combining the two sessions for the main analysis.

#### 4.5 Misses and accuracy

There were 15 recorded misses across 288 successful target selections. Misses decreased with radius: 8 at R=30 px, 6 at R=50 px, and 1 at R=70 px. Star and Triangle each accounted for 5 misses, while Circle, Hexagon, and Rounded Square had no recorded misses. Because the total error count is small, these values are best interpreted descriptively rather than as a strong inferential comparison.

#### 4.6 Multivariable model

| Predictor | Type-II ANOVA p-value | Interpretation |
| --- | --- | --- |
| ID_R | 6.35e-18 | Strong difficulty effect |
| Shape | 1.31e-05 | Additional geometry-related variation |
| Movement direction | 0.0009 | Systematic directional variation |
| Repetition | 0.0031 | Within-block order variability remains |
| Distractor count | 0.593 | No detectable linear effect |
| Session | 0.913 | No detectable session shift |

The full model (ID_R + Shape + Direction + Distractors + Session + Repetition) produced R² = 0.380 and adjusted R² = 0.334. The result suggests that Fitts-like difficulty remains the strongest single systematic component, but geometry and direction contribute additional explainable variance in the map-selection task.

### 5. Discussion

The experiment shows a clear separation between the underlying Fitts-like effect and the additional variability introduced by a more realistic map-selection context. When shape is averaged out, the six Radius × Distance means lie close to a linear Fitts-like relationship (R² = 0.949). However, trial-level R² is lower because the task also includes visual search, geometric differences, direction effects, and ordinary human motor variability.

The shape effect is especially relevant to interface design. Equal circumradius does not guarantee equal selection performance. In this dataset, circular and hexagonal markers were selected faster on average than star and triangle markers. A practical implication is that interfaces using irregular markers may benefit from larger minimum dimensions or invisible hitboxes that exceed the visual shape.

The distractor result is also useful. Varying the number of distractors from one to five did not create a detectable monotonic slowdown, suggesting that the fixed cyan-versus-gray visual rule kept search demands modest. This supports the scenario as a map-selection task without allowing visual search load to dominate the Fitts manipulation.

### 6. Limitations

- The dataset is a within-user pilot. The 288 trials are repeated measurements, not 288 independent participants; therefore, inferential p-values should be reported as exploratory and should not be generalized to a broader user population.

- The size variable R is a circumradius, not the conventional directional width W used in standard Fitts Law. The fitted ID_R should therefore be described explicitly as a custom radius-based index of difficulty.

- The selection-time measure includes target detection/search in addition to cursor movement. The scenario is intentionally more realistic than a pure two-target Fitts task, but this lowers trial-level R².

- Repetition order still showed detectable variability. A future study could counterbalance or model trial order more explicitly, or recruit multiple participants and use a mixed-effects model.

- Incoming-tip orientation was retained for Star and Triangle families, so geometry and orientation policy are linked for those shapes. Future work could compare fixed orientation against incoming-tip orientation as a separate factor.

### 7. Conclusion

The final experiment produced a complete and balanced dataset of 288 recorded selections. Distance and radius generated the expected Fitts-like pattern, with a trial-level regression of MT = 263.38 + 165.44·ID_R (R² = 0.200). Condition averaging increased R² to 0.494, and the six Radius × Distance means yielded R² = 0.949. Marker shape and movement direction explained additional performance variation, while distractor count and session did not show detectable effects. The results therefore support the report's main claim: in a realistic interactive-map task, distance and size remain important predictors of selection time, but marker geometry can add meaningful variation beyond a radius-only Fitts model.

### Appendix A. Key dataset checks

| Check | Result |
| --- | --- |
| Total recorded trials | 288 |
| Conditions | 48 (8 shapes × 3 radii × 2 distances) |
| Trials per condition | 6 |
| Directions | 6, exactly 48 trials each |
| Session balance | 144 + 144 |
| Distractor range | 1-5 markers |
| Total misses | 15 |
| MT range | 456.6 to 2573.5 ms |

