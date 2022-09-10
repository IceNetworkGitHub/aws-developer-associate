# Identity and Access Management

## Users

- There is a hard limit of 5000 IAM users per account
- If you need more than 5000 IAM accounts per AWS account you can use external accounts and have them assume a role. Identity Federation external accounts can't directly access AWS resources, they must assume a role

## Groups

- Groups are **not** a true identity. They can't be referenced as a principal in a policy
- Groups are simply containers for IAM users that can have permissions associated with it
- There is a hard limit of 100 groups per AWS account

## Roles

- IAM roles can have two types of policies which can be attached
  - **The trust policy**
    - The Trust Policy controls which identity can assume that role.
    - The Trust Policy can reference different things. Such as, identities, other IAM users, other roles, and AWS services such as EC2. It can even allow anonymous usage of that role, and other types of identities such as Facebook, Google, etc.
  - **Permissions policy**
    - If something assumes a role, AWS (STS Secure Token Service) generates temporary security credentials for that role. sts:AssumeRole

### Service Linked Roles

- IAM role linked to a specific AWS service
- Predefined by a service
- Providing permissions that a service needs to interact with other AWS services on your behalf
- Service might create/delete the role or allow you to during the setup or within IAM
- You can't delete the role until it's no longer required by that service