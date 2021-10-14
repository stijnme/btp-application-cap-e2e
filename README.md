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

