<!-- Chapter 7 Data Structure and Management -->


# <span style="color: #1c6c8c; font-family: cambria"> Chapter 7. Data Structure and Management </span>


Although we recommend beginning with the RAND Longitudinal File, we are going to begin this Chapter by describing the HRS original data structure and various merges that new users are likely to need to be able to do. We then describe the RAND files, which implement some of these merges. For both the HRS original data and the RAND HRS data, we provide important information that will help you begin using the data and merging data to create data extracts for your specific data analyses. We end this chapter with two ways that researchers sometimes need to restructure the data for specific analyses: stacking data from two adjacent waves and converting from “wide” to “long.”

### <span style="color: #147ca4; font-family: cambria"> Why do I need both HRS original data files and RAND HRS data products? </span>

It is important to remember that the RAND Longitudinal file does not include all of the biennial core data, nor does it include information from HRS off-years studies, administrative linkages, or even all of the tracking information in the Tracker file. The RAND Longitudinal File has many advantages especially for new users but for seasoned researchers as well. For example, RAND constructs many variables that would take a lot of time for individual researchers to create such as total household wealth and income. Thus in practice, most researchers make use of RAND HRS data products merged with HRS original files. This chapter will give you the tools you need to work with all of these data files.

### <span style="color: #147ca4; font-family: cambria"> Data Management with HRS original data </span>

Several elements will help you manage the data. This section begins with information to help you understand the data file naming conventions, levels of data files, and the naming conventions of HRS original variables. All data files can be merged using identification variables.


### <span style="color: #147ca4; font-family: cambria"> Data File Naming Conventions </span>

As noted above, the HRS original data files for the core interview are provided as a set for each wave, with individual data files for each interview section. Figure 10 provides an example of a data file name from the 2020 wave for section C (health), which is a respondent level file.  The “h” at the beginning of the file name just stands for HRS. The second two places are a number indicating the wave (1992-2020). The third part of the file name is a letter indicating the interview section. Then there is an underscore followed by a letter that indicates the level of the file. Appendix C provides a table with all 2020 public data files names listed by section. Note that this table is included in the data description for each core wave. 

Appendix D provides summary of biennial core section content for 2020 and the letter that corresponds to each section in the file name.  Appendix E provides a key to the last part of the file name, the level indicator, which we describe next.


### <span style="color: red; font-family: cambria"> Insert figure 10 here</span>
Figure 10. Data file naming convention, example for section C: health status



### <span style="color: #147ca4; font-family: cambria"> Levels of Core and Exit Data </span>

In the core survey, most questions are asked of all respondents and apply specifically to the respondents themselves, such as self-rated health or current employment status. Some questions are asked about the household, such as the number of people living in the household. For these questions, in two-respondent households, household level questions are asked of one respondent who is designated as the financial respondent, family respondent, or cover screen respondent (the first respondent interviewed) on behalf of the entire household. 

The core survey contains a range of questions about the respondents’ children, siblings, and helpers. To facilitate use of these data, HRS Core data releases for each wave contain files at seven other levels: household member-and-child, sibling, helper, transfer-to-child, transfer-from-child, jobs, and pension. These are described in more detail in [Appendix E]. The two most commonly used levels of HRS original core data files are:

**Respondent-level files** contain questions that were asked of all respondents about themselves (or asked of a proxy about the respondent if the respondent was not able to give an interview). The files contain one record for each respondent or proxy who gave an interview. These files are available for core and exit files for all years.

**Household-level files** contain questions asked about the household. A coversheet respondent answered family questions on behalf of the entire household. Similarly, a family respondent answered family questions on behalf of the entire household, and a financial respondent answered household-level financial questions on behalf of the entire household. The household-level files contain one record for each household in which at least one interview was obtained. These files are available for core files for all years.


### <span style="color: #147ca4; font-family: cambria"> Variable Naming Conventions </span>

Variable naming conventions in the HRS original data are not completely consistent, especially in the earlier waves. Beginning in 2000 (and especially in 2002), the variable naming convention depicted in Figure 11 was adopted and is reasonably consistent since then. The first letter in HRS original variable names is a letter that indicates the wave. [Appendix F] provides the key to the wave indicators (column 2, HRS prefix). The second letter indicates the content section. [Appendix D] provides a key to biennial core sections for the 2020 wave. Then the numeric portion is the variable number. In the example, the first letter of the variable name is R, which indicates that the variable comes from the 2020 wave of core data. The second letter indicates that the variable comes from section C (health), and the variable number is 001, which is for self-rated health.


### <span style="color: red; font-family: cambria"> Insert figure 11 here</span>
Figure 11. Variable naming convention 2000 onward, example for section C: self-rated health status


