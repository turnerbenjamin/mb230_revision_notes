# Connected Customer Service and IoT

## Introduction

Connected customer service is an add-in solution to Customer service. It is 
used to connect IoT telemetry data to Customer Service.

It may be used to trigger actions such as sending an automated command to a 
device or proactively scheduling a service.

## Very High-Level Deployment Information

I doubt we need detailed knowledge here. The core components are:

### Azure IoT Hub

This is a managed service for communication between devices and your 
IoT application.

The Connected Customer Service Add-In for IoT Hub allows for a connection to
the Customer Service application.

It is possible to use a custom IoT provider rather than Hub, but this is not
covered in the materials.

### Stream Analytics

This is a managed, real-time event processing engine which is used to gain
insights from IoT data. It is a funnel used to send selective alerts to D365
apps.

### Azure SQL Database

This is used to store device heartbeat messages

### Azure Blob Storage

This is used to store queries used by Stream Analytics

## Interacting with IoT Devices in Hub and Workspace

There are various tables included with Connected Customer Service used to work
with IoT devices:

## Customer Assets

Customer Assets record which products are located where. They also track service
history for that asset. Assets may be IoT devices or some other product.

We may associate a connected device with a Customer Asset record. Once the 
association is made, IoT alerts may be viewed from the record.

It is possible to define a hierarchical structure with parent and child assets.
This is useful where a device contains multiple IoT sensors.

### Registering a Device

A device needs to be registered with IoT hub. This may be done:

- From a customer asset record
- In IoT hub directly

## Capturing Device Data in Customer Service

Using Connected Customer Service device data may be captured:
- When IoT alerts are sent
- Using the pull device data button in the command bar of an asset
- Scheduled data pulls

## IoT Alerts

IoT alerts are received as JSON. We can use Power Automate to parse the
data and update the IoT alert with the parsed values.

There is an IoT Alert to Case Process flow which may be used to generate a new
case from an IoT alert.

## Security Roles

- IoT Administator: All privileges for records on customer assets, IoT devices,
alerts etc
- IoT endpoint user: Special role used by MS to connect Dynamics 365 to IoT
Hub applications

To work with device registration and device data pulls a user will need both of 
these roles or a custom roles with the required.

## Interacting with a Device

There are various records used to interact remotely with a device:

### Device Category

This is used to group multiple devices by type. These can be used for:

- Reporting
- management
- Simplifying interactions with associated devices

We may associate a device category with:
- Command definitions
- Device properties available
- Device Tags (which property definitions are used as device tags and displayed
for devices assigned to this category)
- Device records

### Command Definition

A command represents an action or command to send to a device. This will contain
preconfigured properties which we may then modify when sending a command.

A command may be associated with a device category

### Property Definitions

A command is a collection of properties. These will include:

- Name
- Type
- Editable
- Visible
- Type specific properties, like max and min value for a whole number
- default value

If we define the type as object, we can then define properties of that object
by creating separate property definitions and setting their parent property to
the object property.

## Issuing a Command

We can construct commands manually with JSON or use a command definition to 
simplify the process.

Since the command is JSON, we need to parse the json in Power Automate and then
use the extracted properties to set fields in the Run a device command action.

A command may be sent from an IoT alert or IoT device record