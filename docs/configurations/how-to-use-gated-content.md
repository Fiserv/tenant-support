# How to use Gated-content

## What is Gated Content?

"Gated Content" is a mechanism developed to control file visibility and permissions on Developer Studio.

The different levels of accesses are:

**Public Access**: When all users can access the files publicly.

**Private Access**: When a user can only view the files while they are signed in Developer Studio.

**Private Entitled Access**: When signed in users with the appropriate access or entitlements to the files can access them. This is the most protected level of access. To gain this access users have to become a member of the entitled group through an approval process.

## How Gated Content works

![Gated content flow](assets/images/GC_diagram.png)

## Gated Content access for downloadable links in markdown files

The `file-access-definition.yaml` in the config folder defines asset files that have unique downloadable accessibility configurations. If a file has "access: public" defined for it, then everyone can see/download it.

![Public access](assets/images/GC_public_access.png)

If the file has "access: private" and "groups: \[no groups specified]" meaning, only users who have signed in Developer Studio are permitted to view it. If the file has "access: private" and "groups: \[ABC_BANK]" meaning, only users who have signed in Developer Studio and also belong to the group "ABC_BANK" are permitted to view it. Multiple groups can also be defined here like "groups: \[ABC_BANK, XYZ_BANK]"

![Private access](assets/images/GC_private_access.png)

Also the users can view and download these entitled files when they create a workspace for the product.

![Private entitled access](assets/images/GC_private_entitled_access.png)

> Please Note: Workspace needs to be enabled for a product. So in case its not enabled please open a GitHub support ticket with Developer Studio with label as "enhancement"

## Enable Gated Content access for API endpoints

![Locked API tree](assets/images/gated-apis/gated-api-tree.png)

You can add locks to the left navigation panel for API folders and endpoints which require users to belong to certain access groups (following similar rule to access for downloadable links).

To define them, you'll want to create the `api-access-definition.yaml` under your Github - `config/` folder and follow the following format for each gated entry:

- `xChildProductName` / `xGroupName`: Depends on the top level of your API structure. Some products define 3-level structure with `x-child-product-name` in their API spec while others don't have it.
- `groups`: Same rules as above. Empty list is considered login-only, any string value will be checked against the user's current groups.
- `sections`: An array to define one or more sub-folders that will be locked. This does not need to be defined if you intend to lock at the top level (see above).
- `versions` (Optional): An array for locking specific API versions.

![Example api-access-config file](assets/images/gated-apis/api-access-definition.png)

Here is an example of all the layering you can do with your `api-access-definition`:

```json
// Top-level feature lock
- xChildProductName: "childProductFolder"
  groups: ["TEST_GROUP1"]
// Second level lock with multiple allowed groups
- xChildProductName: "childProductFolder"
  sections:
    - xGroupName: "groupName"
  groups: ["TEST_GROUP1", "TEST_GROUP2"] // User in either "TEST_GROUP1" or "TEST_GROUP2" can access
// API specific lock with version
- xChildProductName: "ChildProductName1"
  sections:
    - xGroupName: "groupName1"
      sections:
        - xProxyName: "apiEndpoint"
  groups: ["TEST_GROUP_3"]
  versions: ["3.0.0"]
// Multi-level lock with all options but only requiring login
- xChildProductName: "Banking Services"
  sections:
    - xGroupName: "Users Data" // Locks entire "Users Data" folder
    - xGroupName: "Public Data" // Locks specifically "GET user" in "Public Data" folder
      sections:
        - xProxyName: "GET user"
  groups: []
  versions: ["3.0.0", "2.0.0"]
```

We currently do not add lock icons in the Catalog page and users can still technically attempt to access locked APIs directly if they know the endpoint path and http method via URL. As such, the content is censored.

![Locked API](assets/images/gated-apis/gated-api.png)

## Enable Gated Content access for other Assets

_**Coming soon...**_

## Provide 'Private Entitled Access' to users

> As of today this part is manual and solely maintained by Developer Studio Team. As part of the future road map, Dev Studio team would be developing a page for administrators from which they could grant access.

For product teams interested in setting up admin groups to provide access to users, please provide the following information which we will add to our database.

- Product/Tenant name
- Group Name
- Developer Studio user account ID (usually found under the network tab when logging in under `UserData` graphql query)

![User Access Group](assets/images/gated-apis/user-access-group.png)

### Tenant's Responsibilities

1. Tenants have to provide a list of the user access groups like "PRODUCT*BANKERS_GROUP", etc. The naming convention is in all caps and separated by '*'.
2. Tenants would have to share the list of user email addresses who register at Developer Studio because the user mapping part is currently manual. The backend mapping process ('user' to 'user access groups') would then be handled by the Dev Studio team.

## Admin UI and Notification Service for users

_**Coming soon...**_
