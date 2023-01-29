# App Fiddle

<details markdown>

&nbsp;

<summary>Welcome to the Flask/SQLAlchemy “App Fiddle”</summary>

You've perhaps used JS Fiddle to explore JavaScript and HTML.  With the power of Codespaces, we can now provide a "fiddle" for a *complete application.*

Use this ***Application Fiddle*** to learn Flask/SQLAlchemy in Codespaces.  You have 3 running apps - execute them, explore the code, alter them (e.g., create endpoints, issue queries), use the debugger, etc.

The Key Technology Concepts (at end) is an inventory of essential skills for creating Flask/SQLAlchemy systems.  Each are illustrated here.

These projects all use the [Northwind Sample Database](https://valhuber.github.io/ApiLogicServer/Sample-Database/).  Other databases are also provided in Next Steps.

Start with the first application - a Basic Flask/SQLAlchemy App.

Then, discover **API Logic Server** - an Open Source CLI to create executable projects, **instantly,** with a single command.  Its open source, and **open** technology: customize projects in your IDE, including unique spreadsheet like rules for logic and security - 40X more concise than manual code.

</details>

&nbsp;

<details markdown>

&nbsp;

<summary>1. Basic App: Flask / SQLAlchemy -- flexible, but slow</summary>

This illustrates a typical framework-based approach for creating projects - a minimal project for seeing core Flask and SQLAlchemy services in action.

Execute using the Run and Debug (*1. Basic App: Flask / SQLAlchemy*), and test with `cURL`.  The relevant code is `api/end_points.py`.

<details markdown>

<summary> Show me how </summary>

&nbsp;

To run the basic app:

1. Click **Run and Debug** (you should see *1. Basic App: Flask / SQLAlchemy*), and the green button to start the server

2. Copy the `cURL` text, and paste it into the `bash`/`zsh` window

<figure><img src="https://github.com/valhuber/apilogicserver/wiki/images/tutorial/1-basic-app.png?raw=true"></figure>

</details>

Frameworks are flexible, and leverage your existing dev environment (IDE, git, etc).  But the manual effort is time-consuming, and complex.  This minimal project **does not provide:**

* an API endpoint for each table

* a User Interface

* any security, or business logic (multi-table derivations and constraints).


</details>

&nbsp;

</details>


<details markdown>


<summary>2. API Logic Project: Instant, Open</summary>

&nbsp;

Instead of frameworks, we might employ a Low Code approach.  Low Code tools provide excellent custom user interfaces.  However, these often require extensive screen painting, and typically require a proprietary IDE.

The *API Logic Project* app provides an alternative, creating an entire project by reading your schema.  This approach is:

* **Instant:** faster than Low Code screen painting, with instant APIs and Admin User Interfaces:

  * **API:** an endpoint for each table, with filtering, sorting, pagination and related data access.  Swagger is automatic.

  * **Admin UI:** multi-page / multi-table apps, with page navigations, automatic joins and declarative hide/show.  It executes a yaml file, so basic customizations do not require HTML or JavaScript background.

      * Custom UIs can be built using your tool of choice (React, Angular, etc), using the API

* **Open:** a fully open approach:

  * **Open Source:** install with pip or docker

  * **Open Technology:** using standard IDEs such as VSCode or PyCharm.  All of the key technology concepts you mastered above (Flask, SQLAlchemy) still fully apply.

This application was created using the API Logic Server CLI (Command Language Interface), with 1 command:

```bash
ApiLogicServer create --project_name=ApiLogicProject --db_url=nw-  # use Northwind, no customizations
```

Execute: **Run and Debug >> *2. API Logic Server: Instant, Open***, and then  **Ports > Admin App > globe**

&nbsp;

<details markdown>

<summary> Show me how </summary>

&nbsp;

To run the ApiLogicProject app:

1. Click **Run and Debug**, select **2. API Logic Server: Instant, Open**, and click the green button to start the server

2. Click the **Ports** tab

3. Click the (top "Admin App" row) **globe** to start your Browser

    * Don't spend too much time exploring the app, we'll see a much better version in just a moment...


<figure><img src="https://github.com/valhuber/apilogicserver/wiki/images/tutorial/2-apilogicproject.png?raw=true"></figure>

</details>

&nbsp;

> Key Takeway: you will achieve this level of schema-driven automation for your own databases on initial creation. 

&nbsp;

An instant Admin App and API are a great start, but there are some serious short-comings:

* **No security -** no login authentication

* **No logic -** multi-table derivations and constraints for save logic

    * For example, open **Customers**, **double-click first Order**, and **delete the first Order**.  Re-click Customer from the left nav menu - it should have reduced the customer's balance from 2102, but it's unchanged.   That's because there is *no logic...*

Let's see how these are addressed, in the next section.

</details>

&nbsp;

<details markdown>


<summary>3. Api Logic Project Logic: Unique Spreadsheet-like Rules -- 40X More Concise</summary>

&nbsp;

A running API and UI are a great start, but completing the project still requires logic and security.  This can be as much as half the effort, so we really haven't achieved "Low Code" until these are addressed.

A unique feature of API Logic Server is provision for:

* **Business Logic Automation:** using unique spreadsheet-like rules for multi-table derivations and constraints, extensible with Python 🏆

* These are **declared in *your IDE,*** with full support for code completion, logging, and debugging

This application is a clone of the prior example, customized in VSCode:

* **API:** additional endpoints are defined in ```ApiLogicProject_Logic/api/customize_api.py```

* **Logic:** the project now implements logic and security

* **User Interface:** the app now has help text that walks you through the key features

You can run the app.  First, stop the server using the red "stop" button).  Then, restart with the same procedure as Step 2, above, choosing ***3. API Logic Project: Logic***.  Observe the customizations:

