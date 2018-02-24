---
layout: post
title: ASA Conference on Statistical Practice 2018, Friday 5 of 6, Posters I Wish I'd Seen
category: [R, ASA, CSP2018]
tags: [R, ASA, CSP2018]
---

![steps](/images/stepcounts01.png "Step Counts in Wearable Activity Tracker Study")

Highlights from [Conference on Statistical Practice](https://ww2.amstat.org/meetings/csp/2018/index.cfm). 

**Friday 2/16/2018**
* [8:00 AM Keynote Address & 9:15 AM Working with Messy Data](https://dgarmat.github.io/CSP2018-Fri-8am/)
* [11:00 AM Streamlining Your Work Using (Shiny) Apps](https://dgarmat.github.io/CSP2018-Fri-11am/)
* [2:00 PM Data Mining Algorithms / Presenting and Storytelling](https://dgarmat.github.io/CSP2018-Fri-2pm/)
* [3:45 PM Working with Health Care Data](https://dgarmat.github.io/CSP2018-Fri-345pm/)
* **Posters I Wish I'd Seen**
* [Additional Sessions I Wish I'd Attended](https://dgarmat.github.io/CSP2018-Fri-Additional/)

**Saturday 2/17/2018**
* [9:15 AM Poster Session 3 / Survival Analysis v. 'Survival' Analysis](https://dgarmat.github.io/CSP2018-Sat-915am/)
* [11:00 AM Causal Inference](https://dgarmat.github.io/CSP2018-Sat-11am/)
* [2:00 PM Deploying Quantitative Models as 'Visuals' in Popular Data Visualization Platforms](https://dgarmat.github.io/CSP2018-Sat-2pm/)
* [Additional Sessions I Wish I'd Attended](https://dgarmat.github.io/CSP2018-Sat-Additional/)


## 5:00 PM Poster Sessions

### 	Curating and Visualizing Big Data from Wearable Activity Trackers *Meike Niederhausen, OHSU-PSU School of Public Health*

Problem: data from a wrist health device tracker study involving 500 people is messy. How can visualization help separate useful data  from not useful data?

They had to throw out the first week ([Hawthorne Effect](https://en.wikipedia.org/wiki/Hawthorne_effect)) and implausible values such as 10000 steps in one minute (manual entry?). They also had to limit to people who had enough activity and didn't just take the watch off for days and days. Can see examples of kinds of data errors and variation by day by activity level of participant in above scatterplot.

Interestingly they appear here to have found a three-way interaction term of predictive worth. We learn to generally avoid three way interaction terms as they're hard to make sense of both conceptually and theoretically. This demonstrates one way to approach trying to visualize such an interaction term to get at the former. The slopes by BMI group across gender really are quite similar, though, so I wonder if this implies a two way interaction is sufficient? In this case it would be BMI group by age regressed on average steps per day. Gender doesn't look significant in terms of slope.

![age vs. gender vs. BMI group](/images/threewayint01.png "Age vs. Gender vs. BMI Group")

I liked these plots showing the correlation of different activity levels with health outcomes. Maybe useful for exercise motivation? Not sure exactly who the study can be inferred to, especially after the data cleaning, but suggestive of reasonable hypotheses. I'm not sure about the multiple hypothesis testing if they did any correction, and if the p-values could be taken on face value given the data cleaning choices, but it offers an awesome glimpse into this, [as I've seen first hand, difficult, highly personal data](https://dgarmat.github.io/Calories-vs-Sleep/). One thing I notice is in each column the slope has the same sign - this makes sense as for each variable on the y-axis, lower is associated with better health outcomes. 

![corrplots01](/images/corrplots01.png "can see the red low p-value ones")

It's interesting to see, on the other hand, how little linear correlation there was with clinical values like blood pressure. I'm surprised to see Diastolic blood pressure goes up with age of these participants, but not Systolic blood pressure. There's really nothing much going on besides age here. One wouldn't expect numbers like HbA1c, a long-term measure of diabetes, to be affected much by this study over a few weeks, so would expect correlations to have more to do with pre-existing habits, and so it's surprising there isn't more going on in this population. Wonder if this sample does represent typical adults. It's weird too because one would expect the numbers in the other charts like BMI to correlate with HbA1c, but I think this implies in these data, it doesn't. Shows just how challenging research with health tracker data can be.

![corrplots02.png](/images/corrplots02.png "again, fewer low p-value ones")

### 	The Boeing Applied Statistics ToolKit: Best Practices and Tools for Collaboration and Reproducibility in High-Throughput Consulting *Robert Michael Lawton, Boeing Research & Technology*

Problem: In fast-paced statistical consulting, balancing quality, reproducibility, and urgency is challenging.

Boeing Research and Technology’s Applied Math Group of 50 mathematicians developed an applied statistics toolkit to help solve this problem. It has: 
* Set of analysis libraries (reusable R code, vignettes, and help)
* Collaboration best practices (R Studio, Git)
* Knowledge management system 
* Program for vetting new statistical capabilities

Unfortunately their presentation live had a lot more interactive detail than as posted as a static .pptx file, but appreciate the careful, thoughtful planning they shared to handle an all-too-familiar challenge of "technical debt" in industry. 

![Boeing toolkit](/images/boeingtoolkit.png "Boeing In-House Statistical Consulting Toolkit")


### 	Estimating the Relative Excess Risk Due to Interaction in Clustered Data Settings *Katharine Correia, Harvard T.H. Chan School of Public Health*

Problem: interaction terms for relative risk coefficients can be difficult to estimate with frequentist methods. Can a Bayesian approach help?

In simulated clusters, often frequenstist approaches to handle interactions did not converge, especially log binomial random intercepts models (FLB bars here) and were especially poor with higher standard devisions of random intercepts (SD here)

![interactions](/images/simcluster01.png "Interaction Terms")

She was able to apply [rstan package](https://cran.r-project.org/web/packages/rstan/index.html) in a Bayesian approach and find a small but significant interaction in absolute risk between age and BMI in terms of live birth from in vitro fertilization. (Risk of success?) In another case, she detected a more dramatic 25% increase in risk of preterm delivery from interaction between nevirapine exposure at conception and poor immunological health. 

This kind of analysis could be important for precision medicine, where we want to start grouping patients into smaller buckets and asses how they will react to different treatments.

### Exploratory Analyses from Different Forms of Interactive Visualizations *[Lata Kodali](http://www.lisa.stat.vt.edu/?q=node/10238), Virginia Tech*

These posters are often interactive when seen in person. Nothing posted yet.

### Using SAS Programming to Create Complex Paneled Graphs from Electronic Health Records *Carrie Tillotson, OCHIN, Inc.*

Problem: a new electronic tool is being implemented - can the changes in key variables before and after be measured and displayed in a visually meaningful way?

They implemented an insurance tool in their electronic health records and tracked changes in an important response over time (maybe count of Medicare billings?) at different facilities. They were able to show these plots to staff at the facilities to give insight how practices had or had not changed since tool implementation.

![SAS plot 01](/images/sas01.png "SAS Plot 01")

###  An Algorithm to Identify Family Linkages Using Electronic Health Record Data *Megan Hoopes, OCHIN, Inc.*

Problem: Health factors highly correlate among family members but explicit family links are often missing from medical records. Is there a reproducible way to impute links between family members in EHRs?

Their strategy to find family links included identifying key fields such as address, home phone, insurance carrier, and fuzzy matching on mother emergency contact phone number, and cases to exclude such as when it looks like there are two adult females in the household so the biological mother is less clear. and then compare this to a "gold standard" data set. In the end, in a pediatric dataset they linked 382,000 mother-child relationships, of which only 44% were explicitly stated in the EHR.

Some caveats: has high precision but low sensitivity - that is the matches it makes tend to be true, but the number of matches caught is low. Also, this method really is limited to household units not genetic relationships.

This plot shows accuracy of linkage is higher with younger children, and children who go to the doctor more often (younger children go to the doctor more so same or different people?)

![household linkages](/images/householdlink01.png "accuracy of linkages")





up next: [Additional Sessions I Wish I'd Attended](https://dgarmat.github.io/CSP2018-Fri-Additional/)
