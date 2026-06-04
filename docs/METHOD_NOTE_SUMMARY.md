# Methodology Summary

**Scope:** Roll‑rate migration analysis, vintage lifecycle metrics and scenario stress testing implemented in Power BI.

Data inputs
- **Exposure ledger:** monthly exposure by account, product, origination date, balance and status.  
- **Delinquency flags:** DPD buckets (0, 1–30, 31–60, 61–90, 90+).  
- **Origination cohorts:** vintage identifiers (month/year) and origination metrics.  
- **External assumptions:** macro shocks and PD/flow adjustments provided as scenario inputs.

Core calculations
- **Roll‑rate matrix:** exposure‑weighted migration probabilities between DPD buckets computed on a monthly vintage basis.  
- **CDR and cohort metrics:** cohort cumulative default rates, exposure run‑off curves, WAL and monthly decay.  
- **Scenario engine:** user‑defined shocks applied to baseline migration matrices; scenario propagation computes delta EL, NPL and Cost of Risk via waterfall decomposition.  
- **Attribution:** segment and vintage attribution of EL and NPL changes using exposure weighting and marginal contribution.

Validation and governance
- **Back‑testing:** historical roll‑rate reproduction and EL reconciliation against realized outcomes.  
- **Sanity checks:** exposure balancing, null handling, and outlier trimming rules.  
- **Auditability:** all transformation steps are documented in the data model; key measures include calculation comments and sample SQL/Power Query snippets.

Limitations and assumptions
- **Sanitised demo:** public preview uses anonymised sample data; production deployment requires tenant data mapping and reconciliation.  
- **Model scope:** this is an analytics and scenario engine; it does not replace regulatory model validation — use as decision support and scenario quantification.  
- **Data quality dependency:** accuracy depends on ledger completeness and consistent delinquency tagging.

Implementation notes
- **Power BI:** model built in Power BI Desktop with parameterised scenario tables and measure library for reusability.  
- **Deployment:** recommended deployment path is Power BI Service with row‑level security and scheduled refresh; for enterprise scale use Premium or Embedded.
