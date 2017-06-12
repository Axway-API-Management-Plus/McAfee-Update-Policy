# McAfee-Update-Policy

# Description
This sample policy can be used to update the McAfee DAT-File on the Axway API-Gateway used by the 'McAfee virus scan' filter.
The configuration contains:
- policy to download & update the used McAfee-DAT-File
- a scheduler to perform the update once a day at 10:15am
- an endpoint to perform the update manually when needed
- an endpoint to check the virus-scan engine
Updates are cached to avoid useless downloads of the recent DAT-File.

Using the McAfee virus scanner on the Axway API-Gateway requires a license!

## API Management Version Compatibilty
This artefact was successfully tested for the following versions:
- V7.5.3 (Linux only)
- V7.5.2 (Linux only)


## Install

```
• Import the Configuration-Fragment: 'McAfee-Sample-Update-Policy.xml' into your configuration.
• This will create:
- a new container: 'AdminPolicies' containing the update policy and the test policy
- two exposed APIs in the default group (port 8080 by default):
- /UpdatePattern: Call this to manually trigger a DAT-File update
- /test-virus: Can be used to verify the virus-scanner is working (see below)
• Create a new folder: /var/tmp/AV where the newest DAT-File gets downloaded
• Deploy the configuration
```

## Usage

After importing the configuration-set and deploying it, two new APIs/Endpoints in the default group are exposed:
- /UpdatePattern: Call this to manually trigger a DAT-File update
- /test-virus: Can be used to verify the virus-scanner is working

When calling: e.g. 
```
http://<api-hostname>:<port>/UpdatePattern 
```
the following happens:
1. The newest DAT-File is downloaded
2. The MD5-Checksum is verified
3. The file is unzipped
4. Moved into the McAfee plugins folder
5. Finally the McAfee engine is initialized with the new DAT-File

As a confirmation you will see a screen similar to this:
![Update successful](https://github.com/Axway-API-Management-Plus/McAfee-Update-Policy/blob/master/images/Update-McAfee-Libraries-successful.png)

You can use the Test-API endpoint to verify that the virus scanner is working. To test  
download the Eicar test virus from here: http://eicar.org/85-0-Download.html and send this file like this
```
$api_server_install/apigateway/posix/lib/sr -f eicar_com.zip -a Content-Type:application/zip http://$SERVER_IP:$PORT/test-virus
```
In the API-Gateway monitoring you will see the following trace output:
![Trace output](https://github.com/Axway-API-Management-Plus/McAfee-Update-Policy/blob/master/images/McAfee-Virus-Scan-Test.png)

## Bug and Caveats

```
This policy has been tested on Linux only!
This policy works only, if the API-Gateway has direct internet access (you may add a proxy)
```

## Contributing

Please read [Contributing.md] (/Contributing.md) for details on our code of conduct, and the process for submitting pull requests to us.

## Team

![alt text][Axwaylogo] Axway Team

[Axwaylogo]: https://github.com/Axway-API-Management/Common/blob/master/img/AxwayLogoSmall.png  "Axway logo"


## License
Apache License 2.0 (refer to document [license] (https://github.com/Axway-API-Management/Executing-loopback-requests-on-a-listener/blob/master/LICENSE))

