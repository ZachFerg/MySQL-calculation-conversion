# MySQL-calculation-conversion
We'll be tracking filemaker calculations and how to convert them for MySQL

# `currentAltStage`
### Fields Used for `currentAltStage`:
|   production_log   | production_log (cont.) |
|:------------------:|:---------------------:|
| date170Packed      | date060Cropping       |
| date165cPkgPrinted | date040DataEntry      |
| date150bRipQC      | date020Upload         |
| date150PackageRip  | date010bIn            |
| date140GreenScreen | date010In             |
| date130Retouching  |                       |
| date030Color       |                       |
| date110OrderEntry  |                       |
| date070QC          |                       |
| date601Rescan      |                       |
#### `currentAltStage` FileMaker calculation:
```SQL	
    Case ( 
    Shoot_Log||PRODUCTION_initialrun::date170Packed≠"";"Shipping";
    Shoot_Log||PRODUCTION_initialrun::date165cPkgPrinted≠"";"Packing";
    Shoot_Log||PRODUCTION_initialrun::date150bRipQC≠"";"Printing";
    Shoot_Log||PRODUCTION_initialrun::date150PackageRip≠"";"Post Rip QC";
    Shoot_Log||PRODUCTION_initialrun::date130Retouching≠"";"Ripping";
    Shoot_Log||PRODUCTION_initialrun::date110OrderEntry≠"";"Retouch";
    Shoot_Log||PRODUCTION_initialrun::date030Color≠"" and Shoot_Log||PRODUCTION_initialrun::date601Rescan≠"";"Order Entry";
    Shoot_Log||PRODUCTION_initialrun::date030Color≠"";"Retouch";
    Shoot_Log||PRODUCTION_initialrun::date070QC≠"";"Color";
    Shoot_Log||PRODUCTION_initialrun::date060Cropping≠"";"QC";
    Shoot_Log||PRODUCTION_initialrun::date040DataEntry≠"";"Cropping";
    Shoot_Log||PRODUCTION_initialrun::date020Upload≠"";"Data";
    Shoot_Log||PRODUCTION_initialrun::date010bIn≠"";"Upload";
    Shoot_Log||PRODUCTION_initialrun::date010In≠"";"Receiving";
    "Not In"
    )
```
#### `currentAltStage` SQL Expression:
lorem ipsum

***

