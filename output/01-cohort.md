# 01 — Return cohort

Source: `data/screenings.csv` (synthetic, 9,000 rows, one per customer, first screening 2025-01-01 to 2025-12-28). Export date 2026-09-30. Only columns defined in `data/README.md` are used. All numbers come from `scratchpad/cohort.py`.

## 1. Metric

**Second-screening return rate** = customers with a non-empty `second_screening_date` / customers in the cohort.

| | Numerator (returned) | Denominator | Rate |
|---|---|---|---|
| Naive, all customers | 304 | 9,000 | 3.4% |
| **Eligible cohort (headline)** | **287** | **5,773** | **5.0%** |

The naive rate counts customers who have not had a full year yet as "not returned", so it understates the return rate by 1.6 pp.

Time to return (from first to second screening, returners only): median **380 days** across all 304 returners (IQR 330–426, range 199–581). For the 287 eligible returners the median is 385 days. No second screening falls on or before the first screening date, and none falls after the export date.

## 2. Not yet eligible

- Eligible means `first_screening_date` ≤ 2025-09-30, so the customer has had at least 12 months to return. That gives **5,773 customers** (Jan to Sep 2025).
- **Not yet eligible:** 3,227 customers with a first screening from 2025-10-01 to 2025-12-28. They are **not counted as not returned**.
- **17 of these 3,227 have already returned** (208–345 days after the first screening). They are kept out of the headline rate.
- Eligible-cohort rate: **287 / 5,773 = 5.0%**.

Caveat: eligible customers do not all have the same amount of time. A January customer has had about 21 months and a September customer exactly 12. Because the median return comes after 380 days, longer follow-up mechanically raises the rate. As a check on equal footing, the rate for returning **within 365 days** of the first screening is 114 / 5,773 = **2.0%**.

## 3. Cuts (eligible cohort, n = 5,773)

Gap = percentage points against the best segment in the cut. Rows are sorted from the largest gap down. "Short" = n × gap, which is roughly how many more returns the segment would have at the best segment's rate. Segments with n < 100 are flagged *small*.

### result_category
| Segment | n | Returned | Rate | Gap (pp) | Short |
|---|---|---|---|---|---|
| unremarkable | 3,995 | 140 | 3.5% | −6.6 | 265 |
| referral_recommended | 564 | 24 | 4.3% | −5.9 | 33 |
| minor_findings | 1,214 | 123 | 10.1% | best | – |

### age_band
| Segment | n | Returned | Rate | Gap (pp) | Short |
|---|---|---|---|---|---|
| 18-39 | 1,313 | 36 | 2.7% | −3.9 | 51 |
| 40-59 | 2,414 | 116 | 4.8% | −1.8 | 43 |
| 60+ | 2,046 | 135 | 6.6% | best | – |

### location_type
| Segment | n | Returned | Rate | Gap (pp) | Short |
|---|---|---|---|---|---|
| mobile_unit | 302 | 3 | 1.0% | −4.9 | 15 |
| optician_chain | 2,360 | 100 | 4.2% | −1.7 | 40 |
| independent_optician | 3,111 | 184 | 5.9% | best | – |

### city
| Segment | n | Returned | Rate | Gap (pp) | Short |
|---|---|---|---|---|---|
| Freiburg | 412 | 13 | 3.2% | −4.3 | 18 |
| Hannover | 514 | 18 | 3.5% | −4.0 | 21 |
| Leipzig | 328 | 12 | 3.7% | −3.8 | 13 |
| Stuttgart | 394 | 15 | 3.8% | −3.7 | 15 |
| Köln | 653 | 26 | 4.0% | −3.5 | 23 |
| München | 332 | 14 | 4.2% | −3.3 | 11 |
| Bremen | 374 | 17 | 4.5% | −3.0 | 11 |
| Kassel | 163 | 8 | 4.9% | −2.6 | 4 |
| Dresden | 304 | 17 | 5.6% | −1.9 | 6 |
| Regensburg | 250 | 14 | 5.6% | −1.9 | 5 |
| Hamburg | 244 | 14 | 5.7% | −1.8 | 4 |
| Essen | 578 | 35 | 6.1% | −1.4 | 8 |
| Rostock | 232 | 15 | 6.5% | −1.0 | 2 |
| Nürnberg | 393 | 26 | 6.6% | −0.9 | 3 |
| Augsburg | 402 | 28 | 7.0% | −0.5 | 2 |
| Berlin | 200 | 15 | 7.5% | best | – |

The city counts are small (8 to 35 returns each), so most of these differences are within noise. City also overlaps with location_type and follow-up, which this cut does not separate.

### optician_follow_up (self-reported by the optician)
| Segment | n | Returned | Rate | Gap (pp) | Short |
|---|---|---|---|---|---|
| none | 3,192 | 132 | 4.1% | −4.1 | 131 |
| email | 1,854 | 95 | 5.1% | −3.1 | 58 |
| phone | 727 | 60 | 8.3% | best | – |

