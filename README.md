# openapi-swagger-ui-fileupload-demo

Demonstrating problem with Swagger UI and file upload.

## Background
In another project I've upgraded the maven plugin for OpenAPI generation(`openapi-generator-maven-plugin`) from version `4.3.1` to `5.1.0`.
When doing this I noticed that Swagger UI doesn't recognize file inputs properly.

The following code snippet would, with version `4.3.1` of `openapi-generator-maven-plugin`, get a file upload input. When using version `5.1.0` the Swagger UI doesn't
display a file input.

```
 requestBody:
    content:
      multipart/form-data:
        schema:
          type: object
          required:
            - definitionFile
          properties
            definitionFile:
              type: string
              format: binary
```
## Prerequisites
* Java 1.8.0_212
* Maven 3.6.3

### Running with OpenAPI Generator 5.1.0
`mvn clean jetty:run`

Browse to http://localhost:9999/swagger-ui/index.html

### Running with OpenAPI Generator 4.3.1
`mvn clean jetty:run -Dopenapi-generator-maven-plugin.version=4.3.1 -Djetty-port=9998`

Browse to http://localhost:9998/swagger-ui/index.html