# `currentCCGStage`
### Fields Used for `currentCCGStage`
|   production_log   | production_log (cont.) |
|:------------------:|:---------------------:|
|       |        |
#### `currentAltStage` FileMaker calculation:
```SQL
	Case ( 
	Shoot_Log::programActual="Service Prints" and Shoot_Log||PRODUCTION_initialrun::date170Packed≠"";"Shipping";
	Shoot_Log::programActual="Service Prints" and Shoot_Log||PRODUCTION_initialrun::date165cPkgPrinted≠"";"Packing";
	Shoot_Log::programActual="Service Prints" and Shoot_Log||PRODUCTION_initialrun::date150bRipQC≠"";"Printing";
	Shoot_Log::programActual="Service Prints" and Shoot_Log||PRODUCTION_initialrun::date150PackageRip≠"";"Post Rip QC";
	Shoot_Log::programActual="Service Prints" and Shoot_Log||PRODUCTION_initialrun::date070QC≠"";"Ripping";
	Shoot_Log::programActual="Service Prints" and Shoot_Log||PRODUCTION_initialrun::date060Cropping≠"";"QC";
	Shoot_Log::programActual="Service Prints" and Shoot_Log||PRODUCTION_initialrun::date030Color≠"";"Cropping";
	Shoot_Log::programActual="Service Prints" and Shoot_Log||PRODUCTION_initialrun::date040DataEntry≠"";"Color";
	Shoot_Log::programActual="Service Prints" and Shoot_Log||PRODUCTION_initialrun::date020Upload≠"";"Data";
	Shoot_Log::programActual="Service Prints" and Shoot_Log||PRODUCTION_initialrun::date010bIn≠"";"Upload";
	Shoot_Log::programActual="Service Prints" and Shoot_Log||PRODUCTION_initialrun::date010In≠"";"Receiving";

	Program Name | Actual Program::programType = "Proof" and Shoot_Log::CCG_HowShot = "Flash Card" and Shoot_Log||PRODUCTION_initialrun::date170Packed ≠ "";"Shipping";
	Program Name | Actual Program::programType = "Proof" and Shoot_Log::CCG_HowShot = "Flash Card" and Shoot_Log||PRODUCTION_initialrun::date165cPkgPrinted ≠ "";"Packing";
	Program Name | Actual Program::programType = "Proof" and Shoot_Log::CCG_HowShot = "Flash Card" and Shoot_Log||PRODUCTION_initialrun::date150bRipQC ≠ "";"Printing";
	Program Name | Actual Program::programType = "Proof" and Shoot_Log::CCG_HowShot = "Flash Card" and Shoot_Log||PRODUCTION_initialrun::date150PackageRip ≠ "";"Post Rip QC";
	Program Name | Actual Program::programType = "Proof" and Shoot_Log::CCG_HowShot = "Flash Card" and Shoot_Log||PRODUCTION_initialrun::date120OnlineOrders ≠ "";"Ripping";
	Program Name | Actual Program::programType = "Proof" and Shoot_Log::CCG_HowShot = "Flash Card" and Shoot_Log||PRODUCTION_initialrun::date110OrderEntry ≠ "";"Online";
	Program Name | Actual Program::programType = "Proof" and Shoot_Log::CCG_HowShot = "Flash Card" and Shoot_Log||PRODUCTION_initialrun::date100ProofIn ≠ "";"Order Entry";
	Program Name | Actual Program::programType = "Proof" and Shoot_Log::CCG_HowShot = "Flash Card" and Shoot_Log||PRODUCTION_initialrun::date090ProofShip ≠ "";"Proof In";
	Program Name | Actual Program::programType = "Proof" and Shoot_Log::CCG_HowShot = "Flash Card" and Shoot_Log||PRODUCTION_initialrun::date170PackedProof ≠ "";"Shipping";
	Program Name | Actual Program::programType = "Proof" and Shoot_Log::CCG_HowShot = "Flash Card" and Shoot_Log||PRODUCTION_initialrun::date165aProofPrinting ≠ "";"Packing";
	Program Name | Actual Program::programType = "Proof" and Shoot_Log::CCG_HowShot = "Flash Card" and Shoot_Log||PRODUCTION_initialrun::date150bPostProofRipQC ≠ "";"Printing";
	Program Name | Actual Program::programType = "Proof" and Shoot_Log::CCG_HowShot = "Flash Card" and Shoot_Log||PRODUCTION_initialrun::date070ProofRip ≠ "";"Post Rip QC";
	Program Name | Actual Program::programType = "Proof" and Shoot_Log::CCG_HowShot = "Flash Card" and Shoot_Log||PRODUCTION_initialrun::date130ZRetouchingTotal ≠ "";"Ripping";
	Program Name | Actual Program::programType = "Proof" and Shoot_Log::CCG_HowShot = "Flash Card" and Shoot_Log||PRODUCTION_initialrun::date070QC ≠ "";"Retouch";
	Program Name | Actual Program::programType = "Proof" and Shoot_Log::CCG_HowShot = "Flash Card" and Shoot_Log||PRODUCTION_initialrun::date060Cropping ≠ "";"QC";
	Program Name | Actual Program::programType = "Proof" and Shoot_Log::CCG_HowShot = "Flash Card" and Shoot_Log||PRODUCTION_initialrun::date050BestOf ≠ "";"Cropping";
	Program Name | Actual Program::programType = "Proof" and Shoot_Log::CCG_HowShot = "Flash Card" and Shoot_Log||PRODUCTION_initialrun::date030Color ≠ "";"Best Of";
	Program Name | Actual Program::programType = "Proof" and Shoot_Log::CCG_HowShot = "Flash Card" and Shoot_Log||PRODUCTION_initialrun::date040DataEntry ≠ "";"Color";
	Program Name | Actual Program::programType = "Proof" and Shoot_Log::CCG_HowShot = "Flash Card" and Shoot_Log||PRODUCTION_initialrun::date020Upload ≠ "";"Data";
	Program Name | Actual Program::programType = "Proof" and Shoot_Log::CCG_HowShot = "Flash Card" and Shoot_Log||PRODUCTION_initialrun::date010bIn ≠ "";"Upload";
	Program Name | Actual Program::programType = "Proof" and Shoot_Log::CCG_HowShot = "Flash Card" and Shoot_Log||PRODUCTION_initialrun::date010In ≠ "";"Receiving";

	Shoot_Log::programActual="Panorama" or Shoot_Log::programActual="High School Grad Group" ; Case ( 
	Shoot_Log||PRODUCTION_initialrun::date170Packed≠"";"Shipping";
	Shoot_Log||PRODUCTION_initialrun::date165cPkgPrinted≠"";"Packing";
	Shoot_Log||PRODUCTION_initialrun::date150bRipQC ≠ "";"Printing";
	Shoot_Log||PRODUCTION_initialrun::date150PackageRip ≠ "";"Post Rip QC";
	Shoot_Log||PRODUCTION_initialrun::date120OnlineOrders≠"";"Ripping";
	Shoot_Log||PRODUCTION_initialrun::date130ZRetouchingTotal≠"";"Online";
	Shoot_Log||PRODUCTION_initialrun::date020Upload≠"";"Retouch";
	Shoot_Log||PRODUCTION_initialrun::date010bIn≠"";"Upload";
	Shoot_Log||PRODUCTION_initialrun::date010In≠"";"Receiving";
	);

	PatternCount ( Shoot_Log::programActual;"Faculty Group" ) and Shoot_Log||PRODUCTION_initialrun::date170Packed≠"";"Shipping";
	PatternCount ( Shoot_Log::programActual;"Faculty Group" ) and Shoot_Log||PRODUCTION_initialrun::date165cPkgPrinted≠"";"Packing";
	PatternCount ( Shoot_Log::programActual;"Faculty Group" ) and Shoot_Log||PRODUCTION_initialrun::date150bRipQC≠"";"Printing";
	PatternCount ( Shoot_Log::programActual;"Faculty Group" ) and Shoot_Log||PRODUCTION_initialrun::date150PackageRip≠"";"Post Rip QC";
	PatternCount ( Shoot_Log::programActual;"Faculty Group" ) and Shoot_Log||PRODUCTION_initialrun::date130fOverlays≠"" and returnToRetouch≠"" ;"Retouch";
	PatternCount ( Shoot_Log::programActual;"Faculty Group" ) and Shoot_Log||PRODUCTION_initialrun::date130fOverlays≠"" and returnToRetouch="" ;"Ripping";
	PatternCount ( Shoot_Log::programActual;"Faculty Group" ) and Shoot_Log||PRODUCTION_initialrun::date060Cropping≠"";"Retouch";
	PatternCount ( Shoot_Log::programActual;"Faculty Group" ) and Shoot_Log||PRODUCTION_initialrun::date050BestOf≠"";"Cropping";
	PatternCount ( Shoot_Log::programActual;"Faculty Group" ) and Shoot_Log||PRODUCTION_initialrun::date030Color≠"";"Best Of";
	PatternCount ( Shoot_Log::programActual;"Faculty Group" ) and Shoot_Log::date001CheckIn≠"";"Color";
	PatternCount ( Shoot_Log::programActual;"Faculty Group" ) and Shoot_Log||PRODUCTION_initialrun::date040DataEntry≠"";"Check In";
	PatternCount ( Shoot_Log::programActual;"Faculty Group" ) and Shoot_Log||PRODUCTION_initialrun::date020Upload≠"";"Data";
	PatternCount ( Shoot_Log::programActual;"Faculty Group" ) and Shoot_Log||PRODUCTION_initialrun::date010bIn≠"";"Upload";
	PatternCount ( Shoot_Log::programActual;"Faculty Group" ) and Shoot_Log||PRODUCTION_initialrun::date010In≠"";"Receiving";

	Shoot_Log::CCG_HowShot="Flash Card" and Shoot_Log||PRODUCTION_initialrun::date170Packed≠"";"Shipping";
	Shoot_Log::CCG_HowShot="Flash Card" and Shoot_Log||PRODUCTION_initialrun::date165cPkgPrinted≠"";"Packing";
	Shoot_Log::CCG_HowShot="Flash Card" and Shoot_Log||PRODUCTION_initialrun::date150bRipQC≠"";"Printing";
	Shoot_Log::CCG_HowShot="Flash Card" and Shoot_Log||PRODUCTION_initialrun::date150PackageRip≠"";"Post Rip QC";
	Shoot_Log::CCG_HowShot="Flash Card" and Shoot_Log||PRODUCTION_initialrun::date120OnlineOrders≠"";"Ripping";
	Shoot_Log::CCG_HowShot="Flash Card" and Shoot_Log||PRODUCTION_initialrun::date601Rescan≠"" and Shoot_Log||PRODUCTION_initialrun::date770QCRecheck≠"";"Online";
	Shoot_Log::CCG_HowShot="Flash Card" and Shoot_Log||PRODUCTION_initialrun::date770QCRecheck≠"";"Scanning";
	Shoot_Log::CCG_HowShot="Flash Card" and Shoot_Log||PRODUCTION_initialrun::date130ZRetouchingTotal≠"";"QC Recheck";
	Shoot_Log::CCG_HowShot="Flash Card" and Shoot_Log||PRODUCTION_initialrun::date070QC≠"";"Retouch";
	Shoot_Log::CCG_HowShot="Flash Card" and Shoot_Log::nameOnShoot="Yes" and Shoot_Log||PRODUCTION_initialrun::date070QC≠"";"Retouch";
	Shoot_Log::CCG_HowShot="Flash Card" and Shoot_Log::nameOnShoot="Yes" and Shoot_Log::date330InDesign≠"";"QC";
	Shoot_Log::CCG_HowShot="Flash Card" and Shoot_Log::nameOnShoot="Yes" and Shoot_Log::date320DataProc≠"";"InDesign";
	Shoot_Log::CCG_HowShot="Flash Card" and Shoot_Log::nameOnShoot="Yes" and Shoot_Log::date310NamesIn≠"" and Shoot_Log||PRODUCTION_initialrun::date060Cropping≠"";"Data Proc";
	Shoot_Log::CCG_HowShot="Flash Card" and Shoot_Log::nameOnShoot="Yes" and Shoot_Log||PRODUCTION_initialrun::date060Cropping≠"" and Shoot_Log::Names_W_Job="Yes";"Data Proc";
	Shoot_Log::CCG_HowShot="Flash Card" and Shoot_Log::nameOnShoot="Yes" and Shoot_Log||PRODUCTION_initialrun::date060Cropping≠"";"Images Out";
	Shoot_Log::CCG_HowShot="Flash Card" and Shoot_Log||PRODUCTION_initialrun::date060Cropping≠"";"QC";
	Shoot_Log::CCG_HowShot="Flash Card" and Shoot_Log||PRODUCTION_initialrun::date050BestOf≠"";"Cropping";
	Shoot_Log::CCG_HowShot="Flash Card" and Shoot_Log||PRODUCTION_initialrun::date030Color≠"";"Best Of";
	Shoot_Log::CCG_HowShot="Flash Card" and Shoot_Log||PRODUCTION_initialrun::date040DataEntry≠"";"Color";
	Shoot_Log::CCG_HowShot="Flash Card" and Shoot_Log||PRODUCTION_initialrun::date020Upload≠"";"Data";
	Shoot_Log::CCG_HowShot="Flash Card" and Shoot_Log||PRODUCTION_initialrun::date010bIn≠"";"Upload";
	Shoot_Log::CCG_HowShot="Flash Card" and Shoot_Log||PRODUCTION_initialrun::date010In≠"";"Receiving";

	Shoot_Log::CCG_HowShot="Into Flow" and Shoot_Log||PRODUCTION_initialrun::date170Packed≠"";"Shipping";
	Shoot_Log::CCG_HowShot="Into Flow" and Shoot_Log||PRODUCTION_initialrun::date165cPkgPrinted≠"";"Packing";
	Shoot_Log::CCG_HowShot="Into Flow" and Shoot_Log||PRODUCTION_initialrun::date150bRipQC≠"";"Printing";
	Shoot_Log::CCG_HowShot="Into Flow" and Shoot_Log||PRODUCTION_initialrun::date150PackageRip≠"";"Post Rip QC";
	Shoot_Log::CCG_HowShot="Into Flow" and Shoot_Log||PRODUCTION_initialrun::date120OnlineOrders≠"";"Ripping";
	Shoot_Log::CCG_HowShot="Into Flow" and Shoot_Log||PRODUCTION_initialrun::date110OrderEntry≠"";"Online";
	Shoot_Log::CCG_HowShot="Into Flow" and Shoot_Log||PRODUCTION_initialrun::date601Rescan≠"" and Shoot_Log||PRODUCTION_initialrun::date770QCRecheck≠"";"Order Entry";
	Shoot_Log::CCG_HowShot="Into Flow" and Shoot_Log||PRODUCTION_initialrun::date770QCRecheck≠"";"Scanning";
	Shoot_Log::CCG_HowShot="Into Flow" and Shoot_Log||PRODUCTION_initialrun::date130ZRetouchingTotal≠"";"QC Recheck";
	Shoot_Log::CCG_HowShot="Into Flow" and Shoot_Log||PRODUCTION_initialrun::date070QC≠"";"Retouch";
	Shoot_Log::CCG_HowShot="Into Flow" and Shoot_Log::nameOnShoot="Yes" and Shoot_Log::date330InDesign≠"";"QC";
	Shoot_Log::CCG_HowShot="Into Flow" and Shoot_Log::nameOnShoot="Yes" and Shoot_Log::date320DataProc≠"";"InDesign";
	Shoot_Log::CCG_HowShot="Into Flow" and Shoot_Log::nameOnShoot="Yes" and Shoot_Log::date310NamesIn≠"" and Shoot_Log||PRODUCTION_initialrun::date060Cropping≠"";"Data Proc";
	Shoot_Log::CCG_HowShot="Into Flow" and Shoot_Log::nameOnShoot="Yes" and Shoot_Log||PRODUCTION_initialrun::date060Cropping≠"" and Shoot_Log::Names_W_Job="Yes";"Data Proc";
	Shoot_Log::CCG_HowShot="Into Flow" and Shoot_Log::nameOnShoot="Yes" and Shoot_Log||PRODUCTION_initialrun::date060Cropping≠"";"Images Out";
	Shoot_Log::CCG_HowShot="Into Flow" and Shoot_Log||PRODUCTION_initialrun::date060Cropping≠"";"QC";
	Shoot_Log::CCG_HowShot="Into Flow" and Shoot_Log||PRODUCTION_initialrun::date050BestOf≠"";"Cropping";
	Shoot_Log::CCG_HowShot="Into Flow" and Shoot_Log||PRODUCTION_initialrun::date030Color≠"";"Best Of";
	Shoot_Log::CCG_HowShot="Into Flow" and Shoot_Log||PRODUCTION_initialrun::date020Upload≠"";"Color";
	Shoot_Log::CCG_HowShot="Into Flow" and Shoot_Log||PRODUCTION_initialrun::date040DataEntry≠"";"Upload";
	Shoot_Log::CCG_HowShot="Into Flow" and Shoot_Log||PRODUCTION_initialrun::date010bIn≠"";"Data";
	Shoot_Log::CCG_HowShot="Into Flow" and Shoot_Log||PRODUCTION_initialrun::date010In≠"";"Receiving";
	"Not In"
	)
```
#### SQL Expression:
lorem ipsum

