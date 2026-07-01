# Domain Expertise - Logistics & Last-Mile Delivery

This file gives the content engine deep domain knowledge for writing authoritative articles. It covers terminology, competitive context, industry myths, regulations, and trusted sources.

---

## Industry Terminology

Use these terms correctly and consistently. Define them on first use in articles aimed at intermediate readers.

| Term | Definition | Usage notes |
|---|---|---|
| **Last mile** | The final leg of delivery from a distribution hub to the end customer's door | Most expensive segment: 53% of total shipping cost (Capgemini, 2024) |
| **Route density** | Number of delivery stops per square kilometer on a given route | Higher density = lower cost per delivery. Target: 8+ stops/km2 in urban areas |
| **Drop density** | Number of successful deliveries per route hour | Key efficiency metric. Industry average: 6-8 drops/hour; optimized fleets hit 10-14 |
| **Time windows** | Customer-specified delivery slots (e.g., 2pm-4pm) | Major constraint in optimization. Narrow windows reduce route flexibility by 30-40% |
| **Vehicle capacity utilization** | Percentage of vehicle load space or weight capacity used per route | Target: >85%. Below 70% signals route planning inefficiency |
| **Failed delivery rate** | Percentage of attempted deliveries where the customer is unavailable or refuses | Industry average: 6-8%. Each failed delivery costs $15-20 in reattempt costs |
| **Cost per delivery (CPD)** | Total route cost divided by successful deliveries | The single most important unit economic for delivery operations |
| **Driver utilization** | Percentage of paid driver hours spent actively delivering (vs. driving empty, waiting, loading) | Target: >75%. Manual planning typically yields 55-65% |
| **Dynamic re-optimization** | Adjusting routes in real-time based on cancellations, new orders, traffic, or breakdowns | Requires live data feeds and sub-minute computation |
| **Proof of delivery (POD)** | Digital confirmation that a delivery was completed (photo, signature, GPS timestamp) | Reduces disputes by 80%+ when implemented |
| **Delivery attempt rate** | Ratio of attempted deliveries to planned deliveries | Below 95% indicates driver skipping or poor address data |
| **Reverse logistics** | Handling returns and pickups alongside forward deliveries | Adds 15-25% complexity to route optimization |

## Competitive Context

### Direct competitors (route optimization)

| Competitor | Strengths | Weaknesses | Typical customer |
|---|---|---|---|
| **Routific** | Clean UI, easy setup, good for small fleets | Limited dynamic re-optimization, no EV support, weaker on time windows | Small fleets (10-50 vehicles), food delivery |
| **OptimoRoute** | Strong multi-day planning, good analytics | Slower optimization for large route sets, less flexible API | Mid-size fleets, field service |
| **Circuit** | Free tier, driver app, simple onboarding | Very basic optimization, no capacity constraints, no enterprise features | Solo drivers, micro-fleets (<15 vehicles) |
| **Google OR-Tools** | Free, open source, highly customizable | Requires engineering team to build and maintain, no UI, no support | Tech companies building in-house solutions |

### Indirect competitors

- **Manual planning (Excel/Google Maps):** Still used by 40-60% of fleets under 50 vehicles. Baseline that every article should reference.
- **TMS platforms (Descartes, Omnitracs):** Built for long-haul and enterprise. Overkill and overpriced for last-mile fleets under 500 vehicles.
- **Delivery management platforms (Onfleet, Bringg):** Include basic routing but optimization is not their core. Good for tracking, weak on route math.

## Industry Myths (address in articles when relevant)

1. **"Manual routing works fine for small fleets"** - Reality: Even at 30 vehicles, manual planners miss 15-25% of optimization opportunities. The savings compound: $2,000-4,000 per vehicle per year.

2. **"All route optimization software is basically the same"** - Reality: The difference between a basic solver and production-grade optimization is 10-15% in route efficiency. Constraints handling (time windows, vehicle types, driver skills) is where tools diverge.

3. **"GPS tracking = route optimization"** - Reality: GPS tracking tells you where vehicles are. Route optimization tells them where to go. Different problems, different tools. Many fleet managers conflate the two.

4. **"AI route optimization replaces dispatchers"** - Reality: It replaces the 2 hours dispatchers spend on spreadsheets, not the dispatchers. Exception handling, customer escalations, and driver management still require human judgment.

5. **"You need 500+ vehicles to justify optimization software"** - Reality: ROI typically turns positive at 15-20 vehicles. A 50-vehicle fleet saving $3,000 per vehicle per year generates $150,000 in annual savings against a software cost of $20,000-40,000.

## Regulations and Compliance

Articles should reference these where relevant. Always cite the specific regulation.

| Regulation | What it covers | Impact on route optimization |
|---|---|---|
| **EU Driving Time Regulation (EC 561/2006)** | Max 9 hours driving/day (extendable to 10 twice per week), 45-min break after 4.5 hours | Routes must factor in mandatory breaks; optimization algorithms need driver hours as a constraint |
| **Low Emission Zones (LEZ)** | Restricted urban areas where high-emission vehicles are banned or charged | Route optimization must consider vehicle emission class and zone boundaries; favors EV-capable tools |
| **GDPR (EU 2016/679)** | Personal data protection including driver GPS tracking and customer addresses | Route data must be processed lawfully; customer delivery addresses are PII |
| **UK Clean Air Zones** | Similar to EU LEZ but UK-specific post-Brexit | Separate zone data required for UK operations |
| **Working Time Directive (2003/88/EC)** | Maximum 48 hours average work week, rest period requirements | Affects multi-shift and weekend delivery scheduling |

## Authority Sources

Cite these in articles to build EEAT credibility. Always include the year.

### Industry reports
- **Capgemini Research Institute** - "The Last-Mile Delivery Challenge" (2024): 53% of total shipping cost is last mile
- **McKinsey & Company** - "The Future of Last-Mile Delivery" (2023): Autonomous and drone delivery projections, cost benchmarks
- **Statista** - Last-mile delivery market size and growth data (updated annually)
- **Pitney Bowes Parcel Shipping Index** - Global parcel volume trends (annual)

### Industry organizations
- **European Logistics Association (ELA)** - Standards and best practices
- **Chartered Institute of Logistics and Transport (CILT)** - Professional body, UK/EU focus
- **Council of Supply Chain Management Professionals (CSCMP)** - US-focused but globally relevant benchmarks

### Data points to cite regularly
- Last-mile delivery accounts for 53% of total shipping costs (Capgemini, 2024)
- Global parcel volume exceeded 200 billion in 2025 (Pitney Bowes, 2025)
- Failed deliveries cost the industry $1.6 billion annually in Europe alone (IMRG, 2024)
- Average consumer expects delivery within 2 days; 30% expect same-day (McKinsey, 2023)
- Electric delivery vehicle adoption growing 35% year-over-year in EU urban areas (ELA, 2025)