### <span style="color: #147ca4; font-family: cambria"> Identification Variables</span>

Two primary identification variables (HHID and PN) uniquely identify a particular respondent record in a data file. Other identification variables, such as sub-household ID, allow merging with files from other levels (e.g., household level or helper level). 

### Household identification or HHID 

As described in the first section of this guide, HRS seeks to interview individuals within households. Both members in coupled households are interviewed. Over time, HRS tracks complex and changing household structures including divorce, widowhood, and remarriage. Therefore, we need one variable that identifies the household and another that identifies a person within that household. 

HHID is a 6-digit character variable assigned to a household at baseline. It is stable across all waves of data. It uniquely identifies the original household and any households derived from that household in subsequent waves. 

### Person Number or PN 

Person number is a 3 digit, character variable that is unique within an original household (HHID) that does not change across waves. It has values of 010 and 020 that are assigned to original respondents in a household.  010 is one member of a couple and 020 is the other member. Anything other than 010 or 020 (e.g., 011, 012, 021, etc…) are new spouse/partners of respondents who get re-married/re-partnered. 

### Sub-household ID or SUBHH

As noted, household composition can change over time as people experience widowhood, divorce/split and remarriage. Sub-household ID is a one digit, character variable. In combination with HHID, xSUBHH (where x is the letter wave indicator) uniquely identifies a household at a given wave. Sub-household IDs can be different at each wave. In the baseline interview, all households for the wave are considered 'original' households and have a SUBHH of zero. Respondents can have a sub-household identifier at a particular wave even if they did not provide an interview. The codes for SUBHH include:

0.  Original household
1.  Sub-household, split off from original
2.  Sub-household, split off from original
3.  Deceased respondent household
4.  Deceased respondent household
5.  Sub-household, split off a household that already split into a '1' and '2'
6.  Sub-household, split off a household that already split into a '1' and '2'
7.  Used when two respondents split and then recombine with each other
8.  Sub-household, split off a household that already split into a '1' and '2'
9.  Not in the sample this wave

Figures 12a-12d show examples of how the SUBHH changes with these potential household changes wave to wave.


<table class="table-style">
  <tr>
    <th>2006</th>
    <th>2008</th>
  </tr>
  <tr>
    <td>Married</td>
    <td>Married</td>
  </tr>
  <tr>
    <td>HHID=123456, PN=010, KSUBHH=0 <br> HHID=123456, PN=020, KSUBHH=0</td>
    <td>HHID=123456, PN=010, LSUBHH=0 <br> HHID=123456, PN=020, LSUBHH=0</td>
  </tr>
</table>



Figure 12a. Married/partnered couple stays together


<table class="table-style">
  <tr>
    <th>2006</th>
    <th>2008</th>
  </tr>
  <tr>
    <td>Married</td>
    <td>010 dies between waves</td>
  </tr>
  <tr>
    <td>HHID=123456, PN=010, KSUBHH=0 <br> HHID=123456, PN=020, KSUBHH=0</td>
    <td>HHID=123456, PN=010, LSUBHH=3 <br> HHID=123456, PN=020, LSUBHH=0</td>
  </tr>
</table>


Figure 12b. One person in a married/partnered couple dies


<table class="table-style">
  <tr>
    <th>2006</th>
    <th>2008</th>
  </tr>
  <tr>
    <td>Married</td>
    <td>Divorced</td>
  </tr>
  <tr>
    <td>HHID=123456, PN=010, KSUBHH=0 <br> HHID=123456, PN=020, KSUBHH=0</td>
    <td>HHID=123456, PN=010, LSUBHH=1 <br> HHID=123456, PN=020, LSUBHH=2</td>
  </tr>
</table>



Figure 12c. Married/partnered couple divorces


<table class="table-style">
  <tr>
    <th>2006</th>
    <th>2008</th>
  </tr>
  <tr>
    <td>Married</td>
    <td>Divorced, 010 remarries between waves</td>
  </tr>
  <tr>
    <td>HHID=123456, PN=010, KSUBHH=0 <br> HHID=123456, PN=020, KSUBHH=0</td>
    <td>HHID=123456, PN=010, LSUBHH=1 <br> HHID=123456, PN=011, LSUBHH=1 <br> HHID=123456, PN=020, LSUBHH=2 </td>
  </tr>
</table>


Figure 12d. Married/partnered couple divorces, and one remarries




[//]: # (links within document)
[Appendix E]: <../chapter-8/hrs8.md>
[Appendix F]: <../chapter-8/hrs8.md>
[Appendix D]: <../chapter-8/hrs8.md>

[//]: # (links to the website)
[RAND Longitudinal File]: <https://hrs.isr.umich.edu/>