***

# currentFacultyStage
```SQL	
	Case ( 
	PatternCount ( Shoot_Log::programActual;"No Package" ) and Shoot_Log||PRODUCTION_initialrun::date150PackageRip≠"";"Shipping";
	Shoot_Log||PRODUCTION_initialrun::date170Packed≠"";"Shipping";
	Shoot_Log||PRODUCTION_initialrun::date165cPkgPrinted≠"";"Packing";
	Shoot_Log||PRODUCTION_initialrun::date150bRipQC≠"";"Printing";
	Shoot_Log||PRODUCTION_initialrun::date150PackageRip≠"";"Post Rip QC";
	Shoot_Log||PRODUCTION_initialrun::date070QC≠"";"Ripping";
	Shoot_Log||PRODUCTION_initialrun::date140GreenScreen≠"" and Shoot_Log||PRODUCTION_initialrun::date030Color≠"";"QC";
	PatternCount ( Shoot_Log::shootNotes;"green" ) and Shoot_Log||PRODUCTION_initialrun::date030Color≠"";"Green Screen";
	Shoot_Log||PRODUCTION_initialrun::date030Color≠"";"QC";
	Shoot_Log||PRODUCTION_initialrun::date060Cropping≠"";"Color";
	Shoot_Log||PRODUCTION_initialrun::date040DataEntry≠"";"Cropping";
	Shoot_Log||PRODUCTION_initialrun::date020Upload≠"";"Data";
	Shoot_Log||PRODUCTION_initialrun::date010bIn≠"";"Upload";
	Shoot_Log||PRODUCTION_initialrun::date010In≠"";"Receiving";
	"Not In"
	)
```
#### SQL Expression:
lorem ipsum

