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


<!-- TO DO: Insert figure 10 here -->
<img src="/chapter-7/ch7-images/Figure-10.svg" alt="Figure-10">


Figure 10. Data file naming convention, example for section C: health status



### <span style="color: #147ca4; font-family: cambria"> Levels of Core and Exit Data </span>

In the core survey, most questions are asked of all respondents and apply specifically to the respondents themselves, such as self-rated health or current employment status. Some questions are asked about the household, such as the number of people living in the household. For these questions, in two-respondent households, household level questions are asked of one respondent who is designated as the financial respondent, family respondent, or cover screen respondent (the first respondent interviewed) on behalf of the entire household. 

The core survey contains a range of questions about the respondents’ children, siblings, and helpers. To facilitate use of these data, HRS Core data releases for each wave contain files at seven other levels: household member-and-child, sibling, helper, transfer-to-child, transfer-from-child, jobs, and pension. These are described in more detail in [Appendix E]. The two most commonly used levels of HRS original core data files are:

**Respondent-level files** contain questions that were asked of all respondents about themselves (or asked of a proxy about the respondent if the respondent was not able to give an interview). The files contain one record for each respondent or proxy who gave an interview. These files are available for core and exit files for all years.

**Household-level files** contain questions asked about the household. A coversheet respondent answered family questions on behalf of the entire household. Similarly, a family respondent answered family questions on behalf of the entire household, and a financial respondent answered household-level financial questions on behalf of the entire household. The household-level files contain one record for each household in which at least one interview was obtained. These files are available for core files for all years.


### <span style="color: #147ca4; font-family: cambria"> Variable Naming Conventions </span>

Variable naming conventions in the HRS original data are not completely consistent, especially in the earlier waves. Beginning in 2000 (and especially in 2002), the variable naming convention depicted in Figure 11 was adopted and is reasonably consistent since then. The first letter in HRS original variable names is a letter that indicates the wave. [Appendix F] provides the key to the wave indicators (column 2, HRS prefix). The second letter indicates the content section. [Appendix D] provides a key to biennial core sections for the 2020 wave. Then the numeric portion is the variable number. In the example, the first letter of the variable name is R, which indicates that the variable comes from the 2020 wave of core data. The second letter indicates that the variable comes from section C (health), and the variable number is 001, which is for self-rated health.


<!-- TO DO: Insert figure 11 here -->
<img src="/chapter-7/ch7-images/Figure-11.svg" alt="Figure-11">


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


### Partner person number or PPN  

xPPN is a three digit identifies the person number of the spouse or partner of a sample member if the sample member is part of a couple. For all the sample members still alive in a given wave, a concatenation of their own person numbers (PN) with xPPN in ascending order would generate xCOUPID. For deceased sample members, xPPN gives the person numbers of their spouses or partners in the last wave during which they were alive. More detail about the PPN is available in the data description for Tracker. 

VISIT THE WEBSITE: Documentation>Data Descriptions>Tracker 

### Other person number or OPN  

OPN is a 3-digit, character variable. In combination with HHID and xSUBHH, OPN uniquely identifies another person that respondents provide information about, such as: 

Household members 
Children 

Or in combination with HHID and PN, OPN identifies a 

Helper 

Sibling 


Specifically, OPN is used in sections E, F, and G to keep track of siblings, children, and helpers, parents, and other household members, in data collection loops. Whereas, other identification variables are available in the Tracker file, the OPN is available in the core data file for each wave. More detail about the OPN is available in the data description for each core data product. 

VISIT THE WEBSITE: Documentation>Data Descriptions>2020 HRS Core 

### Overlap cases 

Overlaps refer to cases that have multiple primary IDs and require special handling in constructing longitudinal files and in merging Tracker data to wave-specific files. The variables HHID and PN reflect the current status of the case, while overlap cases also have a former HHID and PN values from a previous wave. These former values are provided in the identification variables OVHHD and OVPN. More detail is provided in Appendix G. 


### <span style="color: #147ca4; font-family: cambria"> GETTING READY TO USE THE HRS ORIGINAL DATA </span>

As you get ready to use the data, there are several things you should be thinking about.  

- Begin by identifying the variables you need for your analysis and the data files that contain them. It is a good idea to select only the variables you need from each file, since smaller data files are more manageable. Remember that the Concordance tool can help you search for variables in the HRS original data. 

