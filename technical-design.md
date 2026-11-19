# EmberSight technical design

**Development Status: In Progress** — implementation plan.

## Scope and approach

Fuse documented public data into a transparent grid risk model, show uncertainty and source timestamps, and let users compare simulated response scenarios. Outputs are planning demonstrations, not operational incident guidance.

### Spatial contract
Normalize inputs to one coordinate reference system, resolution, and timestamp convention. Each tile records source, version, refresh time, missing-data mask, and transformation steps.

### Risk model
Use a transparent weighted baseline over fuel, slope, and recent weather. Keep the weights and data date visible. Missing inputs lower confidence; they must not silently become zero risk.

### Scenario model
Compare user-selected simulated interventions under the same weather and ignition assumptions. Show sensitivity to changed assumptions. The MVP does not predict exact fire spread or recommend evacuation.

### Evaluation
Backtest historical periods where data is available. Measure ranking quality, calibration by risk band, spatial coverage, freshness, and scenario sensitivity. Publish data limitations alongside metrics.

## Quality and operating requirements

Use public or licensed data with attribution, validate geospatial uploads, control external API costs, and prominently label simulated outputs and uncertainty.

The first implementation should include structured logs, explicit failure handling, bounded retries where external services are involved, and a reproducible local run path. Proposed services and models may change after the baseline is measured.