***

# currentPrepayStage
### Fields Used:
|   production_log   | production_log (cont) | program |
|:------------------:|:---------------------:|---------|
| date170Packed      | date060Cropping       | bgko    |
| date165cPkgPrinted | date040DataEntry      |         |
| date150bRipQC      | date020Upload         |         |
| date150PackageRip  | date010bIn            |         |
| date140GreenScreen | date010In             |         |
| date130Retouching  |                       |         |
| date030Color       |                       |         |
| date110OrderEntry  |                       |         |
| date070QC          |                       |         |
| date601Rescan      |                       |         |


```SQL
	Case ( 
	Shoot_Log||PRODUCTION_initialrun::date170Packed≠"";"Shipping";
	Shoot_Log||PRODUCTION_initialrun::date165cPkgPrinted≠"";"Packing";
	Shoot_Log||PRODUCTION_initialrun::date150bRipQC≠"";"Printing";
	Shoot_Log||PRODUCTION_initialrun::date150PackageRip≠"";"Post Rip QC";
	Shoot_Log||PRODUCTION_initialrun::date140GreenScreen≠"";"Ripping";
	Shoot_Log||PRODUCTION_initialrun::date130Retouching≠"" and Program Name | Actual Program::bgko = "Yes";"BG-KO";
	Shoot_Log||PRODUCTION_initialrun::date130Retouching≠"";"Ripping";
	Shoot_Log||PRODUCTION_initialrun::date030Color≠"";"Retouch";
	Shoot_Log||PRODUCTION_initialrun::date110OrderEntry≠"";"Color";
	Shoot_Log||PRODUCTION_initialrun::date070QC≠"" and Shoot_Log||PRODUCTION_initialrun::date601Rescan≠"";"Order Entry";
	Shoot_Log||PRODUCTION_initialrun::date070QC≠"";"Scanning";
	Shoot_Log||PRODUCTION_initialrun::date060Cropping≠"";"QC";
	Shoot_Log||PRODUCTION_initialrun::date040DataEntry≠"";"Cropping";
	Shoot_Log||PRODUCTION_initialrun::date020Upload≠"";"Data";
	Shoot_Log||PRODUCTION_initialrun::date010bIn≠"";"Upload";
	Shoot_Log||PRODUCTION_initialrun::date010In≠"";"Receiving";
	"Not In"
	)
```
#### SQL Expression:
lorem ipsum

