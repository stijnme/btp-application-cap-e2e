# Getting Started

Welcome to your new project.

It contains these folders and files, following our recommended project layout:

File or Folder | Purpose
---------|----------
`app/` | content for UI frontends goes here
`db/` | your domain models and data go here
`srv/` | your service models and code go here
`package.json` | project metadata and configuration
`readme.md` | this getting started guide


## Next Steps

- Open a new terminal and run `cds watch` 
- (in VS Code simply choose _**Terminal** > Run Task > cds watch_)
- Start adding content, for example, a [db/schema.cds](db/schema.cds).

*Update*: To start the `mitigation` app, start in a second terminal:
```
cd app/mitigations/
ui5 serve
```

## Learn More

Learn more at https://cap.cloud.sap/docs/get-started/.

# Tutorials
## Create a CAP-Based Application
Source: [Create a CAP-Based Application](https://developers.sap.com/tutorials/btp-app-create-cap-application.html)

Init cds app:

`cds init`

Install node modules:

`npm i` 

Start CAP server:

`cds watch` 

### Create OData Service
Copied schema and service file:

```
cp ../tutorial/templates/cap/create-service/db/schema.cds db/
cp ../tutorial/templates/cap/create-service/srv/risk-service.cds srv/
```

Copied file with mockup-data:

`cp -R ../tutorial/templates/cap/create-service/db/data/ db/`

## Create an SAP Fiori Elements-Based UI
Source: [Create an SAP Fiori Elements-Based UI](https://developers.sap.com/tutorials/btp-app-create-ui-fiori-elements.html)

### Generate the UI with an SAP Fiori elements template
Start the `Fiori: Open Application Generator`, choose following options:
- Application Type: `SAP Fiori elements`
- Floorplan: `List Report Object Page`
- Date source: `Use a local CAP Project`
- CAP Project folder path: `../cpapp`
- OData service: `RiskService`
- Main entity: `Risks`
- Project attributes:
    - Module name: `risks`
    - Application title: `Risks`
    - Application namespace: `ns`
    - Description: `Risks`

### Modify the UI with OData annotations
`cp ../tutorial/templates/cap/fiori-elements-app/srv/risks-service-ui.cds srv/`


## Add Business Logic to Your Application
Source: [Add Business Logic to Your Application](https://developers.sap.com/tutorials/btp-app-cap-business-logic.html)
### Add custom code
Depending on the value of the property `impact`, the custom code changes the value of the property `criticality`.

`cp ../tutorial/templates/cap/business-logic/srv/risk-service.js srv/`

## Create a UI Using Freestyle SAPUI5
Source: [Create a UI Using Freestyle SAPUI5](https://developers.sap.com/tutorials/btp-app-create-ui-freestyle-sapui5.html)

### SAP Fiori elements application vs. freestyle UI5 application


### Creating the application
Start the `Fiori: Open Application Generator`, choose following options:
- Application Type: `SAPUI5 freestyle`
- Floorplan: `SAP Fiori Worklist Application`
- Date source: `Use a local CAP Project`
- CAP Project folder path: `../cpapp`
- OData service: `RiskService`

Entity selection:
    - Object collection: `mitigations`
    - Object collection key: `ID`
    - Object ID: `ID`
    - Object number: `None`
    - Object unit of measure: `None`

- Project attributes:
    - Module name: `mitigations`
    - Application title: `Mitigations`
    - Application namespace: `ns`
    - Description: `Mitigations`

### Starting the application
Started the app (from the root folder) with:
`cds watch`

Updated views and bindings for Worklist and Object views.

### (Optional) SAPUI5 serve
Not really needed, but `UI5` tooling has a few more features:
- You can run multiple servers at a time (cds watch can only run once).
- A live reload (that is, automatic browser refresh on saving) of all the UI changes.
- Loading local SAPUI5 resources from dependencies.
- Serve middleware.
    - Proxy for backend service
    - Cache behavior for SAPUI5 resources
    - Theme Build on-the-fly for library development
    - Transpiling middleware

Added `ui5-middleware-livereload` in `package.json` and `ui5.yaml` of the `mitigations` app.
Ran `npm i` in the `mitigations` app folder.

Started in seperate terminals:
- `cds watch` in the root folder
- `ui5 serve` in the `mitigations` folder


## Add More Than One Application to the Launch Page
Source: [Add More Than One Application to the Launch Page](https://developers.sap.com/tutorials/btp-app-launchpage.html)
In the `app/risks/webapp` folder:
`git mv index.html ../../`

To move the `index.html` file up into the `app` folder.
Adjusted the application script in `index.html`.

Renamed:
`cd ../..`
`git mv index.html launchpad.html`

Test:
[http://localhost:4004/launchpage.html#Shell-home](http://localhost:4004/launchpage.html#Shell-home)

## Implement Roles and Authorization Checks In CAP
Source: [Implement Roles and Authorization Checks In CAP](https://developers.sap.com/tutorials/btp-app-cap-roles.html)
### Enable authentication support
Run in the project root folder:
`npm install passport`

### Adding CAP role restrictions to entities
Added role restrictions on `Risks` and `Mitigations` entities in `risk-service.cds`.


### Add Users for local testing
`cp ../tutorial/templates/cap/roles/.cdsrc.json .`

Restarted: `cds watch`

It is now possible to login with an account specified in `.cdsrc.json`.

## Deploy Your CAP Application on SAP BTP Cloud Foundry Environment
### Prepare for SAP BTP Development
Source: [Prepare for SAP BTP Development](https://developers.sap.com/tutorials/btp-app-prepare-btp.html)

In this exercise, we used the SAP BTP trial environment.
The SAP tutorial gives a good quick overview on what is needed to setup a live account on SAP BTP.

Lookup the `Cloud Foundry Environment` settings in the subaccount.

 Log on from the command line:
 `cf api <API Endpoint of your landscape>`

Remark: couldn`t find the correct password. Fixed with login in via sso:
```
cf login  --sso
API endpoint: https://api.cf.us10.hana.ondemand.com/

Temporary Authentication Code ( Get one at https://login.cf.us10.hana.ondemand.com/passcode ):
```
Surfed to the given URL and retrieved authentication code. After pasting this code in the terminal:
```
Authenticating...
OK
```

## Set Up the SAP HANA Cloud Service
Source: [Set Up the SAP HANA Cloud Service](https://developers.sap.com/tutorials/btp-app-hana-cloud-setup.html)
### Add SAP HANA client and configuration to your project
```
cds add hana
```

### Create an SAP HANA Cloud service instance
Created SAP HANA database via the SAP BTP Cockpit.
Instance name: `cpapp`

Remark:
```
Your SAP HANA Cloud service instance will be automatically stopped overnight, according to the server region time zone. That means you need to restart your instance every day before you start working with it.
```



