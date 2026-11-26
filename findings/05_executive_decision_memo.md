# Executive Decision Memo: Homepage A/B Test

**To:** Chief Product Officer, VP of Growth, Lead Product Manager  
**From:** Product Analytics  
**Subject:** Homepage Experiment — Global Rollout Decision

## 1. Executive Recommendation

**DO NOT SHIP GLOBALLY. Proceed with a STAGED DESKTOP ROLLOUT ONLY, subject to revenue guardrails and continued monitoring.**

The new homepage variant improved signup conversion statistically, but the observed lift fell short of the predefined minimum detectable effect (MDE). Furthermore, the variant significantly reduced 30-day revenue per user and produced negative conversion outcomes on Mobile. A controlled Desktop-only rollout is the recommended next step while the team investigates revenue deterioration and remediates the Mobile experience.

## 2. Statistical Findings & Evidence

| Finding | Evidence | Business interpretation |
|---|---|---|
| Conversion | +0.3728 pp; p = 0.01499 | Significant, but below +0.50 pp MDE |
| Revenue guardrail | ARPU: $3.3134 → $2.9163; −11.98%; p = 0.03227 | Statistically significant deterioration |
| Desktop | +0.9147 pp conversion lift | Strong positive response |
| Mobile | −0.1569 pp conversion lift | Negative treatment outcome |
| Device interaction | p = 0.003 | Treatment effect differs significantly by device |
| Temporal stability | Week 1: +0.4746 pp; Week 2: +0.2720 pp | Lift weakened by approximately 42.7% |

The experiment passed its Sample Ratio Mismatch check (p = 0.6355), supporting the validity of the allocation.

## 3. Business Impact & Stakeholder Considerations

**Why not ship when p < 0.05?**

Statistical significance establishes evidence of a difference, not that the difference is commercially worthwhile. The observed conversion lift of +0.3728 pp did not reach the predefined +0.50 pp MDE, while the revenue guardrail deteriorated significantly.

**Why not ship globally and fix Mobile later?**

The negative Mobile conversion lift (−0.1569 pp), combined with a significant device interaction (p = 0.003), indicates that a global rollout would expose a negatively responding segment to the treatment.

**Can we trust the initial conversion improvement?**

Week 2 conversion lift declined approximately 42.7% compared with Week 1. This suggests possible novelty decay, although a formal treatment-by-week interaction test is required to establish statistical significance.

## 4. Resolution & Next Steps

**Product & Growth**
- Authorize a controlled, staged Desktop-only rollout with a concurrent holdout.
- Monitor signup conversion, 30-day ARPU and revenue guardrails throughout rollout.
- Define rollback criteria before increasing exposure.

**Engineering & Design**
- Investigate Mobile usability, responsiveness and checkout friction.
- Run targeted Mobile remediation experiments before reconsidering Mobile deployment.

**Analytics**
- Investigate the drivers of the 11.98% ARPU decline.
- Run a formal treatment-by-week interaction test.
- Re-evaluate conversion and revenue performance over a longer observation period.

**Final Decision:** Reject global deployment. Advance only with a controlled Desktop-only rollout, while resolving Mobile friction and revenue risks before any broader release.