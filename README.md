# HCI-FittsLawTest

以互動地圖標記選取研究菲茲定律（Fitts’ Law）與目標幾何形狀（Target Geometry）的人機互動（Human–Computer Interaction, HCI）實驗。

使用者在地圖上尋找並點擊青色目標標記（Target Marker），背景同時呈現 1–5 個灰色干擾標記（Distractor Markers）。本專案控制移動距離、標記外接圓半徑與移動方向，觀察不同形狀的選取時間（Selection Time）與誤點（Misses）。

| 實驗項目（Experimental Factor） | 設定（Configuration） |
| --- | --- |
| 目標形狀（Target Shape） | 8 種 |
| 外接圓半徑（Circumradius, R） | 30、50、70 px |
| 中心間移動距離（Center-to-center Movement Distance, A） | 280、520 px |
| 移動方向（Movement Direction） | 0°、60°、120°、180°、240°、300° |
| 正式試驗（Recorded Trials） | 48 個條件 × 每條件 6 次，共 288 次 |
| 實驗階段（Sessions） | 2 個階段，每階段 144 次 |

> **研究解讀：**原報告將資料定位為單一使用者的先導研究（Within-user Pilot Study）。288 次重複量測（Repeated Measurements）不等於 288 位獨立受試者；報告中的 p 值（p-values）屬探索性結果，不能直接推論至一般使用者族群。自訂的半徑式難度指標（Radius-based Index of Difficulty, ID_R）也不等同於傳統以方向寬度（Directional Width, W）定義的難度指標。

## 開始使用（Getting Started）

1. 下載 [fitts_interactive_map_6dir.html](./fitts_interactive_map_6dir.html)，以桌面瀏覽器（Desktop Browser）開啟。
2. 依頁面提示開始實驗，尋找並點擊青色標記；每個條件先完成不記錄的暖身定位（Warm-up Positioning），再進行六次正式選取。
3. 完成兩個實驗階段（Sessions）後，使用頁面上的匯出功能保存結果；需要轉移進度時，使用進度匯出／匯入（Export / Import Progress）。

實驗為單一 HTML 檔案，可直接在本機執行。進度保存在瀏覽器本機儲存空間（localStorage）；更換瀏覽器或清除網站資料前，請先匯出進度備份。地圖需要足夠的桌面顯示空間，才能容納最長的 520 px 移動距離。

## 內容導覽（Contents）

- [完整報告（Full Report）](#full-report)
- [1. Executive Summary](#1-executive-summary)
- [2. Scenario, Innovation, and Application](#2-scenario-innovation-and-application)
- [3. Experimental Design](#3-experimental-design)
- [4. Results](#4-results)
- [5. Discussion](#5-discussion)
- [6. Limitations](#6-limitations)
- [7. Conclusion](#7-conclusion)
- [Appendix A. Key dataset checks](#appendix-a-key-dataset-checks)

## 檔案（Files）

| 路徑（Path） | 內容（Contents） |
| --- | --- |
| [`fitts_interactive_map_6dir.html`](./fitts_interactive_map_6dir.html) | 六方向互動地圖實驗（Six-direction Interactive Map Experiment） |
| [`README.md`](./README.md) | 專案介紹、操作方式與完整報告（Full Report） |
| [`assets/report/`](./assets/report/) | 原報告的五張圖（Five Original Report Figures） |

<a id="full-report"></a>

## 完整報告（Full Report）

以下保留 `HCI_Fitts_Map_Marker_Report_EDITABLE.docx` 的英文全文、數值、八個表格與五張原圖，轉為適合網頁閱讀的 Markdown 格式。姓名、學號與繳交日期仍保留原報告的待填欄位。此處為既有報告的完整呈現，並未重新執行統計分析；原始試驗資料不包含在本次文件更新中。

### Effects of Target Geometry on Fitts-Law-Based Selection in an Interactive Map

AI-Assisted Fitts' Law Experiment and Empirical Analysis

| Field | Details |
| --- | --- |
| Course / Assignment | HCI - Fitts' Law Experiment, Part II |
| Scenario | Interactive Monitoring Map marker selection |
| Dataset | 288 recorded trials, two sessions |
| Student | \[Name / Student ID\] |
| Date | \[Submission date\] |

Replace bracketed placeholders before submission.

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

Suggested submission additions: GitHub Pages URL, screenshot or embedded screen recording, and any course-required citation/reference formatting.

