# Launch Pad App
Launch Pad App is a hub for launching Power Apps, websites, and any url based Application. Launch Pad can launch any url based application.
------------
[![Launch Pad App](https://github.com/MSPFE2019/Launch-Pad-App/blob/main/LaunchPad_%20Main.png "Launch Pad App")](https://github.com/MSPFE2019/Launch-Pad-App/blob/main/LPA_HomeScreen.png "Launch Pad App")


------------


### App Onstart

------------


#### Variables


- Set(**varDept** , Office365Users.UserProfile(User().Email).Department) : Get User Department used by AgencyFilter Field
- Set(**varCompany** , Office365Users.UserProfile(User().Email).CompanyName) : Get User CompanyName used by AgencyFilter Field
- Set(**varDomain** , Last(Split(User().Email,"@")).Result) : Get User Email Domain used by AgencyFilter Field
- Set(**appTitle**,"Launch Pad") : App Title


------------


#### Collections


- ClearCollect(*colAppType*,{AppType:"Power App"},{AppType:"Website"},{AppType:"SharePoint Site"},{AppType:"VDI"}) : App Type for Dropdown
- ClearCollect(*colLicenseType*,{AppType:"Standard"},{AppType:"Premium"},{AppType:"No License"}) : License Type for Dropdown
- ClearCollect(*colAudience*,{AppType:"Agency"},{AppType:"Department"},{AppType:"Statewide"}) : Agency Type for Dropdown
- ClearCollect(*col_allActiveApps*,Sort(Filter(Filter('Company App Catalog',AppStatus.Value = "Active"),AgencyFilter = Text(varCompany) Or AgencyFilter = Text(varDept) Or Text(varDomain) = AgencyFilter Or Audience = "Statewide"),Title)) : Filter List based on your information and App Status
	- Notes: If audience is not **Statewide**, user information must match AgencyFilter field
- ClearCollect(*col_CatNew*,{AppCat:"Training"},{AppCat:"Admin"},{AppCat:"HR"},{AppCat:"Org Apps"}) : App Category for Dropdown
- ClearCollect(*col_Cat*,Distinct('Company App Catalog',Category) : App Category list for gallery on main page

------------
### App Components
- [Launch Pad App](https://github.com/MSPFE2019/Launch-Pad-App/blob/main/LaunchPadApp_20230123170529.zip "Launch Pad App") - Canvas App
- [CreateList_LaunchPadApp](https://github.com/MSPFE2019/Launch-Pad-App/blob/main/CreateList_LaunchPadApp_20221229035826.zip "CreateList_LaunchPadApp") - Power Automate to create list for Launch Pad App
- [Launch Pad App Solution](https://github.com/MSPFE2019/Launch-Pad-App/blob/main/LaunchPadApp_1_0_0_1.zip "CreateList_LaunchPadApp") - Solution  for Launch Pad App ( Power App, Create List Power Automate, Power Automate to use the version information)



------------
### Install Components
1. Download App Components listed above.
2. Create SharePoint Site and grant "edit" access to the SharePoint Site.
3. Open Power Automate in your browser and select your destination Power Platform Environment.
4. Import CreateList_LaunchPadApp.
5. Turn on CreateList_LaunchPadApp and run, provide the url for the Launch Pad App site.
	- This will create the LaunchPadApp List on your site
6. Open Power App in your browser and select your destination Power Platform Environment.
7. Edit the App and remove the data connection for SharePoint and replace with site
8. Check app for any errors
9. Publish and Share app with your users.

------------
#### To import a solution:

2. Sign into Power Apps and select Solutions from the left navigation.

3. On the command bar, select Import.

4. [Launch Pad App](https://github.com/MSPFE2019/Launch-Pad-App/blob/main/LaunchPadApp_1_0_0_1.zip "Launch Pad App"), Click to download solution.

5. On the Import a solution page, select Browse to locate the compressed (.zip or .cab) file that contains the solution you want to import.

6. Select Next.

7. Information about the solution is displayed. By default, in the Advanced settings section, if SDK messages and flows exist in the solution, they will be imported. Clear the Enable SDK messages and flows included in the solution option if you want them to import in an inactive state.

9. If your solution contains connection references, you’ll be prompted to select the connections you want. If a connection does not already exist, create a new one. Select Next.

10. If missing dependencies are detected in the target environment, a list of the dependencies is presented. In environments where the required package version is available for import in the target environment, a link to resolve the dependency is presented. Selecting the link takes you to the Power Platform admin center where you can install the application update. After the application update is completed, you can start the solution import again.

11. Select Import.


![Loading Screen](https://github.com/MSPFE2019/Launch-Pad-App/blob/main/LPA_LoadingScreen.png "Loading Screen")

------------
[![MainScreen](https://github.com/MSPFE2019/Launch-Pad-App/blob/main/LPA_HomeScreen.png "MainScreen")](https://github.com/MSPFE2019/Launch-Pad-App/blob/main/LPA_HomeScreen.png "MainScreen")

------------
[![Maint Screen](https://github.com/MSPFE2019/Launch-Pad-App/blob/main/LPA_MaintScreen.png "Maint Screen")](https://github.com/MSPFE2019/Launch-Pad-App/blob/main/LPA_MaintScreen.png "Maint Screen")
