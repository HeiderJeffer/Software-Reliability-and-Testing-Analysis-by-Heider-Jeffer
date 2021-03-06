# Assignment 1: Reduce the number of combinations

The goal of this task is to design and develop in Java test cases that can reduce the combinations foreseen in the data csv files.  Use JUnit 4 to create the annotate tests and the Unit runner Parameterized or the TestRule

Create a repository in gitlab.in.unibz.it for your code. 

SubTasks:

- [X] Reduce the input combinations by automatically merging data from the three files: Account.csv, ProfitCenter.csv CRCComponents.csv. You can do it reading all files and creating a new file with all combinations or reading each file and create an object to pass to the isValid method with a valid combination. 

- [X] Use parametrised tests either with Parameterized runner or with RuleTest. For this you have first to implement a file.csv reader. See the files I uploaded in gitlab

- [X] Create a test for the method isValid() for each combination 

![Alt text](example2/data/Assignment 1 Reduce the number of combinations.PNG)

# 1st Assignment - Reduce the number of combinations

## Test class
`src/com/wuerth/phoenix/cis/university/example1/test/Test.java`

## Dependency
JUnit4 and JRE System Library.

## Total combinations and reduction strategy
Total combinations was 56, which was generated automatically by `CombinationGenerator.Java`
`src/com/wuerth/phoenix/cis/university/example1/test/CombinationGenerator.Java`

Steps of `CombinationGenerator.java` to reduce the combinations were:
* Read `Account.csv`
    * skipped 1st row (table header)
    * skipped 1st column because `getCode()` method from `Account.java` is not used as an valid criteria at `Example1Checker.java`
    * removed duplicates from 1819 rows to 23 rows

* Read `CRComponent.csv`
    * skipped 1st row (table header)
    * skipped 1st column because `getName()` method from `CRComponent.java` is not used as an valid criteria at `Example1Checker.java`
    * removed duplicates from 21 rows to 3 rows

* Read `ProfitCenter.csv`
    * skipped 1st row (table header)
    * skipped 1st column because `getName()` method from `ProfitCenter.java` is not used as an valid criteria at `Example1Checker.java`
    * removed duplicates from 78 rows to 2 rows

* Combined Account, CRComponent, and ProfitCenter from 23 x 3 x 2 to 138 rows
* Filtered valid combinations by passing object to `isValid()` method and wrote 56 combinations to `Combination.csv`
* Implemented unit test by using parameterized test and read reduced combinations at `Combination.csv`
![Alt text](data/result.PNG)

