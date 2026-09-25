# Powerwise

Powerwise is an educational data visualisation website exploring television energy consumption in the Australian market. Built with HTML, CSS and JavaScript, it includes Home, Televisions and About Us pages with responsive layouts and JavaScript navigation.

The Televisions page presents seven research questions using eight static graphs exported from KNIME. These cover screen technologies, screen sizes, model counts by brand, power consumption and star ratings. Each question includes a short observation, graph captions and links to view the original images at full size. Findings reflect the supplied dataset and its groupings.

## About the data

### Data source

The supplied file, `tv_2026_09_10.csv`,  describes products and registrations. Fields include brand, model number, sales markets, screen size and technology, operating power, labelled annual energy consumption, star ratings and availability.

### Data processing

Graphs were exported from KNIME as PNG images and organised around seven research questions. The chart labels show counts grouped by technology, screen size and brand, a median power comparison by technology, and scatter plots exploring relationships between variables.

**KNIME workflow:** Data cleaning and filtering, duplicate removal, missing-value handling, brand-name standardisation and calculations.

The CSV was inspected separately for this documentation; the findings below describe the supplied file before any KNIME transformations. The CSV contains `screensize`, while the graphs use `screensize_inch`, so the unit conversion and rounding should be documented from the workflow. The exact filters, grouping keys and aggregation settings cannot be reconstructed from the CSV alone.

### Privacy

The CSV's fields describe television products and registrations, not individual consumers. No dedicated fields for customer names, contact details, household information or viewing histories were identified. Product and brand website links are included. The published graphs show product characteristics and grouped statistics. The website has no sign-in or data-entry forms and includes no application tracking code.

### Accuracy and limitations

Findings describe a dataset snapshot and do not establish current Australian retail availability. Model or record counts do not measure sales or consumer popularity. Inspection of the supplied CSV identified these limitations:

- **Market coverage:** 177 records do not list Australia in `SoldIn`, and 14 records are marked `Unavailable`. Australian availability comparisons depend on the filters applied in KNIME.
- **Repeated identifiers:** 5,015 rows contain 2,860 distinct `Submit_ID` values. An identifier can appear on multiple rows, so counting records or non-empty identifiers is not automatically a count of unique models.
- **Brand labels:** `SAMSUNG` and `SAMSUNG ELECTRONICS` appear separately. Brand totals depend on whether these labels were combined during processing.
- **Rating fields:** treating blanks, `-` and `N/A` as missing, `Star` has 4,704 missing entries and `SRI` has 4,707. `Star2` and `Star Rating Index` have none under that check. The chosen rating field therefore matters; completeness alone does not validate its values.
- **Comparability:** power differences may reflect screen size and the mix of models. Operating power and labelled energy consumption in kWh/year are different measures. Relationships in the charts do not establish cause and effect.

These checks do not verify the KNIME workflow or prove that every exported graph uses the same records. The static images do not update automatically.

### Ethics

The visualisations are intended for education, rather than product endorsements. Conclusions should remain within the dataset's coverage, acknowledge uncertainty and avoid treating a brand or technology as universally better based on these graphs alone. The original provider should be credited, and the dataset's licence or usage conditions checked before redistribution.

## Project structure

- `T01/index.html` — shared page structure and navigation.
- `T01/home.js`, `televisions.js` and `about.js` — page content.
- `T01/script.js` — navigation and footer updates.
- `T01/styles.css` — shared styling and responsive layouts.
- `T01/public/` — the logo and exported KNIME graphs.

## Running the site

Open `T01/index.html` in a browser with JavaScript enabled, or serve the `T01` folder using a local web server. No dependency installation or build step is required. Alternatively, use XAMPP to act as the local server and run it from the admin config.

For Vercel deployment, set Root Directory to `T01`, Framework Preset to **Other**, and Output Directory to `.`. Enable the Build Command override and leave its text field completely blank.

[View the live website](https://data-viz-t01.vercel.app/)

## Acknowledgement

OpenAI ChatGPT assisted with code, website content and documentation.
