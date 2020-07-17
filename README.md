# openapi-py-client-generator

This CLI tool generates a custom Python OpenAPI 2.0 or 3.0 client for a given yaml / json OpenApi spec using the 
official OpenAPI docker images and configurable mustache templates.

# Using the generated OpenAPI / Swagger client

To use the generated client in your application just include the package in your requirements:

```git+https://github.com/<your-handle>/<your-repo>.git#egg=swagger_client```

Then import the client like any other package:
    
```from swagger_client import MyApi```

### Re-building the OpenAPI / Swagger Client

These are the build steps for re-generating the OpenAPI / Swagger Client. 

#### Pre-requisites:

- You need to have [Docker](https://docs.docker.com/get-docker/) installed locally and running.
- You will need an OpenAPI / Swagger yaml or json spec file OR the URL to that spec.
- If you want to use an OpenApi / Swagger spec FILE on your computer, place the file in the ```/generator/specs``` folder.
 
#### Generating an Updated API Client

    
Open up a new terminal window. From the root folder of this project, run `bash ./generate-client.sh`.

This will utility will generate an updated API client. Usage is simple, just follow the prompts:
- Enter the URL / file name for the OpenApi spec to use
- Choose a version of OpenApi to use: [2 / 3]
- What format is the spec in?: [yml / json]
- Choose a template to use: [oapi2 /  oapi3 / <custom>]
- Would you like to push the client to a remote repository? [yes / no]
- Enter a git repository URL or press enter to use the defaults
- Enter the name of the branch you would like to commit to

And that's it!
   
#### Customizing Defaults
You can configure the defaults by adding a .env file in the ```/generator``` folder.
See ```sample.env``` in the root folder of this project for a template you can use.

You can configure the following defaults:
- API_CLIENT_REPO_URL
- API_SPEC_URL
- OAPI2_TEMPLATE_DIR (Default: oapi2)
- OAPI3_TEMPLATE_DIR (Default: oapi3)
- DEFAULT_OPEN_API_VERSION (Default: 3)
- DEFAULT_SPEC_FORMAT (Default: yml)
- DEFAULT_TEMPLATE_DIR (Default: oapi3)


#### Modifying the Templates

- Documentation for swagger-codegen [Mustache template variables](https://github.com/swagger-api/swagger-codegen/wiki/Mustache-Template-Variables)