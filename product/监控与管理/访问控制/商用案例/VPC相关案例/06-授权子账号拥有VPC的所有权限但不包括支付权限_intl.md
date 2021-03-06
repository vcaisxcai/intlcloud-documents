### Authorizing a sub-account with all permissions of VPC except payment

A sub-account Developer under the enterprise account CompanyExample (ownerUin is 12345678) requires full management permissions (such as creation and management) of the enterprise account CompanyExample's VPC service, except the payment permission. The sub-account is allowed to make an order but cannot pay for it.

Solution A:

The enterprise account CompanyExample directly authorizes the preset policy QcloudVPCFullAccess to the sub-account Developer. For more information on authorization, please see [Authorization Management](https://intl.cloud.tencent.com/document/product/598/10602).

Solution B:

Step 1: Create the following policy using policy syntax
```
 {
    "version": "2.0",
    "statement":[
         {
             "effect": "allow",
             "action": "vpc:*",
             "resource": "*"
         }
    ]
}
```

Step 2: Authorize the policy to the sub-account. For more information on authorization, please see [Authorization Management](https://intl.cloud.tencent.com/document/product/598/10602).


