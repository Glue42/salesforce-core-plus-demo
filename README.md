# Demo app of Salesforce Connector for the Core+ Seed

# Overview

The app is a single page Vanilla JS application.  
It provides the following functionality/screens:

- 2 Actions for testing the Salesforce plug-in:
  - SyncAccount
  - SyncContact
- 3 Contacts and 1 Account from 6 DEV Orgs that belong to the Glue42 Organisation

# Quick Start

## Prerequisites

- [Salesforce CRM Org](https://login.salesforce.com/)
- License key for [**Glue42 Core+**](https://glue42.com/core-plus/). For more details, see the [Configuration > Licensing](https://github.com/Glue42/core-plus-seed/blob/master/readme.md#licensing) section.*
- NodeJS version > 18.13.0
- Git version > 1.65 ([more](https://stackoverflow.com/a/4438292/2848256))

## How to setup

1. Run the following commands in the bash terminal:

```bash
git clone --branch master --recursive git@github.com:Glue42/core-plus-seed.git .\test-sf-demo1
cd test-sf-demo1/
git submodule add https://github.com/Glue42/salesforce-core-plus-demo.git
```

2. Add 2 new local applications in config.json. Please visit [Adding Apps](https://github.com/Glue42/core-plus-seed/blob/master/readme.md#adding-apps) for more details.

```json
                {
                    "title ": "Salesforce Demo App",
                    "type": "window",
                    "name": "salesforce_demo",
                    "details": {
                        "url": "http://localhost:5000/"
                    },
                    "customProperties": {
                        "includeInCanvas": true,
                        "includeInWorkspaces": true,
                        "folder": "Sales Demo",
                        "appManagerOrder": 150

                    }
                },
                {
                    "title": "Salesforce login page",
                    "type": "window",
                    "name": "salesforce_login",
                    "icon": "http://localhost:4200/resources/icons/sf.ico",
                    "hidden": true,
                    "details": {
                        "url": "https://login.salesforce.com/",
                        "top": 25,
                        "left": 800,
                        "height": 800,
                        "width": 780,
                        "mode": "tab",
                        "sfMode": true,
                        "autoInjectAPI": {
                            "enabled": true,
                            "autoInit": true
                        },
                        "preloadScripts": [
                            "http://localhost:4200/preload-scripts/salesforce.js"
                        ]
                    },
                    "customProperties": {
                        "includeInCanvas": true,
                        "includeInWorkspaces": true,
                        "folder": "Sales Demo",
                        "appManagerOrder": 150
                    }
                },
```

3. Add the app as a new client. For more information visit [Add New Clients](https://github.com/Glue42/core-plus-seed/blob/master/readme.md#add-new-clients)

```javascript
const clientsSources = [
    "workspace-platform/",
    "react-client/",
    //...
    "salesforce-core-plus-demo/", // newly added
];
```

4. Execute in terminal (as it's described in [Getting Started](https://github.com/Glue42/core-plus-seed#getting-started))

```bash
npm install
npm run bootstrap
npm start
```

5. Wait for the project to start in the browser, then click on `+` to open the new apps:
    1. First open `salesforce_demo`.
    2. Then open `Salesforce login page`, then eject it in a new window.
