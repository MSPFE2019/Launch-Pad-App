# Launch Pad App
Launch Pad App is hub for launching Apps and websites.
------------



### App Onstart

------------


#### Variables


- Set(**varUseremail**, User().Email)
- Set(**varDept** , Office365Users.UserProfile(User().Email).Department) : Get User Department
- Set(**varCompany** , Office365Users.UserProfile(User().Email).CompanyName) : Get User CompanyName
- Set(**varDomain** , Last(Split(User().Email,"@")).Result) : Get User Email Domain
- Set(**appTitle**,"Launch Pad") : App Title
- Set(**var_TopNav** , ColorValue("#988181")) 
- Set(**app_ID**, "caec314c-4233-40ab-b3df-0e077ae82612") : Launch Pad App ID number


------------


#### Collections


- ClearCollect(*colAppType*,{AppType:"Power App"},{AppType:"Website"},{AppType:"SharePoint Site"},{AppType:"VDI"}) : App Type for Dropdown
- ClearCollect(*colLicenseType*,{AppType:"Standard"},{AppType:"Premium"},{AppType:"No License"}) : License Type for Dropdown
- ClearCollect(*colAudience*,{AppType:"Agency"},{AppType:"Department"},{AppType:"Statewide"}) : Agency Type for Dropdown
- ClearCollect(*col_allActiveApps*,Sort(Filter(Filter('Company App Catalog',AppStatus.Value = "Active"),AgencyFilter = Text(varCompany) Or AgencyFilter = Text(varDept) Or Text(varDomain) = AgencyFilter Or Audience = "Statewide"),Title)) : Filter List based on your information and App Status
- ClearCollect(*col_CatNew*,{AppCat:"Training"},{AppCat:"Admin"},{AppCat:"HR"},{AppCat:"Org Apps"}) : App Category for Dropdown
- );
- ClearCollect(*col_Cat*,Distinct('Company App Catalog',Category) : App Category list for gallery on main page

------------

