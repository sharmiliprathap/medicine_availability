# Do Higher Drug Prices Correlate with Higher Stock Availability in India’s E‑Pharmacy Market?
A study of how brand pricing, competition, and therapeutic categories shape medicine availability on Tata 1mg.

## Background
In India, the same drug molecule is often sold by dozens of brands at very different prices. Patients typically see only brand names, not the molecule itself. This creates a common belief: higher price means better availability. There is no public dataset that tests this assumption, so I built my own dataset from Tata 1mg and analyzed it.

### The questions I wanted to answer through my analysis were:

- How large is the price variation for identical molecules of different brands?
- Are premium brands more reliably available?
- Does competition between brands improve availability?
- Which therapeutic categories are most supply‑unstable?

## Data
This dataset was constructed by scraping Tata 1mg listings. It contains 1,893 cleaned brand listings across four therapeutic classes (Diabetes, Cardiac, Antibiotics, Pain Relief). Each record includes molecule, strength, brand, price, availability, manufacturer, and dosage form.

## Tools I Used
- **Python (BeautifulSoup, Selenium, Pandas):** Core scraping, cleaning, feature engineering, and analysis.
- **Power BI:** Executive dashboard with interactive visuals and slicers.
- **Visual Studio Code:** Main development environment.

## Power BI Dashboard
![](dashboard.gif)
[:bar_chart: View Interactive Power BI Dashboard](https://app.powerbi.com/view?r=eyJrIjoiMTViYjA0ZDYtZTAxOS00MzMzLWI4MjMtYzY1MDJjNDFiMWVlIiwidCI6ImQyMDI4YzQzLWRmNDQtNGVmNi05Yjg5LTY3YTMzOWM1M2QyMyJ9)

## The Analysis

### 1. Price Dispersion / Variation
To measure market price inefficiency, I grouped listings by molecule and compared the cheapest and most expensive brand prices, then calculated the percentage variation. The largest variation occurred for Ibuprofen 400 mg, showing a 9,483% premium between the cheapest and most expensive listings. This confirmed that identical molecules can exhibit extreme price gaps.

However, this outlier was inflated by dosage form differences (IV infusion vs tablet). To correct for this, I extracted dosage form from brand names and recalculated dispersion within the same form (molecule + form). The form‑controlled results provide a true like‑for‑like comparison and prevent infusions from distorting the tablet market story. 
This time, the analysis showed the true form-controlled price dispersion of about 8,000%+, which is still extremely high. This confirms that even after removing formulation mismatch, substantial brand-level price variation remains.

### 2. Price vs Availability (Premium Protection Hypothesis)
I tested whether higher prices actually deliver better reliability by assigning price tiers within each molecule (Budget, Mid, Premium), so “premium” is defined relative to each molecule’s own price distribution.

Availability increased from 56.7% (Budget) to 64.8% (Mid) to 71.9% (Premium). The premium-to-budget gap is about 15.2 percentage points, which is directionally positive but still modest relative to the very large price gaps observed in dispersion analysis.

### 3. Market Competition vs Availability
To test whether availability is driven by competition, I measured brand density (number of competing brands per molecule) and linked it to molecule-level availability.

The relationship was weak: brand density vs availability correlation was about 0.066 (and manufacturer density vs availability about 0.041). This indicates competition helps only at the margin and is not a strong standalone driver of availability reliability.

### 4. Therapeutic Class vs Availability
I compared average availability across therapeutic classes to identify category-level supply risk.

Average availability was Cardiac: 78.7%, Antibiotics: 77.9%, Diabetes: 52.5%, and Pain Relief: 42.0%. The spread between the highest and lowest classes is about 36.7 percentage points, showing substantial structural differences in access across therapeutic categories.

## What I Learned
Building a reliable dataset was the hardest part. Scraped listings required extensive cleaning, deduplication, and dosage‑form correction. The analysis showed that pricing is highly inefficient, and premium brands provide only limited availability advantages. Competition helps somewhat, but availability appears more driven by category‑level supply dynamics.

## Limitations
- Listings reflect online availability, not physical pharmacy stock.
- Dosage‑form extraction is based on naming patterns and may miss edge cases.
- The study covers selected molecules, not the entire market.

## Conclusions

### Insights
Identical medicines can differ in price by thousands of percent. Premium brands are only slightly more reliable, and competition is a weak driver of availability. Category risk is a stronger signal than price.

### Business Implications
Healthcare systems should promote generic substitution and improve price transparency.
Pharmacies should stock multiple interchangeable brands to stabilize supply.
High‑risk categories (pain relief, diabetes) need stronger supply planning.
