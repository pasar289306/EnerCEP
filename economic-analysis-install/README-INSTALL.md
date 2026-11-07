# Economic Analysis for MEASUR (EnerCEP) — install guide

Adds an **Economic Analysis** tab to the report of 8 tools: PSAT (pump), FSAT (fan), PHAST (furnace/process heating),
SSMT (steam), Compressed Air, Process Cooling, Water, Waste Water. Treasure Hunt is untouched.
Per measure: simple and discounted payback, NPV, IRR, benefit/cost ratio, cost of saved energy.
Then sensitivity (tornado, spider, two-way tables) and Monte Carlo (histogram, cumulative curve, correlations).

## Install (base = MEASUR v1.10.0)

The package is the file `economic-analysis.patch` (33 files: 28 changed, new ones added), built against the
unmodified MEASUR v1.10.0 source. From the project root:

    git apply --check economic-analysis.patch && git apply economic-analysis.patch

Alternative: unzip `EnerCEP-economic-analysis-overlay.zip` over the project root.

## Then

    npm install
    npm run build        # Angular was NOT compiled while writing this; report any error

## Push to EnerCEP

    git add -A && git commit -m "Add economic analysis" && git push -u origin main

## Check these things
1. SSMT: operating cost is treated as thousands of dollars per year (x1000), like the report's own payback.
   Compare the new simple payback with "Simple Payback Period" in the steam report.
2. SSMT energy = boiler fuel only; electricity changes appear in cost savings only.
3. Compressed air: salvage value is treated as money received at year 0 (reduces net investment).
4. Water has no modifications, so it analyses only the measures you enter by hand.
