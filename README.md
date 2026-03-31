# A/B Testing Case Study: Checkout Conversion Experiment

## Overview

This project simulates an A/B test evaluating whether a redesigned checkout experience improves user conversion rates compared to the existing interface.

The analysis follows an industry-style experimentation workflow including hypothesis testing, guardrail validation, power analysis, sample ratio mismatch detection, and heterogeneous treatment effect estimation across user segments.

The experiment is conducted on a simulated dataset of 20,000 users split evenly between control and treatment groups.

---

## Experiment Objective

The goal of the experiment is to determine whether a new checkout design increases purchase conversion rate without negatively impacting user experience metrics such as latency.

### Hypotheses

Null hypothesis (H₀):
The new checkout design does not change conversion rate.

Alternative hypothesis (H₁):
The new checkout design increases conversion rate.

---

## Dataset Description

Synthetic dataset with:

- 20,000 users
- 50/50 traffic allocation
- Baseline conversion rate: 10%
- Expected lift: +2 percentage points

Columns:

| Column | Description |
|--------|-------------|
| user_id | Unique identifier |
| variant | Control or treatment group |
| conversion | Purchase indicator (0/1) |
| latency_ms | Page latency (guardrail metric) |
| device | Mobile or desktop |
| user_type | New or returning |
| traffic_source | Organic, ads, referral |

---

## Metrics

### Primary Metric (Overall Evaluation Criterion)

Conversion rate = number of purchases / number of exposed users

---

### Guardrail Metrics

Used to ensure no negative impact on user experience:

- Page load latency

---

## Experiment Results

### Conversion Lift

Observed conversion rates:

| Variant | Conversion Rate |
|---------|-----------------|
| Control | 10.41% |
| Treatment | 11.88% |

Absolute lift:

+1.47 percentage points

Relative lift:

+14.17%

Two-proportion z-test:

p-value = 0.00046

Result:

Statistically significant improvement in conversion rate.

95% confidence interval:

[+0.60%, +2.35%]

---

## Guardrail Metric Validation

Latency comparison between variants:

p-value = 0.79

Conclusion:

No statistically significant degradation in performance.

---

## Sample Ratio Mismatch (SRM) Check

Expected allocation:

50 / 50 split

Chi-square test:

p-value = 0.777

Conclusion:

No evidence of assignment bias.

---

## Power Analysis

Required sample size per variant:

≈ 3,835 users

Actual sample size per variant:

≈ 10,000 users

Achieved statistical power:

≈ 0.995

Conclusion:

Experiment sufficiently powered to detect the target effect.

---

## Sensitivity Analysis (Minimum Detectable Effect)

With the current sample size, the experiment reliably detects conversion lifts of approximately:

≥ 1.3 percentage points

Smaller improvements would likely remain undetected.

---

## Segment-Level Treatment Effects

Treatment effect evaluated across multiple user segments.

### Device Type

| Device | Lift |
|--------|------|
| Desktop | +1.96% |
| Mobile | +1.16% |

Both segments show statistically significant improvements.

---

### User Type

| Segment | Lift |
|---------|------|
| New users | +2.05% |
| Returning users | +0.90% |

Treatment benefits new users more strongly.

---

### Traffic Source

| Source | Lift |
|--------|------|
| Ads | +1.59% |
| Organic | +1.30% |
| Referral | +1.72% |

Referral segment shows the largest observed improvement.

Segment-level hypothesis testing for referral traffic:

p-value = 0.040

Statistically significant at α = 0.05.

---

## Key Conclusions

- The redesigned checkout significantly improves conversion rate
- No latency regression detected
- Experiment allocation integrity confirmed (no SRM)
- Sample size sufficient to detect meaningful improvements
- Stronger treatment effects observed among new users and desktop users
- Referral traffic shows the largest observed segment-level lift

---

## Tools Used

- Python
- NumPy
- Pandas
- SciPy
- Statsmodels

---

## Future Improvements

Planned extensions:

- novelty effect detection across experiment duration
- multiple-testing correction across segments
- sequential testing methods
- visualization dashboards for experiment monitoring
