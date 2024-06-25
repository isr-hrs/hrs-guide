<!-- Chapter 2 Survey Design  -->


# <span style="color: #1c6c8c; font-family: cambria">Chapter 2. Survey Design</span>

### <span style="color: #147ca4; font-family: cambria">HRS MULTISTAGE COMPLEX DESIGN</span>

To draw a nationally representative sample of the US population over age 50, HRS employs a
complex sample design with two main design features: stratification and clustering. Figure 2
depicts a basic multistage design.


### <span style="color: red; font-family: cambria"> Insert figure 2 here</span>


Figure 2. Generic multistage complex sample design [statement of permission]

In a national sample, the process involves multiple steps: initially, large areas called primary sampling units (PSUs), typically counties, are selected. Then, within these PSUs, smaller areas like cities or towns called secondary sampling units (SSUs) are chosen (strata). Next, specific sections of homes (clusters) are picked, and finally, individuals within those homes are selected for interviews.

The HRS sample is based on a multi-stage, area-clustered, stratified sample design. It consistently separates large primary sampling units (PSUs), like major cities, which are always included, from smaller PSUs, chosen based on their population size. This ensures that denser areas are more likely to be selected. PSUs are typically big cities or combined counties.

This sample design includes a deliberate oversampling of Hispanic and African American households. This method increases their numbers in the HRS to allow for more accurate analysis and comparisons within these racial/ethnic groups.

The HRS focuses on the U.S. population over 50 who do not live in institutions. People in the study who move into nursing homes after joining are still interviewed every two years, making the sample representative of older adults both at home and in nursing facilities post-enrollment.

The HRS sample design results in varied selection chances for participants, so using sampling weights is crucial to avoid bias when making generalizations about the U.S. population. Standard methods for estimating variance don't work well due to the sample's specific geographic organization, and corrections using design variables are necessary. [Chapter 8] gives instructions on how to properly use these weights and design variables in analysis.

A video tutorial is available that reviews these concepts in detail.

VISIT THE WEBSITE: Documentation>Tutorials

Sonnega A. HRS sample Design, Weighting, and Complex Variance Estimation; 2022. 

More information about the sampling design and the development of weights for 2016 and beyond is available on the website. 

VISIT THE WEBSITE: Documentation>Survey Design and Methodology

Lee S, Nishimura R, Burton P, McCammon RJ. HRS 2016 Sampling Weights. Ann Arbor, MI: Survey Research Center, Institute for Social Research, University of Michigan; 2021.

Heeringa SG, Connor J. Technical Description of the Health and Retirement Study Sample Design. Ann Arbor, Michigan: Institute for Social Research, University of Michigan; 1995.

Heeringa SG. Technical Description of the Asset and Health Dynamics Among the Oldest Old (AHEAD) Study Sample Design. Ann Arbor, Michigan: Institute for Social Research, University of Michigan; 1995.

### <span style="color: #147ca4; font-family: cambria">Creating a Longitudinal Cohort</span>

As shown in Figure 3, the HRS gradually added participants over time. The 1992 cohort included people born between 1931 and 1941 and their spouses, who have been interviewed every two years since. In 1993, the study expanded to include the Assets and Health Dynamics of the Oldest Old (AHEAD) cohort, for individuals born in 1924 or earlier, who were at least 70 at that time. 

Over time, the HRS expanded by merging existing cohorts and adding new ones to fill age gaps for those over 51 in the U.S. In 1998, it merged the initial cohorts and added the Children of the Depression (CODA, born 1924-1930) and War Babies (born 1942-1947) groups. HRS now regularly adds younger groups: Early baby boomers (born 1948-1953) in 2004, Mid baby boomers (born 1954-1959) in 2010, Late baby boomers (born 1960-1965) in 2016, and the first part of Generation X (eGenx, born 1966-1971) in 2022.

For all cohorts, both members of a couple are included in the sample. And remember, while the sampled respondent is in the eligible age range, the spouse or partner can be of any age. Age-ineligible spouse/partners will have a zero weight in any wave that their birth cohort is not represented, but note that many younger spouses or partners will age into study age-eligibility in a later wave and will then be assigned a positive weight.



### <span style="color: red; font-family: cambria"> Insert figure 3 here</span>
Figure 3. HRS longitudinal cohort sample design


### <span style="color: #147ca4; font-family: cambria">Who is Interviewed?</span>

As previously described, the HRS samples households initially. Initial recruitment into the study is at the door step of a home. The interviewer checks if there is anyone living in the household of an eligible age to participate in the study. The questions first confirm that the person answering is a household member, meaning they live there, eat, and sleep there. Then, they are asked to count how many people in the household are in three different age groups: 18-44, 45-59, and 60 or older. 

When a household has at least one person aged 45 or older, the interviewer collects more information about everyone aged 18 and above living there. This includes their name, birth year or age, ethnicity, race, and whether they are in a couple. The survey then chooses up to two qualified individuals for an in-depth interview. If a couple is living in the household and at least one partner is cohort-eligible, both partners are selected for the interview. During these interviews, the chosen participants may talk about their parents, children, and others who assist them, but only the selected individuals, not their relatives or helpers, are interviewed. Both members of a couple are considered respondents in the HRS.

Of course, household composition can change over time as people are, for example, widowed, divorced, and remarried. HRS tracks all of these changes, and seeks to enroll any new partners. [Chapter 7. Data Structure and Management] provides the information you need to track changes in households over time if that is of interest for your research.


