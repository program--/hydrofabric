
<!-- README.md is generated from README.Rmd. Please edit that file -->

# Climate

### Mean precipitation

> Mean daily precipitation (mm/day)

<span style="color:blue">We will use the daily GridMet files for pr\_\*
from 2000-2020. This will be used to compute a table with rows
representing catchments, and columns representing a daily catchment mean
</span>.

### Fraction of snow

> Fraction of precipitation falling as snow (i.e., on days colder than 0
> °C)

<span style="color:blue">We will use the daily GridMet files for
tmin\_\* from 2000-2020 to create a matrix mask. This mask will be
applied to the mean daily PPT matrix to compute the fraction.</span>

### Precip. seasonality

> Seasonality and timing of precipitation (estimated using sine curves
> to represent the annual temperature and preciptiation cycles, positive
> \[negative\] values indicate that precipitation peaks in summer
> \[winter\], values close to 0 indicate uniform precipitation ([eq
> 14](https://www.sciencedirect.com/science/article/pii/S030917080900102X))

<span style="color:red">NOT SURE YET.</span>

### High precip. frequency

> Frequency of high precipitation days (≥5 times mean daily
> precipitation) (days/year)

<span style="color:blue">Using the mean PPT matrix, the following will
be applied rowwise `(sum(x >= rowMean(.))` </span>.

### High precip. duration

> average duration of high precipitation events (number of consecutive
> days ≥5 times mean daily precipitation) (days)

<span style="color:blue">Will be computed from daily PPT matrix </span>.

### Low precip. frequency

> frequency of dry days (&lt;1 mm/day) (days/year)

<span style="color:blue">Will be computed from daily PPT matrix </span>.

### Low precip. duration

> average duration of dry periods (number of consecutive days &lt;1
> mm/day) (days)

<span style="color:blue">Using the mean PPT matrix, the following will
be applied rowwise `(sum(x <=1))` </span>.

### Mean PET

> Mean daily PET (estimated by N15 using Priestley-Taylor formulation
> calibrated for each catchment)

<span style="color:blue">We will use the daily GridMet files for pet\_\*
from 2000-2020 </span>.

### Aridity

> Aridity (PET/P, ratio of mean PET \[estimated by N15 using
> Priestley-Taylor formulation calibrated for each catchment\] to mean
> precipitation)

<span style="color:blue">We will create a single AI layer computed as
the mean annual PET divided by the mean annual PRCP </span>.

# Catchment

### Area

> Catchment area (Geospatial Fabric estimate) (km<sup>2</sup>)

<span style="color:blue">We be computed on hydrofabric
geometries`(sum(x >= rowMean(.))` </span>.

### Mean elevation

> Catchment mean elevation (meters)

<span style="color:blue">Will be extracted from NWM 1km geogrid `HGT_M`
</span>.

### Mean slope

> Catchment mean slope (m/km)

<span style="color:blue">Will be computed and extracted from NWM 1km
geogrid `HGT_M` </span>.

# Soil

### Geological permeability

> Subsurface permeability (log10) m2 from GLHYMPS

### Frac. carbonate sedimentary rock

> Fraction of the catchment area characterized as “Carbonate sedimentary
> rocks” from GLiM

### Clay fraction

> clay fraction (of the soil material smaller than 2 mm, layers marked
> as oragnic material, water, bedrock and “other” were excluded) %
> (STATSGO)

<span style="color:blue"> Will extract the `clay.bsq` file distributed
by Penn State and compute catchment mean </span>.

### Soil depth to bedrock

> silt fraction (of the soil material smaller than 2 mm, layers marked
> as oragnic material, water, bedrock and “other” were excluded) %
> (STATSGO)

<span style="color:blue">Will extract the `depth.bsq` file distributed
by Penn State and compute catchment mean </span>.

### Sand fraction

> sand fraction (of the soil material smaller than 2 mm, layers marked
> as organic material, water, bedrock and “other” were excluded) %
> (STATSGO)

<span style="color:blue">Will extract the `sand.bsq` file distributed by
Penn State and compute catchment mean </span>.

### Saturated hyd. conductivity

> saturated hydraulic conductivity (estimated using a multiple linear
> regression based on sand and clay fraction for the layers marked as
> USDA soil texture class and a default value \[36 cm/hr\] for layers
> marked as organic material, layers marked as water, bedrock and
> “other” were excluded) cm/hr [Table
> 4](https://agupubs.onlinelibrary.wiley.com/doi/epdf/10.1029/WR020i006p00682)

#### -0.60 + (0.0126 x %sand) - (0.0064 x %clay)

<span style="color:blue">Using the mean sand and clay percentages the
above formula can be applied</span>.

### Volumetric porosity

> volumetric porosity (saturated volumetric water content estimated
> using a multiple linear regression based on sand and clay fraction for
> the layers marked as USDA soil texture class and a default value
> \[0.9\] for layers marked as organic material, layers marked as water,
> bedrock and “other” were excluded)

#### 50.5 - (0.142 x %sand) - (0.037 x %clay)

<span style="color:blue">Using the mean sand and clay percentages the
above formula can be applied</span>.

### Soil depth

> soil depth (maximum 1.5 m, layers marked as water and bedrock were
> excluded) (m)

<span style="color:blue">Will extract the `depth.bsq` file distributed
by Penn State and compute catchment mean </span>.

### Silt fraction

> silt fraction (of the soil material smaller than 2 mm, layers marked
> as oragnic material, water, bedrock and “other” were excluded)

<span style="color:blue">Will extract the `silt.bsq` file distributed by
Penn State and compute catchment mean </span>.

### Max. water content

> maximum water content (combination of porosity and
> soil\_depth\_statsgo, layers marked as water, bedrock and “other” were
> excluded)

<span style="color:blue"> Multiply the porosity and the soil
depth</span>.

# Land Cover / Veg

## Frac. of Forest

> forest fraction

<span style="color:blue">Will extract the percent forest from the MODIS
land cover </span>.

## Max. green veg. frac. (GVF)

> maximum monthly mean of the green vegetation fraction (based on 12
> monthly means)

<span style="color:blue">Will Use MODIS 8 day NDVI to Compute GVF as
{(NDVI - NDVImax)/NDVImax-NDVImin </span>.

where NDVI is the NDVI value at a grid point i, NDVI is a global
constant given by the 5<sup>th</sup> percentile of NDVI<sub>max</sub>
for the barren land use class, and NDVI<sub>V</sub> is the 90th
percentile of NDVI<sub>max</sub> values for the land use class at grid
point i. As NDVI composites are collected over a longer time period, the
NDVImax can be periodically updated to reflect subtle variations in the
distributions of NDVI<sub>max</sub> by land-use classification.
[here](https://weather.msfc.nasa.gov/sport/modeling/modisGVF.html)

## Annual GVF diff.

> difference between the maximum and mimumum monthly mean of the green
> vegetation fraction (based on 12 monthly means)

## Annual leaf area index (LAI) diff.

> difference between the maximum and mimumum monthly mean of the leaf
> area index (based on 12 monthly means)

<span style="color:blue">Will Use Monthly MODIS LAI </span>.

## Max. LAI

> maximum monthly mean of the leaf area index (based on 12 monthly
> means)

<span style="color:blue">Will Use Monthly MODIS LAI </span>.