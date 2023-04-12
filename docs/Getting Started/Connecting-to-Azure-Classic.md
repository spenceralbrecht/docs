# Connecting to Microsoft Azure (Classic Compute)

Connecting to Microsoft Azure (Classic Compute) can be tricky. First you'll need to download and install the [Azure CLI](https://docs.microsoft.com/en-us/azure/cli-install-nodejs) for your platform.

## Authenticating to the CLI

Afterwards you'll need to login to the Azure CLI using the command:

`azure login`

## Setup the CLI

You'll need to make sure you are in ASM (Azure Service Management) mode. Execute the command:

`azure config mode asm`

## Find Your Subscription

Then list your available subscriptions:

```
$ azure account list
info:    Executing command account list
data:    Name                                         Id                                    Current  State   
data:    -------------------------------------------  ------------------------------------  -------  --------
data:    VS Ultimate MSDN 2                           e93b6f78-623c-465c-8d00-0b4fff26d9c9  true     Enabled 
data:    BizSpark                                     66a6dde6-4077-4e1d-9dae-aa1fffd19572  false    Enabled 
data:    Pay-As-You-Go                                b8ad6910-1175-44da-97e4-a06fff50fe61  false    Enabled 
data:    Windows Azure MSDN - Visual Studio Ultimate  e13f9517-925e-414b-b40c-afffff1582b6  false    Enabled 
data:    VS Ultimate MSDN 1                           59e1ab07-6953-439a-b56c-4f01b7ffffba  false    Enabled 
```

Copy the subscription Id you would like to connect to VM power and execute the command:

## Download Publish Settings File

`azure account download <subscription id>`

You will be taken to your browser to download your .publishsettings file:

![Azure account download browser screenshot](https://cdn.vmpower.com/prod-render/dist/img/cloud-steps/azureasm/step2.png)

## Creating the Certificate

Using the path of the .publishsettings file execute the command to create your `.pem` management certificate file:

```
azure account cert export -p <path-to-.publishsettings-file>
```

## Securely Upload Certificate to VMPower
In your current directory you should have a file with the name being `<subscription id>.pem`. Enter your subscription ID into the VMPower Azure Classic VM connection form along
with your `<subscription id>.pem` file.
