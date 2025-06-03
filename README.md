Here is a draft **README** for your Colab project notebook `GEOL0069_End_of_year_assignment__DU_LIU.ipynb`, incorporating your specified points in a structured and formal academic style:

---

# 🌍 Inland Water Detection Using Sentinel-2 and K-Means Clustering

### *GEOL0069 End-of-Year Assignment – Du Liu*

---

## 📌 1. Project Overview

This project addresses the challenge of **automated inland water body detection** using satellite imagery. Accurately identifying open water surfaces is crucial for hydrological monitoring, ecosystem assessment, and climate-related water resource management. The method combines **remote sensing spectral indices** (NDWI and NDVI) with **unsupervised machine learning (K-Means clustering)** to detect and characterize inland water bodies. The regions studied are the **Sacramento Delta (USA)** and **Loburu Delta (Kenya)** using **Sentinel-2 MSI** data.

---

## 🌐 2. Remote Sensing Technique

The primary technique employed is **spectral index-based detection** using:

* **NDWI (Normalized Difference Water Index)** to detect surface water.
* **NDVI (Normalized Difference Vegetation Index)** to provide contextual land cover information.

NDWI is calculated using the green and near-infrared (NIR) bands of Sentinel-2:

$$
\text{NDWI} = \frac{B3 - B8}{B3 + B8}
$$

NDVI is calculated as:

$$
\text{NDVI} = \frac{B8 - B4}{B8 + B4}
$$

These indices are then thresholded and clustered to delineate land cover types, especially water bodies.

And also for the geometric correction workflow which is used to precisely geolocate Sentinel-2 MSI imagery. Image datation, along with satellite attitude (roll, pitch, yaw) and position (X, Y, Z in WGS84), is used to define the spacecraft reference frame. Attitude is corrected using bias and drift, while position is adjusted using a second-degree polynomial function. This reference frame is transformed into the MSI instrument frame, which is then split into VNIR and SWIR focal plane frames. Each focal plane corresponds to specific spectral bands (B1–B9 for VNIR, B10–B12 for SWIR), and transformations are applied to account for band-dependent geometry. Band 4 is used as the geometric reference segment to align all other bands through correlation, ensuring accurate co-registration and ground mapping of all spectral information.

