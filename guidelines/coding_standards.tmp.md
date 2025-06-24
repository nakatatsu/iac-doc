# Coding standards

## Style
- Module calls must always be documented in main.tf.
- Variable blocks must always be documented in variables.tf.
- Variable blocks and output blocks must always have descriptions.
- Variable blocks must always have types specified.
- Use variable blocks when there are parameter differences between callers (e.g., CPU 4096 for production, CPU 1024 for development). However, do not use default values.
- Do not reference variable blocks as values in output blocks.
- Locals blocks must be documented in locals.tf.
- Avoid overusing data blocks. When using them, place data blocks immediately above the resource blocks that use them.
- The order of resource block attributes should be as follows: 1. If present, The count or for_each meta-argument, 2. Resource-specific non-block parameters, 3. Resource-specific block parameters, 4. If required, a lifecycle block, 5. If required, the depends_on parameter. No other constraints apply.
- The order of variable block attributes should be as follows: 1. Type, 2. Description, 3. Default (optional), 4. Sensitive (optional), 5. Validation blocks
- Avoid using abbreviations and use formal names instead. (e.g., `[NG] cg [OK] coding guidelines`). However, abbreviations that are used as proper nouns like `RDS` and `id` can be used.
- Avoid embedded attributes like ingress/egress in security groups, and associate them using dedicated resources like aws_security_group_rule.

## Tags
- Set Environment (e.g., development, production) and Service (e.g., ecommerce, auth) in aws_default_tags in root modules.
- Always set Name tags for resources that use Name tags as identifiers.
- Set Environment and Project in default_tags within the provider block. Never set them anywhere else.

## Tools
- Apply terraform fmt to all .tf files.
- Perform syntax validation with terraform validate.
- Introduce TFLint to detect AWS best practice violations and unused declarations.

## Naming Conventions
- Use snake_case for resource names in terraform code (e.g., web_server).
- Name resources that are the only one in a module as main. (e.g., resource "aws_vpc" "main").
- Name multiple resources in a module according to their purpose (e.g., primary, read_replica).
- Do not use plural forms in resource names.
- Do not use names that duplicate resource types in resource names (e.g., aws_instance.ec2_instance).
- Add units to numeric values (e.g., size_gb, ram_size_gb).
- Use MiB/GiB for storage and MB/GB for others as decimal units.
- Name boolean variables in affirmative form (e.g., enable_external_access).
- Name AWS resource names (Name tags) in the format `[environment]-[project]([-additional_info_if_any])` (e.g., `production-practitioner-api`). In HCL, use variables like `${var.environment}-${var.project}-api`. 'api' is just an example, so be sure to replace it appropriately. 