- If you are using longitudinal information for the same variable, it is a good idea to understand any potential differences in the question wording or changes in the code frame that may have occurred over time. Don’t forget to consult the Alternate Wave Chart, for variables that are only asked every other wave. 

- Think about what the unit of analysis is: the individual, the household, a couple, respondent-caregiver, other? Knowing what level of analysis you want to do will help you know what merges you need to do. If you are merging files, will you have one record per respondent, one record per household or what? What identification variables will be required to merge the various files that contain variables needed for your analysis?  

- If you are merging variables across data files, what type of merge will be required? Will the merge be a one-to-one matching of records, e.g., respondent-to-respondent, or a one-to-many, e.g., household-to-respondent, matching?


### <span style="color: #147ca4; font-family: cambria"> REGISTER FOR THE HRS ORIGINAL DATA </span>

Begin by registering to access the data. To register for the public data, go to the Data Products link from the homepage. On the right hand side of the page, you’ll see the set of links under HRS Data Portal shown in Figure 13. 


<!-- TO DO: Figure 13 goes here -->


Figure 13. HRS Data Portal 

After that, simply complete the registration information on the Create New Account link. You will receive login credentials that you will use each time you login to the website.  

Come back to this page to use your credentials to login. The other way you can create an account or login after creating an account is a yellow bar across the top of the page for every HRS data file. See Figure 14 for an example to download the Cross-wave Tracker File. 


<!-- TO DO: Figure 14 goes here -->


Figure 14. Create account and login on the data products page for the Tracker File 

Do read the Conditions of Use! This contains important information about citing the data in your manuscripts, emailing hrspublications@umich.edu when you have research products to share (dissertation, thesis, journal article, book, book chapter, report, etc.), and letting us know if your registration information changes.  

Of key importance is the provision for very limited third party distribution of the data. You will also find here instructions for submitting replication datasets that may be required by journals where you are submitting your HRS research. 

During registration, you will have the opportunity to sign up to receive quarterly user newsletters and data announcements. We recommend that you sign up for both.  


### <span style="color: #147ca4; font-family: cambria"> DOWNLOAD AND GET READY TO USE THE HRS ORIGINAL DATA </span>

Now you are ready to begin downloading data from the HRS website. Go to the data file you are interested in using and login. After you are logged in you will see the data files for download. We describe here the distribution files, focusing particularly on core data and our recommendation for a file structure to download to your PC or laptop. Note that the distribution set includes program statements to “build” the data files. Note that from 2018 onward, the distribution set includes the data files already built. However, it also includes the program statements. 


### <span style="color: #147ca4; font-family: cambria"> Distribution Files </span>

The files are packaged for download from the HRS web site in two different ways – as one large .zip file that contains six smaller .zip files, one .pdf file, and one .txt file, or the eight smaller files available individually for separate download. For example, for the 2016 wave of core data, the combined file is H16core.zip.  

The distribution set includes the data description, codebook, and questionnaire for the file. The data are available in ASCII, SPSS, SAS, and Stata file formats. 

Note that when you open the zipped file for the core interview for any given biennial wave, you will see separate data files for each separate section (e.g., section C: Health etc…).. 


### <span style="color: #147ca4; font-family: cambria"> Directory Structure and Contents </span>


While a particular setup is not required for using HRS files, we suggest a directory structure. By using this directory structure, you will not have to change the path name in your program statement files. If you use a different structure, just change the directory references in the program statement files.  

Again, using the 2016 Core Wave as an example. The individual .zip files for separate download are: Data file H16da.zip contains data files. Program statement files H16sas.zip contains SAS program statements. H16sps.zip contains SPSS program statements. H16sta.zip contains STATA program statements. Documentation files H16cb.zip contains the codebook. H16qn.zip contains the questionnaire. H16dd.pdf - this document.  

Directory 

Contents 

c:\hrs2016  

Files downloaded from Web site 

c:\hrs2016\codebook 

Unzipped files from H16cb.zip 

c:\hrs2016\data 

Unzipped files from H16da.zip 

c:\hrs2016\qnaire 

Unzipped files from H16qn.zip 

c:\hrs2016\sas 

Unzipped files from H16sas.zip 

c:\hrs2016\spss 

Unzipped files from H16sps.zip 

c:\hrs2016\stata 

Unzipped files from H16sta.zip 

Decompress the selected .zip files into the appropriate subdirectories.  


### <span style="color: #147ca4; font-family: cambria"> Program Statements </span>

