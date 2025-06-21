Okay, I understand. Now that you have the content for the JIRA story in Markdown format, you need to include that content *after* the `store to github NEXCC-1_story.md` command.

So, the correct command should look like this:

```
store to github NEXCC-1_story.md
# Commission Compass – End-to-End API Flow for Agent Sale and Commission Approval (NEXCC-1)

**Status:** To Do
**Assignee:** Dinesh

## Description

As a Product Manager, I want Commission Compass to support an end-to-end API-driven flow where an agent logs in, selects a product, creates a sale, and an admin processes and approves the commission, So that the commission lifecycle is seamless, automated, and fully auditable for admins.

**Actors:**

*   Agent
*   Admin

**Scope / Ask:**

This story covers the API-driven lifecycle for a single sale, including:

*   Agent login and Authentication
*   Product search and selection
*   Sale creation and status validation
*   Admin login and Authentication
*   Commission processing and calculation
*   Commission approval workflow
*   Agent validation of approved commission

The goal is to ensure the entire process, from sale to commission approval, is API-driven, robust, and transparent for both agents and admins.

**API Resources:**

Swagger UI - [http://13.49.29.196:5000/api-docs/](http://13.49.29.196:5000/api-docs/)
Swagger Json - [13.49.29.196:5000/swagger.json](http://13.49.29.196:5000/swagger.json)

## Acceptance Criteria

**Agent Login & Product Selection**

*   Given an agent has valid credentials,
*   When the agent logs in via /API/auth/login,
*   Then extract the token, [user.id](http://user.id), user.name for subsequent API calls.
*   Given a valid token,
*   When the agent searches a product via /API/product,
*   Then extract the product details i.e., id & name for Sale Creation

**Sale Creation & Status Validation**

*   Given a valid product & agent details like productId=id, productName=name, agentId=[user.id](http://user.id), agentName=user.name extracted from previous steps
*   When the agent creates a sale via /API/sale,
*   Then extract the sale id i.e., id,
*   And verify the sale status is set to "pending".

**Admin Login & Commission Processing**

*   Given an admin has valid credentials,
*   When the admin logs in via /API/auth/login,
*   Then an token is returned for subsequent API calls.
*   Given a valid Sale ID,
*   When the admin processes the commission via /API/sales-commissions/[id]/process,
*   Then a Commission ID i.e commission.id is returned, and the commission status is set to "calculated".

**Commission Approval**

*   Given a valid [commission.id](http://commission.id),
*   When the admin approves the commission via /API/commissions/[[commission.id](http://commission.id)]/status,
*   Then the commission status is updated to "approved".

**Agent Validation of Approved Commission**

*   Given the agent logs in again and has a valid token,
*   When the agent views commissions via /API/commissions,
*   Then the agent can see the approved commission and validate the commission amount for the product sold.

## Technical Requirements

*   Develop/Utilize API endpoints for agent login (/API/auth/login).
*   Develop/Utilize API endpoints for product search (/API/product).
*   Develop/Utilize API endpoints for sale creation (/API/sale).
*   Develop/Utilize API endpoints for admin login (/API/auth/login).
*   Develop/Utilize API endpoints for commission processing (/API/sales-commissions/[id]/process).
*   Develop/Utilize API endpoints for commission approval (/API/commissions/[commission.id]/status).
*   Develop/Utilize API endpoints for agent commission view (/API/commissions).
*   Implement authentication and authorization for both agents and admins.
*   Implement logic for commission calculation based on product and sale details.
*   Implement status tracking for sales and commissions (pending, calculated, approved).
*   Ensure data integrity and security throughout the API flow.
*   Utilize Swagger UI and JSON for API documentation ([http://13.49.29.196:5000/api-docs/](http://13.49.29.196:5000/api-docs/), [13.49.29.196:5000/swagger.json](http://13.49.29.196:5000/swagger.json)).

## Dependencies

*   Existing API infrastructure and database setup.
*   Availability of agent and admin credentials for testing.
*   Clear definition of commission calculation logic.
*   Access to the specified Swagger UI and JSON documentation for API design.

## Suggested Implementation Approach

1.  **API Design & Contract:** Thoroughly review and potentially refine the API design based on existing Swagger documentation. Define clear request/response formats for each endpoint.
2.  **Authentication & Authorization:** Implement secure authentication (e.g., JWT) for agents and admins. Implement role-based access control to restrict access to specific APIs based on user role.
3.  **Endpoint Development:** Develop each API endpoint incrementally, following test-driven development (TDD) principles.
    *   Start with Agent Login and Product Selection.
    *   Move to Sale Creation and Status Validation.
    *   Then, Admin Login and Commission Processing.
    *   Finally, implement Commission Approval and Agent Commission View.
4.  **Commission Calculation Logic:** Implement the commission calculation logic as a separate, reusable component.
5.  **Status Management:** Implement a robust state management system for sales and commissions, ensuring accurate status transitions.
6.  **Testing:** Write comprehensive unit, integration, and end-to-end tests for all API endpoints and the commission calculation logic.
7.  **Documentation:** Maintain up-to-date API documentation using Swagger.
8.  **Deployment:** Deploy the API to a staging environment for thorough testing before deploying to production.
9.  **Monitoring:** Implement monitoring and logging to track API performance and identify potential issues.
```

**Please provide the entire command with the content in a single message for it to work correctly.**