***

# currentProofStage
```SQL
	Case ( 
	Shoot_Log||PRODUCTION_initialrun::date170Packed≠"";"Shipping";
	Shoot_Log||PRODUCTION_initialrun::date165cPkgPrinted≠"";"Packing";
	Shoot_Log||PRODUCTION_initialrun::date150bRipQC≠"";"Printing";
	Shoot_Log||PRODUCTION_initialrun::date150PackageRip≠"";"Post Rip QC";
	Shoot_Log||PRODUCTION_initialrun::date140GreenScreen≠"";"Ripping";
	Shoot_Log||PRODUCTION_initialrun::date130Retouching≠"" and Program Name | Actual Program::bgko = "Yes";"BG-KO";
	Shoot_Log||PRODUCTION_initialrun::date130Retouching≠"";"Ripping";
	Shoot_Log||PRODUCTION_initialrun::date110OrderEntry≠"";"Retouch";
	Shoot_Log||PRODUCTION_initialrun::date100ProofIn≠"" and Shoot_Log::shootNotes="No Orders" and moneyInPlantDate01="";"Order Entry";
	Shoot_Log||PRODUCTION_initialrun::date601Rescan≠"";"Order Entry";
	Shoot_Log||PRODUCTION_initialrun::date100ProofIn≠"" and Shoot_Log::shootNotes≠"No Orders" and moneyInPlantDate01≠"";"Scanning" ;
	Shoot_Log||PRODUCTION_initialrun::date100ProofIn≠"" and Shoot_Log::shootNotes≠"No Orders" and moneyInPlantDate01="";"Waiting On Orders";
	Shoot_Log||PRODUCTION_initialrun::date090ProofShip≠"";"Proof Return" ;
	Shoot_Log||PRODUCTION_initialrun::date170PackedProof≠"";"Shipping" ;
	Shoot_Log||PRODUCTION_initialrun::date165aProofPrinting≠"";"Packing";
	Shoot_Log||PRODUCTION_initialrun::date150bPostProofRipQC≠"";"Printing";
	Shoot_Log||PRODUCTION_initialrun::date070ProofRip≠"";"Post Rip QC";
	Shoot_Log||PRODUCTION_initialrun::date030Color≠"";"Ripping";
	Shoot_Log||PRODUCTION_initialrun::date060Cropping≠"";"Color" ;
	Shoot_Log||PRODUCTION_initialrun::date040DataEntry≠"";"Cropping";
	Shoot_Log||PRODUCTION_initialrun::date020Upload≠"";"Data";
	Shoot_Log||PRODUCTION_initialrun::date010bIn≠"";"Upload";
	Shoot_Log||PRODUCTION_initialrun::date010In≠"";"Receiving";
	"Not In"
	)
```
#### SQL Expression:
lorem ipsum