All core data files for waves 1992 through 2016 need to be “built.” Each data file comes with associated SPSS, SAS, or STATA program statements to read the data. Files containing SPSS statements are named with .SPS extension, those with SAS statements with a .SAS extension, and those with STATA statements with .DO and .DCT extensions. The statement files are named beginning with the same prefix as the corresponding data file. For example, SAS statements in the file H16A_R.SAS go with the H16A_R.DA data file. 



### <span style="color: #147ca4; font-family: cambria"> MERGING HRS ORIGINAL DATA FILES </span>


For many analyses, you may need to merge various HRS data files. We provide detail for the most common merges. Recall that HRS original files are provided at different levels previously described. Merging between and across files levels requires the use of the identification variables already described. The statistical code to accomplish the merges is contained in Appendix H.  

### <span style="color: #147ca4; font-family: cambria"> Merging two or more respondent-level files </span>

The most common type of merge with HRS original data is a respondent level merge of two or more respondent-level data files. Figure 15 illustrates this merge with an example dataset from two respondent level data files: the Tracker file (Trk2020tr_r) and H20C_R, the file containing data from Section C. Health for the 2020 wave. When we combine these files using the identifiers HHID and PN we get one new merged file (HRS2020_1).  


<!-- TO DO: Figure 15 goes here -->


Figure 15. Merging two or more respondent level files 


### <span style="color: #147ca4; font-family: cambria"> Merging two household-level files </span>

To create a household-level file with data from two or more household-level files, merge the household-level files using HHID and nSUBHH where nSUBHH is the current-wave SUBHH. Figure 16 illustrates this merge with an example dataset from two household level data files: the file containing data from Section H. Housing (H20H_H) and the file containing data from Section E. Family Structure (H20E_H) for the 2020 wave. When we combine these files using the identifiers HHID and RSUBHH we get one new merged file (HRS2020_2). 


<!-- TO DO: Figure 16 goes here -->


Figure 16. Merging two or more household level files 


### <span style="color: #147ca4; font-family: cambria"> Merging household-level data onto a respondent-level file  </span>

Sometimes we need to merge data from a household level file with respondent-level data. Here we are putting the household level variable onto each respondent-level record, maintaining a respondent-level file. To do this, we merge the respondent-level file(s) and the household-level file(s) using HHID and nSUBHH where nSUBHH is the current wave SUBHH. Figure 17 illustrates this merge with an example dataset from one respondent level data file and one household level file: the Tracker file (Trk2020tr_r) and H20Q_H (the file containing data from Section Q. Assets and Income). When we combine these files using the identifiers HHID and SUBHH we get one file (HRS2020_3).  


<!-- TO DO: Figure 17 goes here -->
<img src="/chapter-7/ch7-images/Figure-17-1.svg" alt="Figure-17-1">
<img src="/chapter-7/ch7-images/Figure-17-2.svg" alt="Figure-17-2">


Figure 17. Merging household level data on a respondent level file 


### <span style="color: #147ca4; font-family: cambria"> Combining data from both household members </span>

ShapeSome analyses are facilitated by combining data from two respondents in the same file. For example, studies that examine so called “dyadic interactions,” or the effect of partners on each other, require data to be by structured so that respondent level data in wide format (one row for each respondent) has corollary partner data on the same line. Specifically, here we are performing a respondent-level merge to add information from one partner’s record to the other. We start by creating a “spouse” file. Figure 18 shows that we start with a respondent-level file. Then we create a “spouse” file by changing PN to RPPN (a wave-specific PPN) and rename the variable by adding S to the end (RC001S). Keep only HHID, new PN, and the new spouse variable of interest, which yields the new dataset we’ll call HRS2020_couple.  


<!-- TO DO: Figure 18 goes here -->


Figure 18. Combining data from both household members 


### <span style="color: #147ca4; font-family: cambria"> Merging respondent-level files across two or more waves </span>

Figure 19 illustrates merging respondent level files longitudinally using two respondent level data files: H18C_R and H20C_R, the files containing data from Section C. Health for the2018 and 2020 waves. When we combine these files using the identifiers HHID and PN we get one new merged file (HRS2020_4).  


<!-- TO DO: Figure 19 goes here -->


Figure 19. Merging respondent-level files across two or more waves 


### <span style="color: #147ca4; font-family: cambria"> Merging a helper-level file with a respondent-level file  </span>

We summarize this information by creating a single record per respondent. 


