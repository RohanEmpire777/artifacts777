## nexcc-1: commission compass – end-to-end api flow for agent sale and commission approval

**summary:** commission compass – end-to-end api flow for agent sale and commission approval

**status:** to do

**assignee:** dinesh

**reporter:** dinesh

**created:** 2025-06-04t20:07:30.163+0530

**updated:** 2025-06-10t10:10:24.749+0530

**description:**

as a product manager, i want commission compass to support an end-to-end api-driven flow where an agent logs in, selects a product, creates a sale, and an admin processes and approves the commission, so that the commission lifecycle is seamless, automated, and fully auditable for admins.

**actors:**

*   agent
*   admin

**scope / ask:**

this story covers the api-driven lifecycle for a single sale, including:

*   agent login and authentication
*   product search and selection
*   sale creation and status validation
*   admin login and authentication
*   commission processing and calculation
*   commission approval workflow
*   agent validation of approved commission

the goal is to ensure the entire process, from sale to commission approval, is api-driven, robust, and transparent for both agents and admins.

**api resources:**

swagger ui - [http://13.49.29.196:5000/api-docs/](http://13.49.29.196:5000/api-docs/)

swagger json - [13.49.29.196:5000/swagger.json](http://13.49.29.196:5000/swagger.json)

**acceptance criteria:**

*   **agent login & product selection**
    *   given an agent has valid credentials,
    *   when the agent logs in via `/api/auth/login`,
    *   then extract the token, user.id, user.name for subsequent api calls.
    *   given a valid token,
    *   when the agent searches a product via `/api/product`,
    *   then extract the product details i.e., id & name for sale creation

*   **sale creation & status validation**
    *   given a valid product & agent details like productid=id, productname=name, agentid=user.id, agentname=user.name extracted from previous steps
    *   when the agent creates a sale via `/api/sale`,
    *   then extract the sale id i.e., id,
    *   and verify the sale status is set to "pending".

*   **admin login & commission processing**
    *   given an admin has valid credentials,
    *   when the admin logs in via `/api/auth/login`,
    *   then an token is returned for subsequent api calls.
    *   given a valid sale id,
    *   when the admin processes the commission via `/api/sales-commissions/[id]/process`,
    *   then a commission id i.e commission.id is returned, and the commission status is set to "calculated".

*   **commission approval**
    *   given a valid commission.id,
    *   when the admin approves the commission via `/api/commissions/[[commission.id]]/status`,
    *   then the commission status is updated to "approved".

*   **agent validation of approved commission**
    *   given the agent logs in again and has a valid token,
    *   when the agent views commissions via `/api/commissions`,
    *   then the agent can see the approved commission and validate the commission amount for the product sold.