***

# currentSeniorStage
### Fields Used:
| production_log         | production_log (cont) | contract      |
|------------------------|-----------------------|---------------|
| date170Packed          | date010bIn            | seniorPoseHow |
| date165cPkgPrinted     | date010In             |               |
| date150bPostProofRipQC |                       |               |
| date070ProofRip        |                       |               |
| date070QC              |                       |               |
| date200SrYb            |                       |               |
| date060Cropping        |                       |               |
| date030Color           |                       |               |
| date040DataEntry       |                       |               |
| date020Upload          |                       |               |
```SQL
	Case ( 
	Shoot_Log||PRODUCTION_initialrun::date170Packed≠"";"Shipping";
	Shoot_Log||PRODUCTION_g_shootid::date165cPkgPrinted≠"";"Packing";
	Shoot_Log||PRODUCTION_g_shootid::date150bPostProofRipQC≠"";"Printing";
	Shoot_Log||PRODUCTION_g_shootid::date070ProofRip≠"";"Post Rip QC";
	Shoot_Log||PRODUCTION_initialrun::date070QC≠"";"Ripping";
	Shoot_Log||PRODUCTION_initialrun::date200SrYb≠"";"QC";
	Shoot_Log||PRODUCTION_initialrun::date060Cropping≠"" and Contract::seniorPoseHow="Onsite";"Services";
	Shoot_Log||PRODUCTION_initialrun::date060Cropping≠"" and Contract::seniorPoseHow="Best of's";"Services";
	Shoot_Log||PRODUCTION_initialrun::date060Cropping≠"" and Contract::seniorPoseHow="Onsite/Mugbook";"Services";
	Shoot_Log||PRODUCTION_initialrun::date060Cropping≠"" and Contract::seniorPoseHow="Onsite/PMC";"Services";
	Shoot_Log||PRODUCTION_initialrun::date060Cropping≠"" and Contract::seniorPoseHow="Onsite/IQ";"Services";
	Shoot_Log||PRODUCTION_initialrun::date060Cropping≠"" and Contract::seniorPoseHow="Best of's/Mugbook";"Services";
	Shoot_Log||PRODUCTION_initialrun::date060Cropping≠"" and Contract::seniorPoseHow="Best of's/PMC";"Services";
	Shoot_Log||PRODUCTION_initialrun::date060Cropping≠"" and Contract::seniorPoseHow="Best of's/IQ";"Services";
	Shoot_Log||PRODUCTION_initialrun::date060Cropping≠"";"QC";
	Shoot_Log||PRODUCTION_initialrun::date030Color≠"";"Cropping";
	Shoot_Log||PRODUCTION_initialrun::date040DataEntry≠"";"Color";
	Shoot_Log||PRODUCTION_initialrun::date020Upload≠"";"Data";
	Shoot_Log||PRODUCTION_initialrun::date010bIn≠"";"Upload";
	Shoot_Log||PRODUCTION_initialrun::date010In≠"";"Receiving";
	"Not In"
	)
```
***

# currentSpecStage
### Fields Used:
| production_log     |
|--------------------|
| date170Packed      |
| date165cPkgPrinted |
| date150bRipQC      |
| date150PackageRip  |
| date030Color       |
| date060Cropping    |
| date040DataEntry   |
| date020Upload      |
| date010bIn         |
| date010In          |
### Filemaker:
```SQL
	Case ( 
	Shoot_Log||PRODUCTION_initialrun::date170Packed≠"";"Shipping" ;
	Shoot_Log||PRODUCTION_initialrun::date165cPkgPrinted≠"";"Packing" ;
	Shoot_Log||PRODUCTION_initialrun::date150bRipQC≠"";"Printing" ;
	Shoot_Log||PRODUCTION_initialrun::date150PackageRip≠"";"Post Rip QC" ;
	Shoot_Log||PRODUCTION_initialrun::date030Color≠"";"Ripping" ;
	Shoot_Log||PRODUCTION_initialrun::date060Cropping≠"";"Color" ;
	Shoot_Log||PRODUCTION_initialrun::date040DataEntry≠"";"Cropping";
	Shoot_Log||PRODUCTION_initialrun::date020Upload≠"";"Data";
	Shoot_Log||PRODUCTION_initialrun::date010bIn≠"";"Upload";
	Shoot_Log||PRODUCTION_initialrun::date010In≠"";"Receiving";
	"Not In"
	)
```
#### SQL Expression:
lorem ipsum