<!-- TO DO: Figure 20 goes here -->


Figure 20. Merging a helper-level file with a respondent-level file 


### <span style="color: #147ca4; font-family: cambria"> DATA MANAGEMENT WITH RAND HRS PRODUCTS </span>

As with the HRS original data, data management with the RAND HRS Products requires an understanding of some of the key features of the data including the variable naming conventions, the identification variables, and the structure of the data. As we will show, part of the processing that goes into creating RAND HRS Products involves some of the merges we have just discussed. The two most commonly used RAND HRS data products are the RAND HRS Longitudinal File and the Fat Files. 

### <span style="color: #147ca4; font-family: cambria"> RAND HRS Longitudinal File Structure </span>

To create the RAND HRS Longitudinal File, RAND researchers merge a large selection of variables from across the core biennial sections, including the exit interviews, for all available waves. They also merge some household level information, such as household income.  

An important feature of the RAND HRS Longitudinal File is that it also merges some spouse/partner data (for coupled households) onto to their partner’s record (as discussed in Combining data from both household members). To distinguish one respondent’s information from the other, RAND uses the prefix designation of “S” in the variable name, as shown in the section of this guide describing the RAND HRS Longitudinal File Variable Naming Conventions. This makes it convenient for individual-level analyses that consider spouse or partner characteristics as potentially influencing an individual. Because there are separate records (lines) for each member of the couple, the data are also structured to allow you to conduct couples-levels “dyadic” analyses.  

Consider the case of Shawn and Casey, who are a couple both providing interviews in the HRS (see Figure 21). We also have respondents who are not partnered, such as Ethel, and there is no need for an S variable for that individual. In the RAND HRS Longitudinal File, they would appear as: 


<table class="table-style">
  <tr>
    <th>HHID</th>
    <th>PN</th>
    <th>R1SHLT</th>
    <th>S1HLTH</th>
  </tr>
  <tr>
    <td>123456</td>
    <td>010 (Shawn)</td>
    <td>3</td>
    <td>2</td>
  </tr>
  <tr>
    <td>123456</td>
    <td>020 (Casey)</td>
    <td>2</td>
    <td>3</td>
  </tr>
    <tr>
    <td>234567</td>
    <td>010 (Ethel)</td>
    <td>4</td>
    <td>.U</td>
  </tr>
 <caption class="child">.U=unmarried/partnered</caption>

</table>

Figure 21. Structure of the RAND HRS Longitudinal File 


As noted, HRS tracks changes in relationship status over time. The RAND Longitudinal File (like the Tracker File) contains records for all members of an original household as well as subsequent re-partnerships stemming from it. For example, if Shawn and Casey split, their records will remain in the data, but their S variables will now be missing (.U) from the wave that they were no longer partnered until (if) either of them re-partners. New partners are enrolled as respondents. 

RAND creates a household wave-specific identification variable called HwHHID, which is HHID plus the wave-specific SUBHH and the PN. To provide additional assistance in tracking re-partnerings, they also include a variable called SwHHIDPN. xPPN and xPN_SP are used in the creation of SwHHIDPN, which assigns the Respondent’s spouse each wave. If respondents change spouses between wave 1 and wave 2, S1HHIDPN will be different than S2HHIDPN. Otherwise, it will be the same or 0/missing (for no spouse from divorce/widow/etc).   

Finally, a very important feature of the RAND HRS Longitudinal File is that is includes a wide range of constructed variables. For example, the HRS interview collects large amounts of information on sources of household income and household wealth. The Longitudinal File contains wave-specific summary variables for each of these important variables (HwITOT for total household income and HwATOTA for total house hold wealth). Another example of a constructed variable in the Longitudinal File that draws on a large number of HRS original variables is tenure in longest held job (RwJLTEN). 

VISIT THE WEBSITE: Data Products>RAND HRS Products>RAND HRS Longitudinal File 2020 


### <span style="color: #147ca4; font-family: cambria"> RAND HRS Longitudinal File Codebook </span>

RAND creates very detailed codebooks that you will consult often as you use the data.  Note that the codebook for the RAND HRS Longitudinal File is very large (more than 1,700 pages), but is a searchable pdf. The codebook is called randhrs1992_2020v1.pdf, listed under the documentation. 