1. Click Category - you need to **login** now (user u1, password p).  That's because authentication has been activated.

2. Categories has fewer rows per **multi-tenant Grant logic** in ```ApiLogicProject_Logic/security/declare_security.py```

3. The app now shows **help text** to introduce its features per updates in ```ApiLogicProject/ui/admin/admin.yaml```

4. Our Delete Order test adjusts the customer balance, since we how have **business logic** in ```ApiLogicProject_Logic/logic/declare_logic.py```

You can use VSCode to *diff* these from their originals in the *ApiLogicProject*.

Use the [```Detailed Tutorial```](ApiLogicProject/readme.md) to further explore this app.

&nbsp;

> **Key Take-aways** <br>1. **Instant** project creation<br>2. Spreadsheet-like **Rules**<br>3. Fully Customizable in **your IDE**.


</details>
&nbsp;

<details markdown>

&nbsp;

<summary>Next Steps: new projects</summary>


As shown above, it's easy to create projects with a single command.  To help you explore, ApiLogicServer provides several prepackaged sqlite databases.  For example, create a project for this 1 table database:

```bash
cd app_fiddle
ApiLogicServer create --project_name=todo --db_url=todo
```
You can also try these other examples (be sure to `cd tutorial`; use the name below for both the _project_name_ and the _db_url_):

* **chinook** - albums and artists
* **classicmodels** - customers and orders

Launch configurations have been pre-created, then re-execute the Admin app as above.


> Next, try it on your own databases: if you have a database, you can have an API and an Admin app in minutes.

</details>

&nbsp;

<p align="center">
  <h2 align="center">Key Technology Concepts</h2>
</p>
<p align="center">
  Select a skill of interest, and<br>Click the link to see sample code
</p>
&nbsp;


| Tech Area | Skill | Basic App Example | APILogicProject Logic Example | Notes   |
|:---- |:------|:-----------|:--------|:--------|
| __Flask__ | Setup | [```flask_basic.py```](Basic_App/flask_basic.py) |  [```api_logic_server_run.py```](ApiLogicProject/api_logic_server_run.py) |  |
|  | Events | |  [```ui/admin/admin_loader.py```](ApiLogicProject_Logic/ui/admin/admin_loader.py) |  |
| __API__ | Create End Point | [```api/end_points.py```](Basic_App/api/end_points.py) | [```api/customize_api.py```](ApiLogicProject_Logic/api/customize_api.py) |  see `def order():` |
|  | Call endpoint |  | [```test/.../place_order.py```](ApiLogicProject_Logic/test/api_logic_server_behave/features/steps/place_order.py) | |
| __Config__ | Config | [```config.py```](ApiLogicProject_Logic/config.py) | | |
|  | Env variables |  | [```config.py```](ApiLogicProject_Logic/config.py) | os.getenv(...)  |
| __SQLAlchemy__ | Data Model Classes | [```database/models.py```](ApiLogicProject_Logic/database/models.py) |  |  |
|  | Read / Write | [```api/end_points.py```](Basic_App/api/end_points.py) | [```api/customize_api.py```](ApiLogicProject_Logic/api/customize_api.py) | see `def order():`  |
|  | Multiple Databases |  | [```database/bind_databases.py```](ApiLogicProject_Logic/database/bind_databases.py) |   |
|  | Events |  | [```security/system/security_manager.py```](ApiLogicProject_Logic/security/system/security_manager.py) |  |
| __Logic__ | Business Rules | n/a | [```logic/declare_logic.py```](ApiLogicProject_Logic/logic/declare_logic.py) | ***Unique*** to API Logic Server  |
| __Security__ | Multi-tenant | n/a | [```security/declare_security.py```](ApiLogicProject_Logic/security/declare_security.py) |   |
| __Behave__ | Testing |  | [```test/.../place_order.py```](ApiLogicProject_Logic/test/api_logic_server_behave/features/steps/place_order.py) |  |
| __Alembic__ | Schema Changes |  | [```database/alembic/readme.md```](ApiLogicProject_Logic/database/alembic/readme.md) |   |
| __Docker__ | Dev Env | | [```.devcontainer/devcontainer.json```](.devcontainer/devcontainer.json) | See also "For_VS_Code.dockerFile" |
|  | Containerize Project |  | [```devops/docker/build-container.dockerfile```](ApiLogicProject_Logic/devops/docker/build-container.dockerfile) |  |