### <span style="color: #147ca4; font-family: cambria">Family Respondent and Financial Respondent</span>

In the HRS, participants answer questions about themselves as well as about their households. In coupled households, questions related to family details or financial matters like income and wealth, are directed to only one member of a couple. The person who answers family-related questions during a survey wave is labeled the Family Respondent (or Family R), and the one who answers financial questions is called the Financial Respondent (or Financial R). These roles are identified by special wave-specific markers xFAMR and xFINR found in the study's Tracker file. If the selected person living in the household is single, that individual is both the Family R and the Financial R.


### <span style="color: #147ca4; font-family: cambria">Interview Modes and design features</span>

The biennial waves of data collection shown in Figure 3 are referred to in HRS as the core interview. Since the first wave in 1992, baseline core interviews have been conducted face-to-face in respondents’ homes. Through 2002, panel (follow-up) interviews were typically conducted by telephone unless the participant is over age 80, in which case panel interviews could also be face-to-face.  


### <span style="color: #147ca4; font-family: cambria">Enhanced Face-to-Face Interview</span>

From 2006 onwards, HRS has used a strategy that combines both in-person and telephone interviews. Participants are randomly divided into two groups: one group receives a detailed in-person interview which includes health assessments and a special survey about mental and emotional health (this is called the enhanced face-to-face or EFTF interview). The other group is interviewed over the phone and answers just the standard set of questions asked every two years. Each participant's type of interview—whether in-person or by phone—switches with every new survey wave

Figure 4 shows how the enhanced in-person interview plan works. There are two groups, "A" and "B". Group "A" had their in-depth face-to-face interview in 2006, while Group "B" did not. In 2008, Group "B" had their turn for the in-depth interview, and Group "A" did not. After that, each group takes turns for the enhanced interview with every new survey wave: Group "A" in 2010, Group "B" in 2012, and so on, alternating each time.

This means that while core survey data are available every wave on the full sample, the physical, biomarker, and psychosocial measures are available every wave on only half of the full core sample – either A or B – and every four years for all A and B respondents. The enhanced interview can take place at the baseline interview or at follow-up.


### <span style="color: red; font-family: cambria"> Insert figure 4 here</span>
Figure 4. Design of the enhanced face-to-face interview

The variable EFTFASSIGN can be found in the Tracker file. It is a flag for which sample a given respondent is in, A or B. 

VISIT THE WEBSITE: Data Products>Downloads>Public Survey Data/Cross-Wave Tracker File



### <span style="color: #147ca4; font-family: cambria">Web Mode</span>

Starting in 2018, HRS gave some households the option to complete their main survey online. These households were chosen based on whether all the members said they use the internet regularly during the previous survey. However, households scheduled for the in-depth face-to-face interviews during a particular survey cycle were not given the web option. To understand how offering surveys online affects participation rates, data quality, and the answers provided, about 40% of the households that could do the survey online continue to do it in the usual way (by phone or in-person) as a comparison group. In the survey materials, any instructions that are only for the web interviews are highlighted in teal.

The Tracker file has two flag variables that help identify web cases and controls: IWMODE and WEBCONTROL. In addition, starting in 2018, there are mode indicators in each of the HRS core section data files.

VISIT THE WEBSITE: Data Products>Downloads>Public Survey Data/Cross-Wave Tracker File



### <span style="color: #147ca4; font-family: cambria">Proxy Respondents</span>

Another important design feature of the HRS is the use of proxy respondents. Respondents who are unwilling or unable to do an interview themselves are offered the opportunity to use a proxy, who is usually a spouse or other family member. A research paper by [Weir, Faul, and Langa] available in the bibliography provides more information on this topic.


Weir DR, Faul JD, Langa KM. Proxy interviews and bias in the distribution of cognitive abilities due to non-response in longitudinal studies: a comparison of HRS and ELSA. Longitudinal and Life Course Studies. 2011;2(2):170-184. 

The process of proxy selection is documented on the study website.

VISIT THE WEBSITE: Documentation>Survey Design and Methodology 

Scroll down to the section on Survey Design:

HRS Staff. Proxy Selection in the HRS

Tracker file provides a flag variable called PROXY with detail on the circumstances of the proxy interview.

VISIT THE WEBSITE: Data Products>Downloads>Public Survey Data/Cross-Wave Tracker File


### <span style="color: #147ca4; font-family: cambria">Follow-up to Nursing Homes</span>

Although the baseline core interviews are conducted with community-dwelling persons only, respondents who move to nursing homes and other senior living facilities after the baseline wave are retained and interviewed there in subsequent waves. Thus, although the study does not sample nursing home residents, over time the sample has come to represent the population residing in nursing homes in the US.

An indicator variable called NURSHM is available in Tracker that provides detail on the circumstances of the nursing home interview. A nursing home weight is also available beginning in 2000.

VISIT THE WEBSITE: Data Products>Downloads>Public Survey Data/Cross-Wave Tracker File



[//]: # (links within document)
[Chapter 8]: <../chapter-8/hrs8.md>
[Chapter 7 on Data Structure and Management]: <../chapter-7/hrs7.md>

[//]: # (links to the website)
[RAND Longitudinal File]: <https://hrs.isr.umich.edu/>
[Weir, Faul, and Langa]: <https://hrs.isr.umich.edu/>