It is very worthwhile to familiarize yourself with the structure of the codebook and be sure to read through the entry for any variables you use so that you are aware of what assumptions, if any, were used in the process of creating it. There is a lot of important introductory information at the beginning of the codebook, such as “What’s New” in each data release, how to download the data and set up your computing environment, some simple programming examples (such as performing a merge), and so forth.   


For each variable, the codebook includes: 

  - Variable list: for each wave, contains name, label and variable type (continuous or categorical) 

  - Descriptive statistics: N, mean, standard deviation, minimum, maximum 

  - Categorical variable codes: all variable values and frequencies by survey wave 

  - How constructed: defines what information the variable captures and describes missing values 

  - Cross wave differences in the HRS original data: describes any changes in the survey that may impact longitudinal analysis  

  - HRS original data variables used: name and label of all original HRS variables used to construct the variable 

 

Note that the codebook provides frequency distributions for the “S” variables, but these do not represent separate individuals represented by the “R” variables. For any given wave, the count for the “S” variable is included in the count for the “R” variable. And if you subtracted the count for any “R” variable in a given wave from the count for the “S” variable (R5CESD minus S5CESD, for example), you would have roughly the count in that wave of single households. 

VISIT THE WEBSITE: Data Products>RAND HRS Products>RAND HRS Longitudinal File 2020 



### <span style="color: #147ca4; font-family: cambria"> RAND HRS Fat Files </span>

The RAND Fat files are individual respondent-level datasets for each wave of the HRS that include almost all the variables from each interview section merged into a single (very large)  respondent-level file. These files can easily be merged with other RAND HRS data products (by HHIDPN), or with the any of the HRS original data files. The Fat Files are not processed and contain only HRS original variables.  


### <span style="color: #147ca4; font-family: cambria"> RAND HRS Longitudinal File Variable Naming Conventions</span>

One of the things that can be confusing using HRS original data is that the variable names, especially in the earlier waves of core data, were inconsistently named. All variables in the RAND HRS Longitudinal File are renamed to be longitudinally consistent across survey waves and follow a standardized naming convention, depicted in Figure 22.  


<!-- TO DO: figure 22 goes here -->
<img src="/chapter-7/ch7-images/Figure-22.svg" alt="Figure-22">


Figure 22. RAND HRS Data Products variable naming conventions  

The first letter indicates “who” the variable reports on: “R” indicates the respondent, “S” indicates a spouse or partner, and “H” indicates the entire household. The second portion of the variable name is a number that indicates the RAND HRS wave number that corresponds to a survey year. Appendix F shows the correspondence between the HRS original data wave indicator and the RAND wave indicator. The last part of the variable name is the variable stem which, in this case, refers to self-reported health. 

Some variables are not wave-specific and therefore do not have a wave number. These are mostly identifiers and demographic variables that do not change by wave. These variables have an “A” instead of a wave number (EX: RABYEAR is the Respondent’s birth year).  Also, the Exit Interview variables have an “E” instead of the wave number.   


### <span style="color: #147ca4; font-family: cambria"> Identification variables </span>

All RAND HRS Data Products can easily be merged with other RAND HRS data products and with any of the HRS original data files.  

The primary identification variables HHID and PN are included in the RAND Longitudinal File (and all RAND HRS data products). RAND also creates a version of the original household identification (HHID) and person number (PN) that is simply a combination of the HHID and PN variables provided in Tracker. To merge any RAND product, you can use HHIDPN, but to merge to an HRS original data product, you have a couple of options. 

You can merge on HHID and PN or you can create RAHHIDPN (a character version of HHID PN). Below we provide the code to create RAHHIDPN with the HRS original data. 

SAS: 	RAHHIDPN = HHID || PN; 

Stata: 	genstr9 rahhidpn=hhid+ pn; 

SPSS: 	String RAHHIDPN (A9). 

Compute RAHHIDPN = concat(HHID,PN).  


### <span style="color: #147ca4; font-family: cambria"> CREATING AN ANALYSIS FILE </span>

The RAND HRS Longitudinal File contains a large part of the HRS original core data, and many users complete their research projects using only this data file. As you have seen, however, there is a vast amount of data collected in other parts of the study that you are likely to want to combine with the resources of the RAND HRS Longitudinal File. Even if you are drawing more heavily on data from other parts of the study, you will likely want to use some constructed variables, such as total household wealth and total household income. The RAND HRS Longitudinal File is a respondent-level file, so just follow the code for the appropriate merge given your needs.  

