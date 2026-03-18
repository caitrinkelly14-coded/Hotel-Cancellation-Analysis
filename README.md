# How hotel can begin to trust reservations again.

**One-line hook:** Start counting on your guests to follow through, as long as it the real guest making the reservation

---

## The Business Problem

A hotel chain in Portugal is struggling to understand why they have so many cancellations. Even with long term 
and non refundable booking they are still seeing many last minute cancellations. This is results in the hotel losing millions 
due to the lost opportunity to book reliable guests.


## The Data

We are working with a comprehensive dataset of 119,390 hotel booking records across 32 distinct features. Our baseline cancellation 
rate is 37%, giving us a solid, moderately balanced target for our predictive model. Overall data quality is high, though we need to 
address significant missing data in the 'company' and 'agent' fields (missing 94% and 13% of records, respectively) and investigate 
a few potential outliers in room rates and party sizes before proceeding.

<!--
Tip: Translate technical details into human terms.
Instead of "The dataset has 32 features and 119,390 rows..."
Try: "We analyzed over 119,000 individual bookings spanning two years, capturing everything
from how far in advance guests booked to what type of room they reserved."
-->

## Key Discoveries

- ** Time is is enemy of commitment :** [The further in advance a booking is made, the higher risk it has of being canceled. From this, 
hotels should expect that bookings made far in advance will not be as reliable as those made last minute. This should be shown by having 
a caoutious attitude of bookings in advance (expecting a portion to get canceled) an a higher expectation of relying on last minute 
bookings to follow through.
- **Financial Skin in the Game:** The hotel must investigate which specific market segments are being offered these non-refundable rates. 
If third-party distributors are routinely locking up inventory with non-refundable deposits and then canceling, the hotel is likely 
turning away direct, paying customers in the meantime. We should tighten the contracting terms with these specific distributors to require 
higher upfront payments or stricter cancellation windows.
- **Markets responsible for highest amount of cancellations:** The above chart fills in the gap on our finding from the previous chart, 
outling cancellations rates by market type, and confirmed our hypthosis of why non refundable reservations are not being upheld. The large 
60% "groups" category confirms what we predicted: the third party tour operators are reserving blocks and cancelling last minute, 
accounting for a large amount of the non refundable cancellations. This results in a dangerous inventory displacement for the hotel. Moving 
forward, leadership must fundamentally restructure group contracting to enforce strict "attrition clauses" (financial penalties for 
dropping blocks of rooms late in the game) and cap the percentage of inventory allocated to Groups during peak seasons.

<!--
Tip: Write findings as "headlines" a newspaper editor would approve.
Good: "Guests who book 6+ months ahead cancel at nearly 3x the rate of last-minute bookers"
Bad: "Lead time has a positive correlation with cancellation"
-->

## Visualizing the Story

<!-- Embed your most compelling chart. Pick the ONE visual that best captures your main finding. -->

!With the data anomalies removed, the true baseline of our customer behavior is exposed. The "Groups" segment emerges as the undisputed 
highest-risk channel, canceling over 60% of the time. Travel Agents (both Online and Offline) also show significant volatility, canceling 
roughly 35% of their bookings. In stark contrast, "Direct" bookings and "Corporate" accounts are highly reliable, with cancellation rates 
sitting safely under 20%. <img width="1189" height="590" alt="Cancellation_by_Market" src="https://github.com/user-attachments/assets/cf6544b1-bae6-4b6f-9fd8-dd193e005c4a" />


*By allowing high-risk "Groups" to hold our rooms hostage during peak booking windows, we are actively turning away the reliable "Direct" 
retail customers who actually show up and pay.*

## Prediction Model

Our Naive Bayes model achieves an overall accuracy of roughly 71%, but the confusion matrix shows the true operational trade-offs of these 
predictions. The model produces 5,210 false negatives, meaning thousands of actual cancellations will slip through undetected, resulting in 
"spoiled" (empty) inventory and lost revenue. Conversely, the model generates 1,763 false positives, incorrectly flagging reliable guests 
as flight risks. For a hotel, this false alarm is arguably the more dangerous error; if revenue managers trust the model and aggressively 
resell those 1,763 rooms, they risk overbooking and having to "walk" confirmed guests to another property, which incurs immediate financial 
penalties and severely damages brand reputation. Ultimately, however, the model successfully identifies 3,706 true cancellations in 
advance, giving the commercial team a highly targeted list of risky bookings to proactively manage, potentially recovering thousands of 
dollars in revenue that would have otherwise been lost.

<!--
Tip: Translate model metrics into business impact.
Instead of "The model achieved 78% accuracy..."
Try: "Our model correctly flags 8 out of 10 at-risk bookings, giving the hotel front desk team
enough lead time to proactively reach out and offer flexible rebooking options."
-->

## Recommendations

1. **Overhaul Contracting for the "Groups" Segment. :** Implement strict, tiered "attrition clauses" (financial penalties) and rolling 
non-refundable deposit milestones for all wholesale and event group contracts.ur discovery phase proved that the "Groups" segment is the 
primary driver of inventory displacement, carrying a massive 60%+ cancellation rate. Furthermore, the data showed that blocks categorized 
under "Non Refundable" deposits are effectively failing at a near-100% rate. By forcing third-party organizers to pay heavy penalties for 
dropping blocks of rooms late in the game, the hotel will immediately reduce inventory spoilage, potentially recovering tens of thousands 
of dollars per quarter in rooms that can be resold to reliable retail guests.
2. **Shift Marketing Spend to Direct and Corporate Channels.:** Cap the total percentage of hotel inventory allocated to wholesale/group 
channels during peak seasons and redirect marketing budget to heavily incentivize "Direct" and "Corporate" bookings. Our market segment 
analysis clearly demonstrated that Direct and Corporate bookings are incredibly stable, boasting cancellation rates safely under 20%. 
Shifting our overall channel mix by even 10-15% toward these reliable segments will drastically stabilize revenue forecasting, increase 
the average daily rate (ADR), and reduce the operational chaos caused by last-minute group drops.
3. **Revise the Overbooking Strategy Based on Lead Time:** Yield managers should confidently overbook the hotel for reservations made 
more than 3-4 months in advance, but rapidly tighten inventory controls once the 45-day window hits.The data clearly shows that time 
is the enemy of commitment; the median lead time for a canceled booking is over 100 days, compared to roughly 45 days for a fulfilled 
stay. Optimizing the overbooking curve based on lead time maximizes occupancy when the risk of cancellation is highest, while safely 
protecting the hotel from the severe financial penalties and reputation damage of having to "walk" a confirmed guest at the last minute.

## Tools & Techniques

Python | Pandas | Scikit-Learn | Matplotlib | Seaborn | Gaussian Naive Bayes | Google Colab

---

*This project was completed as part of ISOM 835: Predictive Analytics at Suffolk University\'s
Sawyer Business School.*
'''

