## HealthConnect Experience Lab Week 6: Advanced Analytics & Decision Support Report

## Introduction

This report builds on the Week 5 foundation, where data cleaning, exploratory data analysis (EDA), KPI development, and an initial dashboard were completed across the HealthConnect Experience Lab dataset (5,000 appointment records). Rather than repeating that work, Week 6 focuses on deepening and validating the most business-relevant findings from Week 5, investigating relationships between key variables and appointment outcomes, and translating those findings into actionable recommendations for HealthConnect management.


## Summary of Week 5 Findings

Total Appointments: 5,000
Attendance Rate: 46.28%
Cancellation Rate: 5.26%
No-Show Rate: 48.46%
Average Booking Lead Time: 29.64 days
Average Distance to Clinic: 10.08 km
Attendance varies modestly by appointment type, with Follow-up appointments showing the lowest attendance rate and highest no-show rate.
Attendance appears broadly similar across gender groups.
Reminder channel and whether a reminder was sent both showed a visible relationship with attendance.


## Selected Findings for Deeper Investigation

Three findings were selected for deeper investigation based on their potential business impact and actionability:
Booking lead time and its relationship with appointment outcome,
Distance to clinic and its relationship with appointment outcome,
Patient appointment history (previous appointments and previous no-shows) and its relationship with appointment outcome.
These were prioritized because, unlike demographic factors (gender, age), they represent operational levers HealthConnect can realistically act on — through scheduling policy, patient support, and risk-based reminder targeting.


## Deeper Analysis

1. Booking Lead Time vs. Appointment Outcome
The Booking_Lead_Days (bins) by Appointment_Outcome chart shows a clear pattern: at low lead-time bins (booked close to the appointment date), attendance is high and no-shows are comparatively low (534 attended vs. 237 no-show at the shortest lead time bin). However, as booking lead time increases, the relationship reverses — at higher lead-time bins, no-shows overtake attendance (e.g. 203 attended vs. 509 no-show; 264 attended vs. a much larger no-show count at the highest bins shown). This indicates that appointments booked far in advance are considerably more likely to end in a no-show than appointments booked close to the visit date. This suggests that patients who book long in advance may forget, deprioritize, or have circumstances change before the appointment date arrives.


 






2. Distance to Clinic vs. Appointment Outcome
The Distance_To_Clinic by Appointment_Outcome chart shows that attendance and no-shows are both concentrated in the 0–15 km range, where the bulk of appointments occur (e.g. 850 attended vs. 838 no-show in the 10km bin). Beyond roughly 20 km, appointment volume drops sharply for all outcomes, but no-shows consistently continue to outnumber or closely track attendance in the remaining bins (e.g. 95 attended vs. 124 no-show at 20km; 34 attended vs. 53 no-show beyond that). This reveals that while most patients live close to the clinic, the pattern across distance bins shows no-shows becoming proportionally more common relative to attendance as distance increases, even though total volume shrinks. This indicates distance is a contributing factor to missed appointments, though not the dominant one given how concentrated the data is near the clinic.



 




3. Patient History (Previous Appointments and Previous No-Shows) vs. Appointment Outcome
Two additional relationships were investigated beyond the original seven business questions, as they emerged as strong patterns worth validating:
Previous Appointments: Patients with 0 previous appointments show a near-even split between attendance (1,910) and no-shows (1,942), while patients with more previous appointment history (4–6 range) show a similar proportional pattern (403 attended vs. 479 no-show), suggesting prior visit history alone does not strongly predict future attendance.
Previous No-Shows: Patients with 0 previous no-shows still show a near-even attendance/no-show split (2.1K attended vs. 2.1K no-show), while the small number of patients with 1+ previous no-shows show a no-show-leaning pattern (0.2K attended vs. 0.3K no-show), though the sample size in this group is much smaller. This indicate that these two variables show weaker, less conclusive patterns compared to booking lead time and distance. Previous no-show history shows a mild tendency toward repeat no-shows, but the sample size for patients with prior no-shows is small relative to the overall dataset, so this finding should be treated as preliminary rather than conclusive.




 



Reminder Channel Vs Appointment Outcome
The first visual show equal count of attendance and no-shows however, there was recorded number of no-shows when reminders were not sent. SMS shows the highest number of attendance which was closely followed by Email. The highest no-show rate was observed when no reminder was sent. (51.39%) and followed by Whatsapp(49.77%). This indicates that SMS yielded the highest attendance. This is probably because it can be received with data internet service unlike Email or Whatsapp.

 
## KPI Validation
The core KPIs (Total Appointments, Attendance Rate, Cancellation Rate, No-Show Rate, Average Booking Lead Time, Average Distance to Clinic) were reviewed against the underlying fact table and confirmed to be calculating correctly, using DIVIDE-based DAX measures with appropriate handling of the Appointment_Outcome categories. The KPIs remain meaningful indicators of overall dashboard health.



## Business Impact Ranking
Based on the depth and actionability of the findings above, the factors most strongly associated with no-shows and cancellations, ranked by business impact are:

Booking lead time which shows the clearest and most actionable pattern; directly informs scheduling and reminder policy.

Distance to clinic: a real but moderate factor; supports the case for transport support.

Previous no-show history: this is a weaker, preliminary signal; worth monitoring but not yet strong enough to act on decisively.

Reminder channel / reminder sent: while not one of the original seven questions, this showed a consistent relationship with attendance and should be considered a quick-win lever.



## Recommendations
Based on the findings above, the following recommendations are proposed to HealthConnect management:

Introduce targeted reminders for long-lead-time bookings. Since attendance drops as booking lead time increases, patients who book far in advance should receive additional reminder touch points (e.g. a reminder shortly after booking, in addition to the standard pre-appointment reminder).

Consider a maximum recommended booking window where feasible, to reduce the proportion of appointments booked far in advance and therefore at higher no-show risk.

Offer transport support options for patients living further from the clinic particularly beyond the 15–20 km range, where no-shows proportionally increase.

Prioritize SMS reminders over other channels or no reminder at all, given SMS showed the highest associated attendance rate among reminder channels tested.

Continue monitoring previous no-show history as a potential early-warning signal, but treat it as a secondary factor until more data is available to confirm the pattern.

Cross-Track Contribution (Data Science Track)
The findings on booking lead time, distance to clinic, and previous no-show history could serve as useful predictive features for a no-show/cancellation risk model. In particular, booking lead time showed the strongest and most consistent relationship with appointment outcome and is recommended as a priority feature for any future predictive modelling work on this dataset.


## Data Limitations
The dataset is synthetic, so patterns identified may not fully reflect real-world patient behavior. 

The dataset does not include reasons for cancellation or no-show, limiting the ability to explain why the observed patterns occur.

Sample sizes become small at the extremes of some variables (e.g. very long distances, multiple previous no-shows), reducing confidence in those specific findings.

No patient satisfaction or qualitative feedback data was available to contextualize the quantitative patterns found.


## Conclusion
This Week 6 analysis deepened three key findings from the Week 5 dashboard: booking lead time, distance to clinic, and patient appointment history and validated that booking lead time is the strongest, most actionable driver of no-shows and cancellations in the dataset. These findings support concrete recommendations around reminder targeting, scheduling policy, and patient support for distant patients, while also flagging useful features for future predictive modelling work.