![Image Alt]([image_url](https://github.com/caiiiiy1/0069final22081852/blob/main/%E5%B1%8F%E5%B9%95%E6%88%AA%E5%9B%BE%202025-06-03%20084546.jpg?raw=true))


---

## 🤖 3. AI Algorithm – K-Means Clustering

K-means clustering was used to classify each pixel based on multi-band or index values. The iterative process follows these steps:

1. Initialize `k` centroids randomly.
2. Assign each data point to the nearest centroid.
3. Recalculate centroids based on the mean of assigned points.
4. Repeat until centroids stabilize.



---

## 💻 4. Code Implementation (Summary)

The notebook includes the following components:

* **Data Preprocessing:** Sentinel-2 bands (B3, B4, B5, B8, B11) loaded, rescaled, and masked.
* **Index Calculation:** NDWI and NDVI indices computed.
* **Binary Masking:** Threshold-based water and vegetation classification.
* **K-Means Clustering:** Applied to index features and selected band combinations (e.g., B5 & B11).
* **Confusion Matrix Evaluation:** Accuracy of clustering against NDWI water mask.
* **Region Comparison:** Sacramento vs. Loburu Delta performance assessment.

*Note: All code cells are fully documented and runnable in Google Colab.*

---

## 🌱 5. Environmental Cost

This project uses **cloud-based computing (Google Colab)**, which incurs environmental cost through energy-intensive data processing. To reduce carbon footprint:

* **Efficient libraries** (NumPy, scikit-learn) were used.
* **Selective visualization** and sampling strategies reduced unnecessary computation.
* Downloaded imagery was limited to **specific areas and bands**, minimizing storage and I/O energy.


---

## 🛰️ 6. Data Source

All satellite data used in this project were acquired from the [Copernicus Data Space Ecosystem (ESA)](https://browser.dataspace.copernicus.eu/).

* **Sentinel-2 MSI (Multispectral Instrument) Level-2A data**
* Bands used: B3 (Green), B4 (Red), B5 (Red Edge), B8 (NIR), B11 (SWIR)
* AOIs: Sacramento Delta (North America), Loburu Delta (Kenya)

---

## 📚 7. References

1. www.esa.int. (n.d.). Facts and figures. [online] Available at: https://www.esa.int/Applications/Observing_the_Earth/Copernicus/Sentinel-2/Facts_and_figures.
2. Copernicus.eu. (2015). S2 Processing. [online] Available at: https://sentiwiki.copernicus.eu/web/s2-processing.
3. Github.io. (2025). Unsupervised Learning — GEOL0069 Guide Book. [online] Available at: https://cpomucl.github.io/GEOL0069-AI4EO/Chapter1_Unsupervised_Learning_Methods_2.html [Accessed 3 Jun. 2025].
4. Orr, J., Gibbons, O. and Arnold, W. (2020). A brief guide to calculating embodied carbon. [online] Available at: https://www.istructe.org/IStructE/media/Public/TSE-Archive/2020/A-brief-guide-to-calculating-embodied-carbon.pdf.
5. Datacenters.google. (2025). Blocked. [online] Available at: https://datacenters.google/efficiency/.
6. Arxiv.org. (2020). Holistically Evaluating the Environmental Impact of Creating Language Models. [online] Available at: https://arxiv.org/html/2503.05804v1 [Accessed 3 Jun. 2025].
7. Ruff, L. (2017). Carbon Intensity. [online] Carbonintensity.org.uk. Available at: https://carbonintensity.org.uk/.
8. Owen, R.A., Owen, R.B., Renaut, R.W., Scott, J.J., Jones, B. and Ashley, G.M. (2008). Mineralogy and origin of rhizoliths on the margins of saline, alkaline Lake Bogoria, Kenya Rift Valley. Sedimentary Geology, 203(1-2), pp.143–163. doi:https://doi.org/10.1016/j.sedgeo.2007.11.007.
9. Evers, J. (2022). Delta | National Geographic Society. [online] education.nationalgeographic.org. Available at: https://education.nationalgeographic.org/resource/delta/.
10. EOS Data Analytics (2017). NDWI: Normalized Difference Water Index In Agriculture. [online] eos.com. Available at: https://eos.com/make-an-analysis/ndwi/.
11. GIS Geography (2018). What Is NDVI (Normalized Difference Vegetation Index)? - GIS Geography. [online] GIS Geography. Available at: https://gisgeography.com/ndvi-normalized-difference-vegetation-index/.
12. Ali, A. and Adebayo, A.O. (2019). Data Mining Application Using Clustering Techniques (K-Means Algorithm) In The Analysis Of Student’s Result. [online] Available at: https://www.researchgate.net/publication/333508765_Data_Mining_Application_Using_Clustering_Techniques_K-Means_Algorithm_In_The_Analysis_Of_Student%27s_Result/figures?lo=1.
13. Jiang, W., Ni, Y., Pang, Z., He, G., Fu, J., Lu, J., Yang, K., Long, T. and Lei, T. (2020). A NEW INDEX FOR IDENTIFYING WATER BODY FROM SENTINEL-2 SATELLITE REMOTE SENSING IMAGERY. ISPRS Annals of the Photogrammetry, Remote Sensing and Spatial Information Sciences, V-3-2020, pp.33–38. doi:https://doi.org/10.5194/isprs-annals-v-3-2020-33-2020.
14. Copernicus Browser. (n.d.). Copernicus Browser. [online] Available at: https://browser.dataspace.copernicus.eu/.


---
