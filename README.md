# Smart Home Security System - Design and Validation Project

This repository contains my complete system-engineering design for a residential Smart Home Security System.

The project focuses on a local-first security architecture: critical functions such as sensor processing, local alarm activation, and event logging continue to work even if Internet access is unavailable. Cloud services are used as an extension for remote access, notifications, synchronization, and backup rather than as a single point of failure.

## Deliverables

- `Smart_Home_Security_SysRS.pdf` - System Requirements Specification based on the ISO/IEC/IEEE 29148:2018 SysRS structure.
- `Smart_Home_Architecture.drawio` - logical and deployment architecture views.
- `Smart_Home_SysML.drawio` - SysML block definition, use-case, state-machine, and sequence diagrams.
- `Smart_Home_Decision_Matrices.xlsx` - weighted tradeoff analysis for sensors, cameras, controllers, and the server/manager architecture.
- `Smart_Home_Verification_Validation_Test_Cases.xlsx` - verification and validation test cases with requirement traceability.

## Main design choices

I chose a hybrid edge + cloud approach because a security system should remain useful when the Internet is down. The local control unit therefore owns the time-critical security logic and local storage. Remote services add convenience without replacing local operation.

For the device layer, I selected Zigbee for low-power sensors and smart-device controllers so both groups can share one mesh/coordinator technology. Z-Wave scored very close to Zigbee in the sensor tradeoff, but the small numerical advantage did not justify adding a second radio ecosystem to the architecture.

For security cameras, I selected PoE IP cameras because stable power, predictable latency, and local-network reliability are more important than easy installation for fixed security video.

## Verification and validation approach

The test workbook separates verification from validation:

- Verification checks that the designed system satisfies its documented requirements and interfaces.
- Validation checks that the resulting behavior meets homeowner and resident needs in realistic use scenarios.

Every numbered test step includes its own expected outcome. The test type uses one clear classification such as `Functional`, `Non-functional (Performance)`, `Non-functional (Reliability)`, `Non-functional (Security)`, or `Non-functional (Usability)`.

## Visual style

The project uses a consistent gray-and-orange theme across diagrams and spreadsheets. Gray represents core/local infrastructure and neutral system elements; orange is used for cloud/external services, selected design decisions, and visual emphasis.

## Submission checklist

- SysRS PDF included
- Architecture `.drawio` included
- SysML `.drawio` included
- Decision matrix `.xlsx` included
- Verification/Validation `.xlsx` included
- Requirements and test cases are traceable by ID
- Required verification and validation scenarios are covered
- Tradeoff decisions include explicit rationale rather than relying only on the highest numerical score
