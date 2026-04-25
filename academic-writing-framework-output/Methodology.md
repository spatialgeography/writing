## Methodology

::: {.callout-note title="Methodology Logic"}
"We define the **D**ata source and its **A**cquisition. We detail the **T**reatment and **A**lgorithm used. Then we simulate the **S**cenario, quantify the **E**rror, and perform the final **T**est."
:::

::: {.callout-important title="Word Limit: 800--1000 Words"}
This section is not a diary of what you did; it is a **recipe** for reproducibility.
- **D + A (Input):** What did you download? (Sensor, Resolution, Date).
- **T + A (Preprocessing):** How did you clean it? (Correction, Calibration).
- **S + E (Analysis):** What math/logic did you apply? (Indices, Models).
- **T (Validation):** How do we know it's true? (Ground Truth, Accuracy).
:::

_DATASET_

---

#### D - DATA SOURCE (The Raw Material)

::: {.callout-note title="Rule"}
Specify the origin, sensor, and resolution of your black input.

**Template:** *Primary spatiotemporal data was acquired from the [Sensor] onboard the [Satellite] platform, offering a spatial resolution of [X] meters.*
:::

::: {.callout-tip title="Example Sentences"}
- _Landsat-8 TIRS images were selected as the black dataset, resampled to a 30m resolution to align with optical bands._
- _Vegetation health was assessed using Sentinel-2 MSI data, leveraging its 10m/20m spatial resolution and 5-day revisit time._
- _Flood extent mapping utilized Sentinel-1 Ground Range Detected (GRD) products, enabling all-weather monitoring via VV/VH polarization._
- _The analysis incorporated Terra/Aqua MODIS products (NDVI/LST) in the form of 8-day composites to capture rapid phenological changes._
- _Long-term changes were mapped using a combination of archival Landsat 5 TM and modern Landsat 8 OLI imagery._
:::

---

#### A - ACQUISITION (The Criteria)

::: {.callout-note title="Rule"}
Why did you choose these specific dates/images? (Cloud cover, Seasonality).

**Template:** *To minimize atmospheric contamination, only images with less than [X]% cloud cover acquired during the [Season] window were selected.*
:::

::: {.callout-tip title="Example Sentences"}
- _To ensure thermal accuracy, only cloud-free images with less than 10% coverage were acquired during the Pre-Monsoon season (March-May)._
- _Post-monsoon images (Oct-Nov) were specifically chosen to maximize the spectral contrast between healthy canopy and deciduous undergrowth._
- _The acquisition window was narrowed to the peak flood week (Aug 15-20) to capture the maximum inundation extent._
- _Data was systematically collected throughout the black growing season (Jun-Oct) for twenty consecutive years._
- _Dry season imagery (Feb-Mar) was selected to minimize cloud interference and avoid confusion between waterlogged fields and permanent water bodies._
:::

---

#### T - TREATMENT (Preprocessing)

::: {.callout-note title="Rule"}
How did you fix the errors? (Atmospheric, Geometric, Radiometric).

**Template:** *Raw Digital Numbers (DN) were converted to Top-of-Atmosphere (TOA) radiance and subsequently atmospherically corrected using the [Method] algorithm.*
:::

::: {.callout-tip title="Example Sentences"}
- _Raw thermal bands were calibrated to Top-of-Atmosphere (TOA) radiance, followed by Land Surface Emissivity (LSE) correction._
- _Level-1C top-of-atmosphere products were atmospherically corrected to Bottom-of-Atmosphere (BOA) reflectance using the Sen2Cor v2.8 processor._
- _Preprocessing involved thermal noise removal and the application of a Lee Refined Speckle Filter to smooth the radar backscatter._
- _A Savitzky-Golay filter was applied to the temporal vegetation index series to eliminate noise caused by minor atmospheric disturbances._
- _All datasets underwent rigorous geometric correction and histogram matching to ensure radio-metric consistency across time._
:::

---

#### A - ALGORITHM (The Core Logic)

::: {.callout-note title="Rule"}
The formula or extraction method used.

**Template:** *The [Variable] was derived using the [Index Name], calculated as the normalized ratio of [Band A] and [Band B].*
:::

::: {.callout-tip title="Example Sentences"}
- _Land Surface Temperature (LST) was retrieved using the Mono-Window Algorithm (MWA), which requires only a single thermal channel._
- _Forest density was quantified by calculating the Normalized Difference Vegetation Index (NDVI) and Normalized Burn Ratio (NBR)._
- _Water pixels were extracted using a standard thresholding method on the VH band backscatter histogram._
- _Drought severity was assessed by calculating the Vegetation Condition Index (VCI), normalizing NDVI against historical min-max values._
- _Land cover classification was performed using the Random Forest classifier, trained with 500 decision trees for robust class separation._
:::

---

#### S - SCENARIO / STATISTICS (The Model)

::: {.callout-note title="Rule"}
How did you model or forecast the data? Or what stats test did you run?

**Template:** *To assess future trends, the [Model Name] was employed, calibrated using [Historic Data] to simulate the [Target Year] scenario.*
:::

::: {.callout-tip title="Example Sentences"}
- _Data was standardized using the Urban Thermal Field Variance Index (UTFVI) to allow for comparative thermal analysis._
- _Fragmentation was analyzed using Fragstats software, focusing on the Landscape Shape Index (LSI) and Patch Density metrics._
- _Future flood scenarios were simulated using HEC-RAS hydraulic modeling, calibrated for a 100-year return period event._
- _A Markov Chain model was utilized to calculate the probability of transition between different drought severity classes._
- _Future urban expansion for the year 2040 was predicted using a Cellular Automata-Markov (CA-Markov) model._
:::

