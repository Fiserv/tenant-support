# Recipes

The "Recipes" section in the Developer Studio’s left navigation panel provides access to practical, outcome-driven guides that help developers accomplish specific tasks using APIs (and potentially, SDKs in the future).

Recipes are contained in markdown files stored in the ```recipes``` folder of the GitHub repository. Each recipe is designed to guide developers through a series of steps to achieve a particular goal.
![recipes folder](assets/images/recipes-folder-example.png "recipes folder")

## Recipe Example

The following is a sample recipe file:

```
# Sample recipe 1

## Title
A clear and descriptive title summarizing the recipe’s purpose

## Description
A brief overview of what the recipe accomplishes and its relevant use cases

## Prerequisites 
Setup requirements such as API keys, libraries, or environment configurations

## Step-by-step instructions
Clear, numbered steps guiding users through the implementation

## Response examples
Sample API responses for both success and error scenarios

## Error handling tips (optional)
Suggestions for managing common implementation errors

## Links to API references (encouraged)
Direct links to relevant API documentation

## Use cases
Real-world scenarios where the recipe is applicable

## Related Recipes
Links to similar or complementary recipes
[recipe 2](?path=docs/recipes/recipe_2.md)
[recipe 3](?path=docs/recipes/recipe_3.md)```
```
## Enable Recipes
To enable the "Recipes" section in Developer Studio, add the following to the ```feature``` section of the ```tenant.json``` file located in the ```/config``` directory of the GitHub repository:

```json
{   
    "name": "enableRecipes",
    "value": true
}
``` 

![enable recipes](assets/images/enable-recipes-tenant-json.png "enable recipes")
