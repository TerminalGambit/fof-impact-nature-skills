# Free / public data sources for nature-related risk diligence

Curated for LEAP-Locate and LEAP-Evaluate. All sources below are free for at least basic use; several have paid tiers for portfolio-scale or commercial use. Confirm licence terms before reproducing data in client-facing deliverables.

## Biodiversity & protected areas

### IBAT — Integrated Biodiversity Assessment Tool
- **Covers:** World Database on Protected Areas (WDPA), Key Biodiversity Areas (KBA), IUCN Red List of Threatened Species
- **Use for:** screening whether a site/asset overlaps with or sits near a protected area, KBA, or threatened-species range
- **Access:** Free for non-commercial / limited use; subscription tiers for commercial portfolio-scale analysis
- **URL:** https://www.ibat-alliance.org

### Protected Planet (WDPA / WD-OECM)
- **Covers:** The underlying WDPA dataset and the World Database on Other Effective Area-based Conservation Measures
- **Use for:** raw protected-area boundaries
- **Access:** Free download for non-commercial use
- **URL:** https://www.protectedplanet.net

### IUCN Red List
- **Covers:** Threatened-species assessments and range maps
- **Use for:** species-level risk screening, e.g., for biotech bioprospecting or infrastructure routing
- **Access:** Free for non-commercial use
- **URL:** https://www.iucnredlist.org

### GBIF — Global Biodiversity Information Facility
- **Covers:** Species occurrence records, aggregated from museums, surveys, citizen science
- **Use for:** species presence near sites; baseline biodiversity context
- **Access:** Free, open
- **URL:** https://www.gbif.org

## Forests & deforestation

### Global Forest Watch
- **Covers:** Tree cover loss (annual, since 2000), deforestation alerts (weekly), primary forest, peatlands, plantations, fires
- **Use for:** sourcing-region deforestation footprints, commodity-driven loss, primary forest overlap
- **Access:** Free; API available
- **URL:** https://www.globalforestwatch.org

### Trase
- **Covers:** Commodity supply-chain traceability linking production regions to traders to consumer markets (soy, beef, palm, cocoa, coffee, others)
- **Use for:** identifying which sourcing regions and traders dominate a buyer's exposure
- **Access:** Free; data downloads available
- **URL:** https://trase.earth

## Freshwater

### WRI Aqueduct
- **Covers:** Baseline water stress, water depletion, seasonal variability, groundwater stress, flood risk (riverine, coastal), drought risk
- **Use for:** site-level water risk screening at watershed scale
- **Access:** Free; data downloads and API
- **URL:** https://www.wri.org/aqueduct

### WWF Water Risk Filter
- **Covers:** Site-level physical, regulatory, and reputational water risk; portfolio-level rollup
- **Use for:** portfolio screening of water-stressed exposure
- **Access:** Free with registration
- **URL:** https://riskfilter.org/water

## Multi-pressure biodiversity risk filters

### WWF Biodiversity Risk Filter
- **Covers:** Site- and portfolio-level screening across biodiversity-related physical, regulatory, and reputational risk
- **Use for:** rapid first-pass nature risk screening, especially in financial portfolios
- **Access:** Free with registration
- **URL:** https://riskfilter.org/biodiversity

## Oceans & coasts

### UNEP-WCMC Ocean+ Data Platform
- **Covers:** Marine and coastal data — protected areas, biodiversity, ecosystem extent (mangroves, seagrass, coral)
- **Access:** Free for most layers
- **URL:** https://data.unep-wcmc.org

### Allen Coral Atlas
- **Covers:** Global coral reef maps and bleaching alerts
- **Access:** Free
- **URL:** https://allencoralatlas.org

### Global Fishing Watch
- **Covers:** Vessel-level fishing activity, transhipment, port visits
- **Use for:** shipping route and fisheries exposure
- **Access:** Free with registration
- **URL:** https://globalfishingwatch.org

## Sector dependency & impact screening

### ENCORE
- **Covers:** Materiality of dependence and impact for sub-industries against ecosystem services and pressures
- **Use for:** LEAP-Evaluate sector screening
- **Access:** Free with registration
- **URL:** https://encorenature.org

### SBTN sector materiality screens
- **Covers:** SBTN's Step 1 materiality screens for science-based nature target setting
- **Use for:** structured prioritisation when moving from disclosure to target-setting
- **Access:** Free; published as guidance documents
- **URL:** https://sciencebasedtargetsnetwork.org

## Climate-nature crossovers

### Climate Watch (WRI)
- **Covers:** Country-level emissions, NDCs, sectoral data
- **Use for:** linking nature exposure to climate policy context
- **Access:** Free
- **URL:** https://www.climatewatchdata.org

### Climate TRACE
- **Covers:** Facility-level GHG emissions inventory from remote sensing
- **Use for:** independent verification of asset-level emissions, including land-sector
- **Access:** Free
- **URL:** https://climatetrace.org

## Indigenous & local communities

### LandMark
- **Covers:** Indigenous and community lands, mapped where data exists
- **Use for:** screening sites for overlap with indigenous and community territories — a critical TNFD social-criterion check
- **Access:** Free
- **URL:** https://www.landmarkmap.org

## Tips for using these in practice

- **Layer, don't substitute.** No single source covers nature comprehensively. A defensible LEAP-Locate typically layers IBAT + Aqueduct + Global Forest Watch + WWF Risk Filters at minimum.
- **Coordinates matter.** Site-level screening requires lat/long. If the GP only has admin-region data, flag the precision loss explicitly.
- **Mind the licence.** Several "free" tools have non-commercial-only terms. For LP-facing deliverables built on portfolio-scale screening, the paid tiers (IBAT, MSCI ESG nature, S&P Sustainable1, ISS ESG biodiversity, ENCORE Plus) are often the licensed path.
- **Note the vintage.** Many global biodiversity layers update annually or less; deforestation alerts are weekly. Always cite the data version in the memo.
- **Don't over-precision.** Many of these layers are modelled at 250m–10km resolution. Treat outputs as risk signals, not measurements.