***

# currentSportsStage
```SQL
	Case ( 
	Shoot_Log::programActual="School Sports 50 Proof" and Shoot_Log||PRODUCTION_initialrun::date170Packed≠"";"Shipping";
	Shoot_Log::programActual="School Sports 50 Proof" and Shoot_Log||PRODUCTION_initialrun::date165cPkgPrinted≠"";"Packing";
	Shoot_Log::programActual="School Sports 50 Proof" and Shoot_Log||PRODUCTION_initialrun::date150bPostProofRipQC≠"";"Printing";
	Shoot_Log::programActual="School Sports 50 Proof" and Shoot_Log||PRODUCTION_initialrun::date070ProofRip≠"";"Post Rip QC";
	Shoot_Log::programActual="School Sports 50 Proof" and Shoot_Log||PRODUCTION_initialrun::date140GreenScreen≠"";"Ripping";
	Shoot_Log::programActual="School Sports 50 Proof" and Shoot_Log||PRODUCTION_initialrun::date130Retouching≠"" and Program Name | Actual Program::bgko = "Yes";"BG-KO";
	Shoot_Log::programActual="School Sports 50 Proof" and Shoot_Log||PRODUCTION_initialrun::date130Retouching≠"";"Ripping";
	Shoot_Log::programActual="School Sports 50 Proof" and Shoot_Log||PRODUCTION_initialrun::date070QC≠"";"Retouch";
	Shoot_Log::programActual="School Sports 50 Proof" and Shoot_Log||PRODUCTION_initialrun::date060Cropping≠"";"QC";
	Shoot_Log::programActual="School Sports 50 Proof" and Shoot_Log||PRODUCTION_initialrun::date030Color≠"";"Cropping";
	Shoot_Log::programActual="School Sports 50 Proof" and Shoot_Log||PRODUCTION_initialrun::date020Upload≠"";"Color";
	Shoot_Log::programActual="School Sports 50 Proof" and Shoot_Log||PRODUCTION_initialrun::date040DataEntry≠"";"Upload";
	Shoot_Log::programActual="School Sports 50 Proof" and Shoot_Log||PRODUCTION_initialrun::date010bIn≠"";"Data";
	Shoot_Log::programActual="School Sports 50 Proof" and Shoot_Log||PRODUCTION_initialrun::date010In≠"";"Receiving";

	Shoot_Log::programActual="School Sports 50 Online Proof Only" and Shoot_Log||PRODUCTION_initialrun::date140GreenScreen≠"";"Ripping";
	Shoot_Log::programActual="School Sports 50 Online Proof Only" and Shoot_Log||PRODUCTION_initialrun::date130Retouching≠"" and Program Name | Actual Program::bgko = "Yes";"BG-KO";
	Shoot_Log::programActual="School Sports 50 Online Proof Only" and Shoot_Log||PRODUCTION_initialrun::date130Retouching≠"";"Ripping";
	Shoot_Log::programActual="School Sports 50 Online Proof Only" and Shoot_Log||PRODUCTION_initialrun::date070QC≠"";"Retouch";
	Shoot_Log::programActual="School Sports 50 Online Proof Only" and Shoot_Log||PRODUCTION_initialrun::date060Cropping≠"";"QC";
	Shoot_Log::programActual="School Sports 50 Online Proof Only" and Shoot_Log||PRODUCTION_initialrun::date030Color≠"";"Cropping";
	Shoot_Log::programActual="School Sports 50 Online Proof Only" and Shoot_Log||PRODUCTION_initialrun::date020Upload≠"";"Color";
	Shoot_Log::programActual="School Sports 50 Online Proof Only" and Shoot_Log||PRODUCTION_initialrun::date040DataEntry≠"";"Upload";
	Shoot_Log::programActual="School Sports 50 Online Proof Only" and Shoot_Log||PRODUCTION_initialrun::date010bIn≠"";"Data";
	Shoot_Log::programActual="School Sports 50 Online Proof Only" and Shoot_Log||PRODUCTION_initialrun::date010In≠"";"Receiving";

	Shoot_Log||PRODUCTION_initialrun::date170Packed≠"";"Shipping";
	Shoot_Log||PRODUCTION_initialrun::date165cPkgPrinted≠"";"Packing";
	Shoot_Log||PRODUCTION_initialrun::date150bRipQC≠"";"Printing";
	Shoot_Log||PRODUCTION_initialrun::date150PackageRip≠"";"Post Rip QC";
	Shoot_Log||PRODUCTION_initialrun::date140GreenScreen≠"";"Ripping";
	Shoot_Log||PRODUCTION_initialrun::date130Retouching≠"" and Program Name | Actual Program::bgko = "Yes";"BG-KO";
	Shoot_Log||PRODUCTION_initialrun::date130Retouching≠"";"Ripping";
	Shoot_Log||PRODUCTION_initialrun::date030Color≠"";"Retouch";
	Shoot_Log||PRODUCTION_initialrun::date070QC≠"";"Color";
	Shoot_Log||PRODUCTION_initialrun::date120OnlineOrders≠"";"QC";
	Shoot_Log||PRODUCTION_initialrun::date110OrderEntry≠"";"Online";
	Shoot_Log||PRODUCTION_initialrun::date060Cropping≠"" and moneyInPlantDate01="" and Shoot_Log::shootNotes="No Orders";"Order Entry";
	Shoot_Log||PRODUCTION_initialrun::date601Rescan≠"" and Shoot_Log||PRODUCTION_initialrun::date060Cropping≠"";"Order Entry";
	Shoot_Log||PRODUCTION_initialrun::date060Cropping≠"" and Shoot_Log::shootNotes≠"No Orders" and moneyInPlantDate01≠"";"Scanning";
	Shoot_Log||PRODUCTION_initialrun::date060Cropping≠"" and Shoot_Log::shootNotes≠"No Orders" and moneyInPlantDate01="";"Waiting On Orders";
	Shoot_Log||PRODUCTION_initialrun::date020Upload≠"";"Cropping";
	Shoot_Log||PRODUCTION_initialrun::date040DataEntry≠"";"Upload";
	Shoot_Log||PRODUCTION_initialrun::date010bIn≠"";"Data";
	Shoot_Log||PRODUCTION_initialrun::date010In≠"";"Receiving";
	"Not In"
	)
```
#### SQL Expression:
lorem ipsum

