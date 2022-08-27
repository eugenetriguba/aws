Tool which lets you create/update/delete resources in AWS with templates.

If you have a description and template format version, the description must directly directly.

Schema

* AWSTemplateFormatVersion
* Description
  * Human-readable description of this template.
* Metadata
  * Control how the different things in the CloudFormation template are presented in the console AWS UI.
* Parameters
  * Prompt the user for more information. i.e. Which size of instance to create?
* Mappings
  * K/V pairs that can be used for lookups.
* Conditions
  * Allow decision making in the template.
    * Must create condition and then use the condition with `Resources`.
* Transform
* Resources
  * Create/update/remove resources in AWS.
* Outputs
  * Way to preset outputs for the template based on what is being done by the template.

Template
- Logical resources

Stack contains all of the logical resources that the template tells it to contain. Living and active representation of a template.

For any logical resource in the stack, CloudFormation makes a corresponding physical resource in your stack. It keeps the logical and physical resources in sync.
