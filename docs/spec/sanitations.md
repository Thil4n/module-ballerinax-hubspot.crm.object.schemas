_Author_:  <!-- TODO: Add author name --> \
_Created_: <!-- TODO: Add date --> \
_Updated_: <!-- TODO: Add date --> \
_Edition_: Swan Lake

# Sanitation for OpenAPI specification

This document records the sanitation done on top of the official OpenAPI specification from HubSpot Automation Action. 
The OpenAPI specification is obtained from (TODO: Add source link).
These changes are done in order to improve the overall usability, and as workarounds for some known language limitations.


1. **Change the `url` property of the `servers` object**:
   - **Original**: `https://api.hubapi.com`
   - **Updated**: `https://api.hubapi.com/crm-object-schemas/v3/schemas`
   - **Reason**: This change is made to ensure that all API paths are relative to the URL (`/crm-object-schemas/v3/schemas`), which improves the consistency and usability of the APIs.


2. **Update API Paths**:
   - **Original**: Paths shared a common segment across all resource endpoints.
   - **Updated**:  Common paths segment is removed from the resource endpoints, as it is now included in the base URL. For example:
     - **Original**: `/crm-object-schemas/v3/schemas`
     - **Updated**: `/`
   - **Reason**: This modification simplifies the API paths, making them shorter and more readable. It also centralizes the versioning to the base URL, which is a common best practice.

## OpenAPI cli command

The following command was used to generate the Ballerina client from the OpenAPI specification. The command should be executed from the repository root directory.

```bash
bal openapi -i docs/spec/openapi.json --mode client -o ballerina
```
Note: The license year is hardcoded to 2024, change if necessary.