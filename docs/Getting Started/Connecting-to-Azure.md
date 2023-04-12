# Connecting to Microsoft Azure

Connecting to Microsoft Azure can be tricky. First you'll need to identify your Azure Active Directory (AAD) domain associated with your subscription. Azure accounts are associated with AAD domains and you can read more about that here](https://docs.microsoft.com/en-us/azure/active-directory/active-directory-how-subscriptions-associated-directory).

You'll then OAuth and provide VMPower with access to your subscription.

## Finding Your AAD Domain

First check your Azure Active Directories in your Azure Portal:

* [https://portal.azure.com/#blade/Microsoft_AAD_IAM/ActiveDirectoryMenuBlade/Domains](https://portal.azure.com/#blade/Microsoft_AAD_IAM/ActiveDirectoryMenuBlade/Domains)

You should see the domains associated with your subscription like so:

![AAD Directory screenshot](https://cdn.vmpower.com/docs/aad-directory.png)

## Entering Your AAD Domain

When presented by VMPower, be sure to enter this domain into the prompt:

![Azure prompt screenshot](https://cdn.vmpower.com/docs/aad-directory.png)

## Not Seeing Your VMs?

There are two main reasons you may not see VMs loaded up by VMPower.

### Insufficient Permissions

VMPower requires that *your account* has and *owner* or *administrator* role on the subscription you wish to connect to VMPower. You can check your current permissions on your Azure subscription by going to the ['Subscriptions' Blade](https://portal.azure.com/#blade/Microsoft_Azure_Billing/SubscriptionsBlade), selecting your subscription and checking the 'My Permissions' section:

![Azure IAM settings screenshot](https://cdn.vmpower.com/docs/azure-iam1.png)
