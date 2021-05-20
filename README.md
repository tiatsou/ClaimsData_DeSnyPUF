# ClaimsData_DeSnyPUF
Analyzing outpatient claims data to find out the high utilizers and the economic impact.

### Background
Datasets used in this project are DE-SynPuf and are retrived from National Rural Health Resource Center. The Data Entrepreneurs’ Synthetic Public Use File (DE-SynPUF) is a set of realistic claims data from 2008 through 2010 made available by CMS(Centers for Medicare & Medicaid Services). And the project followed the tutorial mentioned in this [website](https://www.ruralcenter.org/population-health-toolkit/data/using-claims-data).

- Data: 
1. DE1_0_2008_Beneficiary_Summary_File_Sample_1
2. DE1_0_2008_to_2010_Outpatient_Claims_Sample_1

- Goal: 
Find relationship between outpatient medicare reimbursement and the beneficiaries' chronic condition
  - relationshp between Number of Claims and outpatient medicare reimbursement annual amount
  - how to difine super utilizer
 
### Steps Applied
1. import *Beneficiary* and *Outpatient* data from CVS and change the data type
2. create new factor column *Year* based on the *CLM_THRU_DT* variable in *Outpatient* data
3. create new numeric column *NumerOfClaims* by counting the number of outpatient claim from *Outpatient* data for each beneficiary ID in *Beneficiary* data
4. use pivot table to find the summary statistics for the cleaned data

![image](https://user-images.githubusercontent.com/83623711/119059058-8f4b1a80-b99d-11eb-8725-3735e0eaf1cc.png)

5. plot scatter plot to show the relationship between number of claims and annual medicare reimbursement amount 
   - based on the scatter plot, the more claims tend to have higher reimbursement amount

![image](https://user-images.githubusercontent.com/83623711/119058157-d1735c80-b99b-11eb-9c4e-45d6372e61db.png)

6. use pivot table to find how to define the high utilizers
   - the max number of claims is 33 while the 99% of beneficiaries claims less than 14
   - beneficiaries with more than 14 cliams will be assigned as high utilizers

![image](https://user-images.githubusercontent.com/83623711/119058722-e56b8e00-b99c-11eb-894b-d4caeb62cf03.png)

7. create new binary colum *SuperUtilizer* based on the findings in step 6
8. use pivot table to find the common chronic condition among the high utilizer
   - about 89% of the high utilizers have diabetes 

![image](https://user-images.githubusercontent.com/83623711/119058925-4b581580-b99d-11eb-8c0a-3a8688576dd4.png)

### Conclusion and Recommondation
- more cliams filed by a beneficiary tend to have more medicare reimbursement with 0.39 R Square
- the super utilizer is defined by beneficairies who filed more than 14 claims
- there is a high population(89%) in High Utilizers have diabetes
- the hospital can provide additional information about appropriateness of medical services and how to reach out to the primary healthcare providers. 
- whether the High Utilizer use the outpatient service appropriately in our case needs further analysis

### Reference
Using Claims Data. National Rural Health Resource Center. https://www.ruralcenter.org/population-health-toolkit/data/using-claims-data




