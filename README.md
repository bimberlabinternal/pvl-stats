This script contains several functions for computing outcomes on our longitudinal pVL data. If there are filters to determine if the data is valid for computing a given statistic, they're parameterized and given a reasonable default value. There are two main differentiating categories of subject in our data:

## ART
<img width="3600" height="2400" alt="pvl_29357" src="https://github.com/user-attachments/assets/62f48ed1-d379-4dc8-86c8-0cf1c6fb8700" />

## No ART
<img width="3600" height="2400" alt="pvl_18769" src="https://github.com/user-attachments/assets/32af928d-bc8a-45af-8740-ddb30cfd4d17" />

ART phases are mostly defined by provided anchor dates. Non-ART data are split into acute/chronic via a segmentation algorithm. The outcomes computed are the following:

- **acutePhasePeak_pVL**: The maximum viral load observed during the acute window (infection through art_start + 21 days for ART subjects, or computed via segmentation for non-ART subjects).
- **acutePhasePeak_day**: The days post infection at which acutePhasePeak_pVL occurs.
- **acutePhaseBurden**: Acute-phase viral load burden computed as AUC over dpi using trapezoidal integration, requiring at least 2 acute points.
- **dpiToART_LOD**: First dpi after which the on-ART series is considered under the detection threshold consistently (defined as the first of two consecutive points below LOD).
- **onArtBlipCount**: Count of blips during the on-ART period, defined as measurements after dpiToART_LOD that exceed LOD.
- **timeToRebound**: Time from ART release to first post-release measurement that exceeds 100 copies.
- **postReboundPeak_pVL**: Maximum viral load observed in the first 21 days after ART release.
- **postReboundPeak_day**: The dpi at which postReboundPeak_pVL occurs.
- **postReboundSetpoint**: Geometric mean viral load during the post-rebound setpoint period, defined here as measurements after art_end + 21 days (requires at least 3 points).
- **chronicPhaseSetpoint**: Geometric mean viral load during the chronic phase for No-ART subjects, which is derived by segmentation.