***

## currentStageFinal
```SQL
	Case(
	Shoot_Log::notTrackable = "Yes" ; "Not Trackable" ;

	Shoot_Log::omitFromProduction ≠ "" ; "OMIT" ;

	Kickback ToDo::zstDepartment ≠ "" ; GetValue ( Kickback ToDo::zstDepartment ; 1 ) ;

	Shoot_Log::shootType = "Senior" or Shoot_Log::shootType = "SE Add-on" ; currentSeniorStage ;
	Shoot_Log::shootType = "CG" ; currentCCGStage ;
	Shoot_Log::shootType = "Sports" ; currentSportsStage ;
	Shoot_Log::shootType = "Faculty" ; currentFacultyStage ;
	Program Name | Actual Program::programType = "Prepay" ; currentPrepayStage ;
	Program Name | Actual Program::programType = "Proof" ; currentProofStage ; 
	Program Name | Actual Program::programType = "Speculative" ; currentSpecStage ; 
	Program Name | Actual Program::__pktProgramName = "Services Only (No Packages)" ; currentSvcOnlyStage ; 
	currentAltStage
	)
```
#### SQL Expression:
lorem ipsum

***

# currentStageKits
### Fields Used:
| shoot_log          | 
|--------------------|
| kitBuiltDate       |
| kitPrintedDate     |
| SchedulingPrepDate |
### Filemaker:
```SQL
	Case (
	kitBuiltDate ≠ "" ; "Shipping" ;
	kitPrintedDate ≠ "" ; "Building" ;
	SchedulingPrepDate ≠ "" ; "Printing" ;
	"Prepping"
	)
```
#### SQL Expression:
lorem ipsum

***

# currentSvcOnlyStage
### Fields Used:
| production_log     | production_log (cont) |
|--------------------|-----------------------|
| date170Packed      | date010In             |
| date165cPkgPrinted |                       |
| date150bRipQC      |                       |
| date150PackageRip  |                       |
| date070QC          |                       |
| date060Cropping    |                       |
| date030Color       |                       |
| date040DataEntry   |                       |
| date020Upload      |                       |
| date010bIn         |                       |
### Filemaker:
```SQL
	Case ( 
	Shoot_Log||PRODUCTION_initialrun::date170Packed≠"";"Shipping";
	Shoot_Log||PRODUCTION_initialrun::date165cPkgPrinted≠"";"Packing";
	Shoot_Log||PRODUCTION_initialrun::date150bRipQC≠"";"Printing";
	Shoot_Log||PRODUCTION_initialrun::date150PackageRip≠"";"Post Rip QC";
	Shoot_Log||PRODUCTION_initialrun::date070QC≠"";"Ripping";
	Shoot_Log||PRODUCTION_initialrun::date060Cropping≠"";"QC";
	Shoot_Log||PRODUCTION_initialrun::date030Color≠"";"Cropping";
	Shoot_Log||PRODUCTION_initialrun::date040DataEntry≠"";"Color";
	Shoot_Log||PRODUCTION_initialrun::date020Upload≠"";"Data";
	Shoot_Log||PRODUCTION_initialrun::date010bIn≠"";"Upload";
	Shoot_Log||PRODUCTION_initialrun::date010In≠"";"Receiving";
	"Not In"
	)
```
#### SQL Expression:
lorem ipsum

***
