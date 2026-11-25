# Experiment Diagnostics: Homepage A/B Test

## 1. Executive Summary

The experiment evaluated whether the new homepage variant improved signup conversion without negatively affecting revenue or specific user segments.

The Variant achieved a statistically significant conversion improvement over Control. However, the observed lift did not meet the predefined Minimum Detectable Effect (MDE) of +0.50 percentage points.

More importantly, the Variant generated significantly lower 30-day revenue per user, and its conversion performance differed significantly between Desktop and Mobile users.

**Recommendation: Do not proceed with an immediate full rollout.** Investigate the revenue decline and Mobile experience before making a rollout decision.

## 2. Experiment Health: Sample Ratio Mismatch

The experiment was expected to allocate users equally between Control and Variant.

| Metric | Result |
|---|---:|
| Control users | 25,053 |
| Variant users | 24,947 |
| Expected users per arm | 25,000 |
| Chi-square statistic | 0.2247 |
| p-value | 0.6355 |

The chi-square test found no statistically significant sample allocation imbalance (p = 0.6355).

**Conclusion:** No evidence of Sample Ratio Mismatch (SRM) was detected. The experiment passed this health check.

## 3. Primary Metric: Signup Conversion

The primary metric was the proportion of users who completed signup.

| Metric | Control | Variant |
|---|---:|---:|
| Users | 25,053 | 24,947 |
| Completed signups | 712 | 802 |
| Conversion rate | 2.8420% | 3.2148% |

### Statistical Test

A two-sample proportion Z-test was used to compare signup conversion rates.

| Metric | Result |
|---|---:|
| Absolute lift | +0.3728 percentage points |
| Z-statistic | 2.4326 |
| p-value | 0.014990 |
| 95% Wald confidence interval | [+0.0724 pp, +0.6733 pp] |

The conversion improvement is statistically significant at the 5% significance level. The confidence interval excludes zero.

### Minimum Detectable Effect Assessment

The predefined MDE was +0.50 percentage points.

The observed lift was +0.3728 percentage points, approximately 74.56% of the target MDE.

Although the confidence interval extends above +0.50 percentage points, the observed point estimate does not meet the predefined practical-effect threshold.

**Conclusion:** The Variant improved signup conversion statistically, but the observed improvement did not meet the target MDE.

## 4. Revenue Guardrail: 30-Day ARPU

The experiment's revenue guardrail was evaluated using average revenue per user (ARPU) over 30 days.

A Welch's two-sample t-test was used because it does not assume equal population variances.

| Metric | Control | Variant |
|---|---:|---:|
| Total 30-day revenue | $83,011.10 | $72,753.34 |
| Average revenue per user | $3.3134 | $2.9163 |

| Statistical Metric | Result |
|---|---:|
| ARPU difference (Variant − Control) | −$0.3971 |
| Welch's t-statistic (Control − Variant) | 2.1411 |
| p-value | 0.032274 |

Variant ARPU was approximately 11.98% lower than Control ARPU. The difference was statistically significant at the 5% level.

**Conclusion:** The Variant failed the revenue guardrail. The conversion improvement came alongside a statistically significant decline in 30-day revenue per user.

## 5. Temporal Stability: Novelty Check

Conversion performance was compared across the first and second weeks of the experiment.

| Metric | Week 1 | Week 2 |
|---|---:|---:|
| Control conversion | 2.9128% | 2.7723% |
| Variant conversion | 3.3874% | 3.0443% |
| Absolute lift | +0.4746 pp | +0.2720 pp |

The observed conversion lift declined by approximately 0.2026 percentage points between the two weeks, a reduction of approximately 42.7% relative to Week 1's lift.

**Conclusion:** The results suggest a possible novelty effect or weakening treatment impact over time. However, this comparison is descriptive; a formal treatment-by-week interaction test would be needed to establish whether the decline is statistically significant.

## 6. Device-Level Performance

The experiment showed substantially different conversion outcomes across device segments.

| Metric | Desktop | Mobile |
|---|---:|---:|
| Control conversion | 3.3936% | 2.2880% |
| Variant conversion | 4.3083% | 2.1311% |
| Absolute lift | +0.9147 pp | −0.1569 pp |

Desktop users responded positively to the Variant, while Mobile users experienced a decline in conversion.

### Device Interaction Test

A logistic regression model including experiment arm, device, and their interaction was used to assess whether the treatment effect differed by device.

| Metric | Result |
|---|---:|
| Interaction coefficient | −0.3208 |
| Standard error | 0.109 |
| z-statistic | −2.955 |
| p-value | 0.003 |
| 95% confidence interval | [−0.534, −0.108] |

The negative interaction coefficient was statistically significant. This provides evidence that the treatment effect differs between Desktop and Mobile users.

**Conclusion:** The overall positive conversion result masks meaningful device-level differences. The Variant performs positively on Desktop but negatively on Mobile.

## 7. Final Assessment and Recommendation

### Summary of Findings

| Diagnostic | Result | Assessment |
|---|---|---|
| Sample Ratio Mismatch | p = 0.6355 | Passed |
| Signup conversion | p = 0.014990 | Statistically significant improvement |
| MDE | +0.3728 pp vs +0.50 pp | Target not met |
| Revenue guardrail | p = 0.032274 | Failed |
| Temporal stability | Lift declined by 0.2026 pp | Potential novelty concern |
| Device interaction | p = 0.003 | Significant device divergence |

### Recommendation

The Growth Team's recommendation to ship immediately is not supported by the complete diagnostic evidence.

Although the Variant produced a statistically significant signup conversion improvement, three important concerns remain:

1. The observed conversion lift did not reach the predefined +0.50 percentage-point MDE.
2. The Variant produced significantly lower 30-day ARPU.
3. The treatment effect differed significantly by device, with Mobile users experiencing a negative conversion lift.

The Week 1 versus Week 2 comparison also indicates that the conversion improvement weakened over time, although this decline has not yet been formally tested for statistical significance.

**Recommended next steps:**

- Investigate why 30-day ARPU declined under the Variant.
- Review the Mobile homepage experience and identify potential usability or performance issues.
- Conduct further experimentation after addressing the identified concerns.
- Evaluate treatment stability over a longer observation period.

**Final decision: Do not ship the Variant universally at this stage.** The conversion improvement alone is insufficient to justify rollout when revenue and Mobile conversion performance show statistically significant negative outcomes.