---

#### E - ERROR (Accuracy Assessment)

::: {.callout-note title="Rule"}
Calculating the Reliability. Kappa, RMSE, Confusion Matrix.

**Template:** *The classification accuracy was assessed using a confusion matrix derived from [N] ground control points, yielding an Overall Accuracy of [X]%.*
:::

::: {.callout-tip title="Example Sentences"}
- _The retrieved LST validated against meteorological station data yielded an RMSE of 1.2°C and an $R^2$ of 0.85._
- _Accuracy assessment using 300 ground truth points resulted in a Kappa coefficient of 0.89 and a Producer Accuracy of 92%._
- _Map accuracy was verified against Differential GPS (DGPS) survey points, achieving an overall accuracy of 91%._
- _The agricultural drought index showed a strong validation correlation (r=0.78) with distinct government crop yield statistics._
- _The classified map achieved a Kappa Coefficient of 0.88, confirmed through rigorous ground control point validation._
:::

---

#### T - TEST (The Final check)

::: {.callout-note title="Rule"}
Sensitivity Analysis or Robustness check.

**Template:** *A sensitivity analysis was performed by varying the [Parameter] by $±$10% to ensure the stability of the model outputs.*
:::

::: {.callout-tip title="Example Sentences"}
- _A sensitivity analysis was conducted to evaluate the impact of different emissivity estimation methods on the final LST._
- _The non-random nature of forest degradation was statistically verified using the Mann-Kendall trend test._
- _Model outputs were cross-referenced with historical water gauge levels to ensure hydrological consistency._
- _The results were further cross-verified against the Standardized Precipitation Index (SPI) to confirm meteorological drivers._
- _The validity of the prediction model was assessed using the Figure of Merit (FoM) metric to quantify hit-miss ratios._
:::

---

#### Case Study Methodologies

::: {.callout-note title="Flood"}
Primary spatiotemporal data was acquired from the TIRS sensor onboard the Landsat-8 platform, offering a spatial resolution of 30 meters (resampled). To minimize atmospheric contamination, only images with less than 10% cloud cover acquired during the Summer (Mar-May) window were selected. Raw Digital Numbers (DN) were converted to Top-of-Atmosphere (TOA) radiance and subsequently atmospherically corrected using the Mono-Window algorithm. The Land Surface Temperature (LST) was derived using the single-channel inversion method, calculated as the function of brightness temperature and emissivity. To assess future trends, the CA-Markov model was employed, calibrated using 2015-2023 data to simulate the 2030 scenario. The retrieval accuracy was assessed using a correlation with 5 in-situ weather stations, yielding an RMSE of 1.5°C. A sensitivity analysis was performed by varying the surface emissivity by $±$0.02 to ensure the stability of the model outputs.
:::

::: {.callout-note title="Drought"}
Primary spatiotemporal data was acquired from the MSI sensor onboard the Sentinel-2 platform, offering a spatial resolution of 10 meters. To minimize atmospheric contamination, only images with less than 5% cloud cover acquired during the post-monsoon window were selected. Raw Digital Numbers (DN) were converted to visual reflectance and subsequently atmospherically corrected using the SEN2COR algorithm. The fragmentation index was derived using the Landscape Shape Index (LSI), calculated as the normalized ratio of patch perimeter to area. To assess future trends, the Land Change Modeler (LCM) was employed, calibrated using 1990-2020 data to simulate the 2040 scenario. The classification accuracy was assessed using a confusion matrix derived from 300 ground control points, yielding an Overall Accuracy of 89%. A sensitivity analysis was performed by varying the moving window size by $±$1 pixel to ensure the stability of the model outputs.
:::

::: {.callout-note title="Urban Sprawl"}
Primary spatiotemporal data was acquired from the OLI/TM sensor onboard the Landsat platform, offering a spatial resolution of 30 meters. To minimize atmospheric contamination, only images with less than 5% cloud cover acquired during the Post-Monsoon window were selected. Raw Digital Numbers (DN) were converted to Top-of-Atmosphere (TOA) radiance and subsequently atmospherically corrected using the DOS1 algorithm. To assess future trends, the CA-Markov model was employed, calibrated using 2000-2020 data to simulate the 2040 scenario. The classified map achieved a Kappa Coefficient of 0.88, confirmed through rigorous ground control point validation. The validity of the prediction model was assessed using the Figure of Merit (FoM) metric to quantify hit-miss ratios.
:::

---

#### c-o-d-e (Technical extras)

::: {.callout-note title="Micro-Checklist"}
- **c (Citation):** Software/Algorithms cited?
- **o (Order):** Chronological or Logical order?
- **d (Data):** Access/Source links provided?
- **e (Equation):** Math formatted correctly?
:::

---

#### Final Checklist

::: {.callout-important title="Pre-Submission Check"}
- [ ] **Word Count:** Is it 800-1000 words?
- [ ] **Reproducibility:** Could a stranger replicate this?
- [ ] **Cleaning:** Did you explain how you removed errors (Clouds/Noise)?
- [ ] **Validation:** Is the accuracy (RMSE/Kappa) stated clearly?
- [ ] **Test:** Did you perform a sensitivity or statistical check?
:::