### <span style="color: #147ca4; font-family: cambria"> TWO IMPORTANT PROCEDURES TO RESTRUCTURE THE DATA </span>
### <span style="color: #147ca4; font-family: cambria"> Transforming data files file from “wide” to “long” </span>

The HRS original data and RAND HRS data products are all in wide format, including those that contain cross-wave longitudinal data, such as the Tracker file and the RAND HRS Longitudinal File. That means that there is one record (row) for each respondent (HHID PN), and variables are in the columns for the longitudinal waves. It is often useful to restructure to a “long” format with one record per respondent per wave (HHID PD STUDYYR). Figure 23 depicts this restructuring graphically for the 2020 Tracker file using the example of the variable interview type (IWTYPE). Appendix H provides the code to accomplish this restructuring.  


<table>
  <tr>
    <th colspan="10">TRK2016</th>
  </tr>
  <tr>
  <th>HHID</th>
  <th>PN</th>
  <th>GENDER</th>
  <th>AIWTYPE</th>
  <th>BIWTYPE</th>
  <th>CIWTYPE</th>
  <th>DIWTYPE</th>
  <th>EIWTYPE</th>
  <th>FIWTYPE</th>
  <th>GIWTYPE</th>
  </tr>
  <tr>
    <td>123456</td>
    <td>010</td>
    <td>1</td>
    <td>1</td>
    <td>99</td>
    <td>1</td>
    <td>99</td>
    <td>11</td>
    <td>99</td>
    <td>99</td>
  </tr>
</table>


<table>
  <tr>
    <th colspan="6">longTrk</th>
  </tr>
  <tr>
    <th>HHID</th>
    <th>PN</th>
    <th>GENDER</th>
    <th>STUDYYR</th>
    <th>HRSPREFIX</th>
    <th>IWTYPE</th>
  </tr>
  <tr>
    <td>123456</td>
    <td>010</td>
    <td>1</td>
    <td>1992</td>
    <td>a</td>
    <td>1</td>
  </tr>
    <tr>
    <td>123456</td>
    <td>010</td>
    <td>1</td>
    <td>1993</td>
    <td>b</td>
    <td>99</td>
  </tr>
    <tr>
    <td>123456</td>
    <td>010</td>
    <td>1</td>
    <td>1994</td>
    <td>c</td>
    <td>1</td>
  </tr>
    <tr>
    <td>123456</td>
    <td>010</td>
    <td>1</td>
    <td>1995</td>
    <td>d</td>
    <td>99</td>
  </tr>
    <tr>
    <td>123456</td>
    <td>010</td>
    <td>1</td>
    <td>1996</td>
    <td>e</td>
    <td>11</td>
  </tr>
  <tr>
    <td>123456</td>
    <td>010</td>
    <td>1</td>
    <td>1998</td>
    <td>f</td>
    <td>99</td>
  </tr>
  <tr>
    <td>123456</td>
    <td>010</td>
    <td>1</td>
    <td>2000</td>
    <td>g</td>
    <td>99</td>
  </tr>

</table>

Figure 23. Transforming the data from wide to long  


### <span style="color: #147ca4; font-family: cambria"> Stacking Enhanced Face-to-Face interview data from adjacent waves   </span>

As shown, data from the EFTF are on a random half of the core sample each wave.  Some researchers choose to combine the data from the two half samples, usually combining 2006 and 2008, 2010 and 2012, 2014 and 2016, and 2018 and 2020.  You can think of this as creating four longitudinal waves of EFTF data. In order to do this, we need to address the fact that the variable names change over time. In the HRS original data, from 2002 onward, variable names are the same across waves, except for the alphabetic wave prefix. Note that some of the variables in the LB (psychosocial questionnaire) change over time, so you will need to rename these individually.  

Figure 24 shows this for 2006 and 2008. First, create separate EFTF datasets for 2006 & 2008. Next, remove the wave-specific prefix from the variable names: 2006 = K and 2008 = L. Then stack the resulting datasets.  



<!-- TO DO: insert figure 24 here -->



Figure 24. Stacking Enhanced Face-to-Face interview data from adjacent waves 

Appendix H provides the code to accomplish this restructuring. 

[//]: # (links within document)
[Appendix E]: <../chapter-8/hrs8.md>
[Appendix F]: <../chapter-8/hrs8.md>
[Appendix D]: <../chapter-8/hrs8.md>

[//]: # (links to the website)
[RAND Longitudinal File]: <https://hrs.isr.umich.edu/>