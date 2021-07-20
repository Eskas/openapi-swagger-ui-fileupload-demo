# openapi-swagger-ui-fileupload-demo

Demonstrating problem with Swagger UI and file upload when code has been generated using `openapi-generator-maven-plugin` version `5.1.0`.

## Background
In another project I've upgraded the maven plugin for OpenAPI generation(`openapi-generator-maven-plugin`) from version `4.3.1` to `5.1.0`.
When doing this I noticed that Swagger UI doesn't recognize file inputs properly.
The problem occurs when I use the `jaxrs-jersey` generator, I haven't tested any other generators.


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
`mvn clean package jetty:run`
#### screenshot
![5.1.0 Screenshot](doc/img/5.1.0_screenshot.png?raw=true "5.1.0 Screenshot")
Browse to http://localhost:9999/swagger-ui/index.html

### Running with OpenAPI Generator 4.3.1
`mvn clean package jetty:run -Dopenapi-generator-maven-plugin.version=4.3.1 -Djetty-port=9998`

#### screenshot
![4.3.1 Screenshot](doc/img/4.3.1_screenshot.png?raw=true "4.3.1 Screenshot")
Browse to http://localhost:9998/swagger-ui/index.html

### Running with OpenAPI Generator 6.0.0-SNAPSHOT
`mvn clean package jetty:run -Dopenapi-generator-maven-plugin.version=6.0.0-SNAPSHOT -Djetty-port=9997`
#### screenshot

![6.0.0-SNAPSHOT_screenshot](doc/img/6.0.0-SNAPSHOT_screenshot.png?raw=true "6.0.0-SNAPSHOT Screenshot")
Browse to http://localhost:9997/swagger-ui/index.html