### Month of first_screening_date
| Segment | n | Returned | Rate | Gap (pp) | Short | Returned ≤365 d | Rate ≤365 d |
|---|---|---|---|---|---|---|---|
| 2025-06 | 702 | 24 | 3.4% | −3.9 | 27 | 12 | 1.7% |
| 2025-09 | 877 | 30 | 3.4% | −3.9 | 34 | 27 | 3.1% |
| 2025-08 | 713 | 28 | 3.9% | −3.4 | 24 | 13 | 1.8% |
| 2025-07 | 672 | 29 | 4.3% | −3.0 | 20 | 6 | 0.9% |
| 2025-04 | 599 | 33 | 5.5% | −1.8 | 11 | 11 | 1.8% |
| 2025-05 | 636 | 38 | 6.0% | −1.3 | 9 | 10 | 1.6% |
| 2025-03 | 611 | 37 | 6.1% | −1.3 | 8 | 13 | 2.1% |
| 2025-02 | 498 | 34 | 6.8% | −0.5 | 2 | 13 | 2.6% |
| 2025-01 | 465 | 34 | 7.3% | best | – | 9 | 1.9% |

The gap by month mostly reflects how long each month has been observed. With a fixed 365-day window the ordering does not hold (September becomes the highest month). **This is not a leak.**

### preferred_language (the README says the report is German only)
| Segment | n | Returned | Rate | Gap (pp) | Short |
|---|---|---|---|---|---|
| en | 344 | 11 | 3.2% | −2.0 | 7 |
| pl | 118 | 4 | 3.4% | −1.8 | 2 |
| ru | 170 | 6 | 3.5% | −1.7 | 3 |
| ar | 114 | 5 | 4.4% | −0.8 | 1 |
| tr | 308 | 14 | 4.5% | −0.7 | 2 |
| de | 4,719 | 247 | 5.2% | best | – |
| *(all non-de)* | 1,054 | 40 | 3.8% | −1.4 | 15 |

Report open rate: de 71.7%, non-de 37.3%.

### report_opened
| Segment | n | Returned | Rate | Gap (pp) | Short |
|---|---|---|---|---|---|
| false | 1,995 | 44 | 2.2% | −4.2 | 84 |
| true | 3,778 | 243 | 6.4% | best | – |

### marketing_consent
| Segment | n | Returned | Rate | Gap (pp) | Short |
|---|---|---|---|---|---|
| false | 2,611 | 96 | 3.7% | −2.4 | 62 |
| true | 3,162 | 191 | 6.0% | best | – |

### referral_booked (within result_category = referral_recommended, n = 564)
| Segment | n | Returned | Rate | Gap (pp) | Short |
|---|---|---|---|---|---|
| false | 277 | 10 | 3.6% | −1.3 | 4 |
| true | 287 | 14 | 4.9% | best | – |

### Two-way: preferred_language × report_opened
| Segment | n | Returned | Rate | Gap (pp) |
|---|---|---|---|---|
| de / not opened | 1,334 | 28 | 2.1% | −4.4 |
| non-de / not opened | 661 | 16 | 2.4% | −4.0 |
| non-de / opened | 393 | 24 | 6.1% | −0.4 |
| de / opened | 3,385 | 219 | 6.5% | best |

Once you hold `report_opened` fixed, the language gap almost disappears (0.4 pp among openers, and reversed among non-openers). Non-German customers return less mainly because fewer of them open the report.

### Two-way: result_category × optician_follow_up (the two largest-volume gaps)
| Segment | n | Returned | Rate | Gap (pp) | Short |
|---|---|---|---|---|---|
| referral_recommended / none | 312 | 8 | 2.6% | −15.8 | 49 |
| unremarkable / none | 2,182 | 69 | 3.2% | −15.2 | 332 |
| unremarkable / email | 1,322 | 48 | 3.6% | −14.7 | 195 |
| referral_recommended / email | 163 | 6 | 3.7% | −14.7 | 24 |
| unremarkable / phone | 491 | 23 | 4.7% | −13.7 | 67 |
| minor_findings / none | 698 | 55 | 7.9% | −10.5 | 73 |
| minor_findings / email | 369 | 41 | 11.1% | −7.3 | 27 |
| referral_recommended / phone | 89 | 10 | 11.2% | −7.1 | 6 *(small)* |
| minor_findings / phone | 147 | 27 | 18.4% | best | – |

Neither gap explains the other. The result gap holds at every follow-up level, and the follow-up gap holds within every result. The result gap also holds when report_opened is held fixed: openers are at 4.3% for unremarkable vs 13.9% for minor_findings, and non-openers at 2.0% vs 3.3%. It also holds within every age band.

## 4. Main leak

The largest gap that is big enough to matter is among customers with an **`unremarkable`** result. They make up 3,995 of the 5,773 eligible customers (69%) and return at 3.5%, against 10.1% for **`minor_findings`**, the comparator. That is a 6.6 pp gap, about 265 returns short, and it persists within every follow-up type, age band and report-opened group.
