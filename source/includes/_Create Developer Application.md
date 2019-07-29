# Create Developer Application

-<strong>Step 1 : Create New Application</strong>

- Go to `Developer`tab (the last one)and you will see the following page:

![image](images/CDA1.png)<br />

- Click `Create Application` button and system will prompt you to enter application name:<br /><br />
  ![image](images/CDA2.png)

- New Application is created as follow :

![image](images/CDA3.png)

-<strong>Step 2 : Obtain `clientID` and `cilientSecret`</strong>

- Click on the application created in Step 1 , you may edit and update relevant information here :
  - Note : If you would like to disable the application , simple toggle **"ON/OFF"** switch button at **RHS**.

![image](images/CDA4.png)

- Click on`Show`to reveal your `clientSecret`:

![image](images/CDA5.png)

-<strong>Step 3 : Product Settings</strong>

- Go to `Products` tab in sub-menu and choose desired product to set up :

![image](images/CDA6.png)

- For Loyalty and Social Media features, you will need to input a wwebhook URL as below :

![image](images/CDA7.png)

- For Payment feature , besides wehbook URL, system will show you `Server Public Key` while you are required to provide `Client Public Key` :

![image](images/CDA8.png)

<strong>NOTES ON RSA KEYS</strong> <br />

- `Public Keys` needs to have be wrap as following :
  ![image](images/CDA9.1.png)
- If you need help to generate key, please visit [Generator RSA Key](https://merchant.revenuemonster.my/developer/apps/5781149902293289753/rsa-generator).**Merchant portal => Developer => Application => Generator RSA Key** Suggested key size: 2048 Bit. Keep your private keys in safe place! Or use our **Generate RSA key** tool.

- `Private Keys` are required to sign API request(s) contents. `Public Keys` are used to verify content received.

**Optional Tool: Signature Debugger**<br />

- For security purposes, we enhanced our authentication flow and Open API by adding layers of encryption to our endpoints. You may use our Signature Debugger
- You may develop your own encryption tool on your desired application directly, or you may use our Signature Debugger to do signing/verification using private/public keys as obtained from previous step.
- Refer more on `Signature Debugger`

![image](images/CDA10.png)
