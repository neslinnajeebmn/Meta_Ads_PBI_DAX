# 📊 Meta Ads Campaign Performance Analysis with Power BI

This repository contains DAX measures used in my Power BI project to evaluate the performance of Meta (Facebook/Instagram) advertising campaigns. The goal is to classify campaigns based on five key performance metrics and draw actionable insights using industry-standard benchmarks.

---

## 🎯 Project Objective

To build a **data-driven campaign evaluation framework** for Meta Ads using Power BI, enabling marketers to:

- Benchmark campaign performance
- Identify underperforming campaigns
- Focus on metrics that matter for optimization

---

## 📐 Metrics and Benchmarks

| Metric                 | Benchmark       | Interpretation                     |
|------------------------|------------------|--------------------------------------|
| ROAS                  | ≥ 4              | Profitable return on ad spend       |
| CTR (%)               | ≥ 2.5%           | Healthy engagement rate             |
| Conversion Rate (%)   | ≥ 3%             | Effective conversion from clicks    |
| CPC (USD)             | ≤ $1.50          | Cost-efficient traffic              |
| Cost per Result (USD) | ≤ $10.00         | Acceptable cost per acquisition     |

---

## 🧮 Main DAX Measure – Campaign Verdict

The `CampaignVerdict` measure classifies each campaign as:

- **Best Performance**: Meets at least 4 out of 5 benchmarks
- **Poor Performance**: Fails in 3 or more metrics
- **Mixed Performance**: Falls between the two

```dax
CampaignVerdict = 
SWITCH(TRUE(),
    (
        ([ROAS] < 4) + 
        ([CTR (%)] < 2.5) + 
        ([Conversion Rate (%)] < 3) + 
        ([CPC (USD)] > 1.5) + 
        ([Cost per Result (USD)] > 10)
    ) >= 3, "Poor Performance",

    (
        ([ROAS] >= 4) + 
        ([CTR (%)] >= 2.5) + 
        ([Conversion Rate (%)] >= 3) + 
        ([CPC (USD)] <= 1.5) + 
        ([Cost per Result (USD)] <= 10)
    ) >= 4, "Best Performance",

    "Mixed Performance"
)
💡 Additional DAX Measures Included
ROAS Calculation

CTR (%)

Conversion Rate (%)

CPC

Cost per Result

Campaign Classification KPIs (Best, Mixed, Poor)

PerformanceIssue Comments (for tooltips)

🧠 Learn More
This project is part of my personal portfolio showcasing my skills in Power BI, marketing data analysis, and DAX logic.

🙋‍♀️ About Me
I'm Neslin, a Digital Marketing Analyst in progress—combining performance marketing expertise with data storytelling. Let's connect!

https://neslindigital.wixsite.com/my-site | https://www.linkedin.com/in/neslinnajeeb/