### Combinations
```
accountCode,accountClass,accountType,isPartnerAllowed,pcName,isNotAllocated,crName,isNotAllocated,isVKAllowed,isSEANAllowed,external,dataScenarioType,partnerCode,currencyCode
Code,Logistics,,false,ProfitCenter,true,CRComponent,true,true,true,true,Actual,,
Code,AllocationFormula,,false,ProfitCenter,true,CRComponent,false,false,false,true,Actual,,
Code,AllocationFormula,,false,ProfitCenter,true,CRComponent,true,true,true,true,Actual,,
Code,AllocationFormula,,false,ProfitCenter,true,CRComponent,false,true,true,true,Actual,,
Code,AllocationFormula,,false,ProfitCenter,false,CRComponent,false,false,false,true,Actual,,
Code,AllocationFormula,,false,ProfitCenter,false,CRComponent,true,true,true,true,Actual,,
Code,AllocationFormula,,false,ProfitCenter,false,CRComponent,false,true,true,true,Actual,,
Code,BalanceSheet,,false,ProfitCenter,true,CRComponent,true,true,true,true,Actual,,
Code,BalanceSheet,,false,ProfitCenter,false,CRComponent,true,true,true,true,Actual,,
Code,BalanceSheet,AssetPartner,true,ProfitCenter,true,CRComponent,true,true,true,true,Actual,,
Code,BalanceSheet,AssetPartner,true,ProfitCenter,false,CRComponent,true,true,true,true,Actual,,
Code,BalanceSheet,,true,ProfitCenter,true,CRComponent,true,true,true,true,Actual,,
Code,BalanceSheet,,true,ProfitCenter,false,CRComponent,true,true,true,true,Actual,,
Code,SalesReporting,Customer,false,ProfitCenter,true,CRComponent,false,false,false,true,Actual,,
Code,SalesReporting,Customer,false,ProfitCenter,true,CRComponent,false,true,true,true,Actual,,
Code,SalesReporting,Customer,false,ProfitCenter,false,CRComponent,false,false,false,true,Actual,,
Code,SalesReporting,Customer,false,ProfitCenter,false,CRComponent,false,true,true,true,Actual,,
Code,SalesReporting,SpecialAnalyses,false,ProfitCenter,true,CRComponent,true,true,true,true,Actual,,
Code,SalesReporting,SpecialAnalysesNumOfInvoicingDays,false,ProfitCenter,true,CRComponent,false,false,false,true,Actual,,
Code,SalesReporting,SpecialAnalysesNumOfInvoicingDays,false,ProfitCenter,true,CRComponent,true,true,true,true,Actual,,
Code,SalesReporting,SpecialAnalysesNumOfInvoicingDays,false,ProfitCenter,true,CRComponent,false,true,true,true,Actual,,
Code,SalesReporting,SpecialAnalysesNumOfInvoicingDays,false,ProfitCenter,false,CRComponent,false,false,false,true,Actual,,
Code,SalesReporting,SpecialAnalysesNumOfInvoicingDays,false,ProfitCenter,false,CRComponent,true,true,true,true,Actual,,
Code,SalesReporting,SpecialAnalysesNumOfInvoicingDays,false,ProfitCenter,false,CRComponent,false,true,true,true,Actual,,
Code,SalesReporting,SML,false,ProfitCenter,true,CRComponent,false,false,false,true,Actual,,
Code,SalesReporting,SML,false,ProfitCenter,true,CRComponent,false,true,true,true,Actual,,
Code,SalesReporting,SML,false,ProfitCenter,false,CRComponent,false,false,false,true,Actual,,
Code,SalesReporting,SML,false,ProfitCenter,false,CRComponent,false,true,true,true,Actual,,
Code,SalesReporting,SMLGrossProfit,false,ProfitCenter,true,CRComponent,false,false,false,true,Actual,,
Code,SalesReporting,SMLGrossProfit,false,ProfitCenter,true,CRComponent,true,true,true,true,Actual,,
Code,SalesReporting,SMLGrossProfit,false,ProfitCenter,true,CRComponent,false,true,true,true,Actual,,
Code,SalesReporting,SMLGrossProfit,false,ProfitCenter,false,CRComponent,false,false,false,true,Actual,,
Code,SalesReporting,SMLGrossProfit,false,ProfitCenter,false,CRComponent,true,true,true,true,Actual,,
Code,SalesReporting,SMLGrossProfit,false,ProfitCenter,false,CRComponent,false,true,true,true,Actual,,
Code,SalesReporting,SMLPotential,false,ProfitCenter,true,CRComponent,false,false,false,true,Actual,,
Code,SalesReporting,SMLPotential,false,ProfitCenter,true,CRComponent,true,true,true,true,Actual,,
Code,SalesReporting,SMLPotential,false,ProfitCenter,true,CRComponent,false,true,true,true,Actual,,
Code,SalesReporting,SMLPotential,false,ProfitCenter,false,CRComponent,false,false,false,true,Actual,,
Code,SalesReporting,SMLPotential,false,ProfitCenter,false,CRComponent,true,true,true,true,Actual,,
Code,SalesReporting,SMLPotential,false,ProfitCenter,false,CRComponent,false,true,true,true,Actual,,
Code,SalesReporting,SEAN,false,ProfitCenter,true,CRComponent,true,true,true,true,Actual,,
Code,SalesReporting,SEAN,false,ProfitCenter,false,CRComponent,true,true,true,true,Actual,,
Code,SalesReporting,SpecialAnalysesServiceDegree,false,ProfitCenter,true,CRComponent,false,false,false,true,Actual,,
Code,SalesReporting,SpecialAnalysesServiceDegree,false,ProfitCenter,true,CRComponent,true,true,true,true,Actual,,
Code,SalesReporting,SpecialAnalysesServiceDegree,false,ProfitCenter,true,CRComponent,false,true,true,true,Actual,,
Code,SalesReporting,SpecialAnalysesServiceDegree,false,ProfitCenter,false,CRComponent,false,false,false,true,Actual,,
Code,SalesReporting,SpecialAnalysesServiceDegree,false,ProfitCenter,false,CRComponent,true,true,true,true,Actual,,
Code,SalesReporting,SpecialAnalysesServiceDegree,false,ProfitCenter,false,CRComponent,false,true,true,true,Actual,,
Code,SalesReporting,Employees,false,ProfitCenter,true,CRComponent,true,true,true,true,Actual,,
Code,SalesReporting,Employees,false,ProfitCenter,false,CRComponent,true,true,true,true,Actual,,
Code,SalesReporting,VK,false,ProfitCenter,true,CRComponent,true,true,true,true,Actual,,
Code,PLStatement,PrognosisNumOfAdmDecember,false,ProfitCenter,true,CRComponent,true,true,true,true,Actual,,
Code,PLStatement,PrognosisNumOfAdmMPlus1,false,ProfitCenter,true,CRComponent,true,true,true,true,Actual,,
Code,PLStatement,PrognosisNumOfAdmMPlus2,false,ProfitCenter,true,CRComponent,true,true,true,true,Actual,,
Code,PLStatement,PrognosisOperatingResult,false,ProfitCenter,true,CRComponent,true,true,true,true,Actual,,
Code,PLStatement,PrognosisSales,false,ProfitCenter,true,CRComponent,true,true,true,true,Actual,,
```

## New CSV file
data\Combinations.csv