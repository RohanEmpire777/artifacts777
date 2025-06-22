summary of jira story (nexcc-10000000000) and swagger api

### business scenarios:

*   **agent sale:** an agent logs into the system, selects a product, and creates a sale via api.
*   **commission processing:** an admin logs in, processes the agent's commission based on the sale, and approves it via api.
*   **commission validation:** the agent logs in again to view and validate the approved commission amount.

### context:

the "commission compass" aims to create a seamless, automated, and fully auditable end-to-end api flow for agent sales and commission approvals. this involves multiple actors (agents and admins) interacting with the system through a series of api calls.  the existing swagger documentation provides information for accessing the different apis, but more api definitions may exist beyond what is described in the story.

### scope:

*   **api-driven lifecycle:** covers the entire process from agent login and product selection to commission approval, all driven by api calls.
*   **specific api endpoints:** includes specific endpoints such as:
    *   `/api/auth/login` (agent and admin)
    *   `/api/product` (product search)
    *   `/api/sale` (sale creation)
    *   `/api/sales-commissions/[id]/process` (commission processing)
    *   `/api/commissions/[commission.id]/status` (commission approval)
    *   `/api/commissions` (agent commission view)
*   **data validation:** ensures the entire process is robust and transparent for both agents and admins through api-driven processes.
*   **authentication & authorization:** implementing authentication and authorization for agents and admins.

**api gateway (based on swagger analysis)**

the nexturn api gateway handles creation and modification of sales records, and the agent commission flow documented in the jira story, and may require the agent commission flow documented in the jira story.

### scope:

*   **data models:** defines `saleupsertpayload` and `saleupsertresponse` for sales data.
*   **authentication:** uses jwt bearer authentication.
*   **potential integrations:** integrates with product, agent, agency management systems, payment processing, reporting/analytics, crm, and policy management systems.

input data