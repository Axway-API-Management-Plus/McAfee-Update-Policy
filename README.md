# McAfee-Update-Policy

# Description
This sample policy can be used to update the McAfee DAT-File on the Axway API-Gateway using by the 'McAfee virus scan' filter.
The configuration contains a scheduled policy which is executed once a day at 10:15am and in addition you can initiate the update manually.

## API Management Version Compatibilty
This artefact was successfully tested for the following versions:
- V7.5.3


## Install

```
• Import the Policy-Fragment: 'McAfee-Sample-Update-Policy.xml' into your configuration.
• This will create a new container: 'AdminPolicies' containing the update policy and a test policy
• O
• Deploy the configuration
```

## Usage

```
• The configuration set creates two endpoints which you may use:

```

## Bug and Caveats

```
This policy has been tested on Linux only!
```

## Contributing

Please read [Contributing.md] (/Contributing.md) for details on our code of conduct, and the process for submitting pull requests to us.

## Team

![alt text][Axwaylogo] Axway Team

[Axwaylogo]: https://github.com/Axway-API-Management/Common/blob/master/img/AxwayLogoSmall.png  "Axway logo"


## License
Apache License 2.0 (refer to document [license] (https://github.com/Axway-API-Management/Executing-loopback-requests-on-a-listener/blob/master/LICENSE))

