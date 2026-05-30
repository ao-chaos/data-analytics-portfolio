# Data Analytics Portfolio

A collection of end-to-end data analytics projects built in Python, covering core techniques used in digital media, SaaS, and subscription businesses. Each project is fully reproducible from synthetic data, uses no external API dependencies, and demonstrates analytical thinking from raw data through to actionable business recommendations.

> **Note:** GitHub's notebook renderer requires pre-executed outputs to display correctly. To view the notebooks with all charts and outputs rendered, use the **nbviewer** links below.

---

## Projects

### 1. A/B Test Analysis — Subscription Page Redesign

**Notebook:** [ab_test_analysis.ipynb](ab_test_analysis.ipynb) · [**View on nbviewer**](https://nbviewer.org/github/ao-chaos/data-analytics-portfolio/blob/main/ab_test_analysis.ipynb)

#### Business Question
A digital media company redesigned its subscription landing page. Did the new design significantly improve conversion rates, and is it worth shipping to 100% of traffic?

#### What the Analysis Does

1. **Simulates an A/B experiment** — 8,000 users per variant with a control conversion rate of 2.8% and a variant rate of 3.6%, reflecting a realistic subscription funnel uplift scenario.
2. **Two-proportion z-test** — Calculates the z-statistic and two-tailed p-value (implemented from scratch using math.erfc — no scipy required), and determines statistical significance at alpha = 0.05.
3. **Chi-square test of independence** — Independently validates the z-test result using a 2x2 contingency table; cross-checks that z-squared equals chi-squared.
4. **Confidence intervals** — Computes 95% CIs for both conversion rates and the absolute lift, establishing whether the entire CI lies above zero.
5. **Power analysis** — Builds a sample size curve across a range of minimum detectable effects (MDEs), and confirms the test was adequately powered for the observed effect size.
6. **Business impact projection** — Translates the conversion lift into estimated annual revenue given 500,000 monthly page visitors and a £9.99/month subscription price.

#### Key Results
- Absolute lift: +1.04 percentage points | Relative lift: +37.2%
- p-value: 0.0002 — statistically significant at alpha = 0.05
- 95% CI for lift lies entirely above zero — positive effect confirmed
- Estimated annual revenue impact: ~£373,000
- **Recommendation: Ship the variant**

#### Skills Demonstrated
Statistical hypothesis testing · Confidence interval estimation · Power analysis · Business impact quantification · Data visualisation (matplotlib, seaborn)

---

### 2. Cohort Retention Analysis — Subscriber Lifecycle & LTV

**Notebook:** [cohort_retention_analysis.ipynb](cohort_retention_analysis.ipynb) · [**View on nbviewer**](https://nbviewer.org/github/ao-chaos/data-analytics-portfolio/blob/main/cohort_retention_analysis.ipynb)

#### Business Question
How are subscriber retention rates evolving across acquisition cohorts? Where does churn concentrate in the subscriber lifecycle, and what is the estimated lifetime value of each cohort?

#### What the Analysis Does

1. **Builds 12 monthly acquisition cohorts** (Jan–Dec 2024) — each cohort tracks the percentage of original subscribers still active at months 1 through 12. Later cohorts have fewer observed months (e.g. December has only month-0 data), accurately reflecting real-world data constraints.
2. **Retention heatmap** — Visualises the full cohort x month matrix with percentage annotations, making it easy to spot systematic improvements or anomalies across cohorts.
3. **Retention curves by cohort** — Plots all 12 cohorts on a single chart with a gradient colour scale (red to green across the year), showing how product and onboarding changes affected the retention trajectory over 2024.
4. **Average retention and monthly churn** — Computes the cross-cohort mean retention curve and derives the month-over-month churn rate (percentage point drop), identifying Month 1 as the critical drop-off point.
5. **Customer Lifetime Value (LTV)** — Calculates expected subscriber lifetime (sum of retention rates across observed months) multiplied by monthly price (£9.99) and gross margin (70%), to estimate LTV per cohort and total projected 2024 cohort revenue.
6. **Cohort trend analysis** — Plots Month-3 and Month-6 retention across cohorts with trend lines, providing a leading indicator of whether product changes are improving subscriber quality over time.

#### Key Results
- Average Month-1 churn: ~28% of new subscribers lost in the first month
- Retention stabilises at ~42% from Month 5 onwards (long-term retained base)
- Average LTV: ~£28 per acquired subscriber
- Month-3 retention trend: improving across 2024 cohorts — positive product signal

#### Skills Demonstrated
Cohort analysis · Retention modelling · Churn quantification · Customer LTV calculation · Heatmap visualisation · Time-series trend analysis

---

### 3. News Engagement Analysis — Editorial Performance Intelligence

**Notebook:** [news_engagement_analysis.ipynb](news_engagement_analysis.ipynb) · [**View on nbviewer**](https://nbviewer.org/github/ao-chaos/data-analytics-portfolio/blob/main/news_engagement_analysis.ipynb)

#### Business Question
Which content sections, publishing times, article lengths, and topics drive the highest reader engagement? How should an editorial team prioritise its output to maximise audience interaction?

#### What the Analysis Does

1. **Synthetic article dataset** — Generates 2,400 articles across Jan–Mar 2025 covering 7 sections (News, Politics, Technology, Culture, Sport, Business, Environment), with realistic section weights, word count distributions, and engagement scores. Publishing times follow an empirical hourly distribution that peaks at morning commute hours.
2. **Section performance overview** — Horizontal bar chart of article volume per section, plus a bubble chart plotting volume vs average engagement score (bubble size = avg word count), giving an at-a-glance editorial performance matrix.
3. **Timing analysis** — Four-panel chart covering: hourly publication volume and engagement, day-of-week patterns, a day-by-hour engagement heatmap, and monthly volume/engagement trends. Identifies optimal publishing windows for maximum reader reach.
4. **Article length vs engagement** — Groups articles into word count buckets (under 300 to over 1,600 words) and plots average engagement with 95% confidence intervals. A scatter plot by section with an OLS trend line shows the length-engagement relationship, quantified by Pearson r.
5. **Topic analysis** — Ranks the top 15 topics by article volume and the top 12 by average engagement score, with colour coding (green = above average, red = below average). Reveals which topics punch above their weight in engagement relative to publication frequency.
6. **Key findings and editorial recommendations** — Synthesises all four analyses into actionable guidance: best time to publish, optimal article length, highest-ROI topics, and weekend content strategy.

#### Key Results
- Technology and Politics sections achieve the highest average engagement scores (above 85/100)
- Morning commute window (7–9am) generates a measurable engagement uplift vs other hours
- Articles in the 900–1,200 word range consistently outperform shorter and longer pieces
- AI, cybersecurity, and policy topics lead engagement per article published

#### Skills Demonstrated
Exploratory data analysis (EDA) · Multi-panel data visualisation · Heatmap analysis · Correlation analysis · Segment-level performance benchmarking · Editorial data strategy

---

## Tech Stack

| Tool | Purpose |
|------|---------|
| Python 3 | Core language |
| NumPy / Pandas | Data generation and manipulation |
| Matplotlib / Seaborn | Visualisation |
| math (stdlib) | Statistical tests (z-test, chi-square) — no scipy dependency |
| Jupyter Notebook | Interactive presentation format |

---

## Running the Notebooks

```bash
git clone https://github.com/ao-chaos/data-analytics-portfolio.git
cd data-analytics-portfolio
pip install numpy pandas matplotlib seaborn
jupyter notebook
```

All notebooks use fixed random seeds and generate their own synthetic data — no external datasets or API keys required.

---

## About

Built as part of a data analytics portfolio targeting digital media and subscription business roles. Each project reflects the types of analysis performed in editorial intelligence, subscription growth, and product analytics teams.
