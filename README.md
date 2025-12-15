S7API
=====

Scene7 IPS API SOAP Client Stub

This project generates a SOAP client stub from the Scene7 IPS API WSDL using Apache Axis2.

## Documentation

Supported WSDLs can be found [here](https://experienceleague.adobe.com/en/docs/dynamic-media-developer-resources/image-production-api/c-wsdl-versions#concept-aff3e13f3b59486882260b5f2e962226)

| API Release Version | WSDL File | Namespace URI |
|---------------------|-----------|---------------|
| 6.8/2014R1 | IpsApi-2014-04-03.wsdl | http://www.scene7.com/IpsApi/xsd/2014-04-03 |
| 6.6/2013R1 | IpsApi-2013-02-15.wsdl | http://www.scene7.com/IpsApi/xsd/2013-02-15 |
| 6.0/2012R1 | IpsApi-2012-02-14.wsdl | http://www.scene7.com/IpsApi/xsd/2012-02-14 |
| 4.5 | IpsApi-2010-01-31.wsdl | http://www.scene7.com/IpsApi/xsd/2010-01-31 |
| 4.4 | IpsApi-2009-07-31.wsdl | http://www.scene7.com/IpsApi/xsd/2009-07-31 |
| 4.2 | IpsApi-2008-09-10.wsdl | http://www.scene7.com/IpsApi/xsd/2008-09-10 |
| 4.0 | IpsApi-2008-01-15.wsdl | http://www.scene7.com/IpsApi/xsd/2008-01-15 |
| Pre-4.0 | IpsApi.wsdl | http://www.scene7.com/IpsApi/xsd |

API Documentation can be found [here](https://experienceleague.adobe.com/en/docs/dynamic-media-developer-resources/image-production-api/operation-methods/operation-parameters/c-methods)

## Prerequisites

- Java 8 or higher
- Maven 3.x

## Building the WSDL Stub

### Default Build (API Version 6.8)

To generate and compile the SOAP client stub from the WSDL:

```bash
mvn clean compile
```

This will:
1. Download the WSDL file from the Scene7 server
2. Generate Java client code using Axis2 wsdl2code plugin
3. Compile the generated code

The generated source code will be located in:
```
target/generated-sources/axis2/wsdl2code/src/com/scene7/api/webserviceclient/
```

### Building a JAR Package

To package the compiled stub into a JAR file:

```bash
mvn clean package
```

The JAR file will be created at:
```
target/IPSApi-6.8_2014R1.jar
```

### Using Different API Versions

This project supports multiple API versions via Maven profiles, as documented in the [Adobe Experience League IPS Web Service WSDL versions](https://experienceleague.adobe.com/en/docs/dynamic-media-developer-resources/image-production-api/c-wsdl-versions#concept-aff3e13f3b59486882260b5f2e962226):

- **6.8** (default): `mvn clean compile -P6.8` - Uses `IpsApi-2014-04-03.wsdl`
- **6.6**: `mvn clean compile -P6.6` - Uses `IpsApi-2013-02-15.wsdl`
- **6.0**: `mvn clean compile -P6.0` - Uses `IpsApi-2012-02-14.wsdl`
- **4.5**: `mvn clean compile -P4.5` - Uses `IpsApi-2010-01-31.wsdl`
- **4.4**: `mvn clean compile -P4.4` - Uses `IpsApi-2009-07-31.wsdl`
- **4.2**: `mvn clean compile -P4.2` - Uses `IpsApi-2008-09-10.wsdl`
- **4.0**: `mvn clean compile -P4.0` - Uses `IpsApi-2008-01-15.wsdl`
- **pre-4.0**: `mvn clean compile -Ppre-4.0` - Uses `IpsApi.wsdl`

Each profile uses a different WSDL file and namespace URI. The generated package name may vary depending on the version.

## Generated Code Structure

The generated stub includes:
- Service stub classes (`IpsApiServiceStub.java`)
- Data transfer objects (DTOs) for all API types
- Exception classes for fault handling
- Callback handlers for asynchronous operations

## Using the Generated Stub

After building, you can use the generated stub in your Java projects by:

1. Adding the JAR as a dependency, or
2. Including the generated source files directly in your project

The main entry point is typically `IpsApiServiceStub` class located in the `com.scene7.api.webserviceclient` package.

## Dependencies

The project includes the following dependencies:
- Apache Axis2 Kernel (1.4.1)
- Apache Axis2 ADB (1.4.1)
- Log4j (1.2.16)
