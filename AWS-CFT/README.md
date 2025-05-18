
# CloudFormation (CFT) – Infrastructure as Code (IaC) Notes

## What is AWS CloudFormation (CFT)?

AWS **CloudFormation** lets you define your infrastructure as code using **YAML or JSON templates**. These templates describe:
- Which resources you need (like EC2, S3, etc.)..
- How they are configured..
- How they relate to each other..

You **deploy the entire infrastructure** as a **stack**. A **stack** is a collection of resources that are created, updated, or deleted together.
## Overview

- #### **IaC (Infrastructure as Code)**:
	- allows users to define cloud infrastructure using code.

- #### **User Input Formats:**
	- YAML / JSON

- #### **Deployment Target:** 
	- AWS Cloud

## AWS CLI vs AWS CFT (CloudFormation Template)

| Feature          | AWS CLI                                | AWS CloudFormation (CFT)                        |
| ---------------- | -------------------------------------- | ----------------------------------------------- |
| Approach         | Imperative (step-by-step instructions) | Declarative (describe what you want)            |
| Template Support | No                                     | Yes                                             |
| Automation       | Manual commands / scripts              | Template-driven via stacks                      |
| Drift Detection  | No                                     | Yes (detects changes not aligned with template) |
| Infrastructure   | One-off configuration                  | Managed as a single unit (stack)                |

## Key Features

- **Drift Detection**
    
    - Detects if someone manually changed a resource outside of CloudFormation (e.g., via AWS Console).
        
    - CloudFormation compares the actual AWS environment with the template.
        
    - It **highlights** the differences (drift) and allows you to take corrective actions.

- **Stacks**
    
    - A **stack** is the result of deploying a template
	    
    - All resources in a template are grouped into a single stack.
        
    - You can **create**, **update**, or **import** stacks.
