## Integrate [Become KYC service](https://becomedigital.net/) to your website with Become web button

How it looks like in your code:

```
<become-button userId="<YOUR_USER_ID>" contractId="<YOUR_CONTRACT_ID>" token="<YOUR_JWT_TOKEN>" />
```

How it looks like on your page:

<img src="https://gist.githubusercontent.com/Tyg0th/15c5131ef7d2b24b9effa97eb45dedce/raw/07a5e1f3e428bd1d32bfe2940591872e1ae1ec2d/become-button-example.jpg" width="211" />


### Integrate

Add this script to your `<script>` tag 

```
<script src="https://onboarding.becomedigital.net/resources/button_demo_polipay.js"></script>
```

Declare the userId for this identity, the contractId and the token in the custom element

```
<become-button userId="<YOUR_USER_ID>" contractId="<YOUR_CONTRACT_ID>" token="<YOUR_JWT_TOKEN>" />
```

### API

#### Button attributes

| Attribute name | Description                                                                                     |
|----------------|-------------------------------------------------------------------------------------------------|
| `userId`     | Custom unique key per validation declared by the user                             |
| `contractId`     | Contract identifier for validation type |
| `token`     | JWT safe created for requests in the API generated by company credentials                             |
| `country`     | 2 characters country identifier, if provided it will not show the country selection step and use it as default. Example of use: "FR" (France)                             |
| `state`     | 2 charactes state identifier (only available for US states when country is "US")                             |


#### Events

You can also subscribe to the events that the button emits to let you know about the validation process, the most importants are

| EventName                  | Description                                     |
|----------------------------|-------------------------------------------------|
| become:verificationStarted | Validation process started                      |
| become:userFinishedSdk     | Successful completion of the validation process, return latest step data |
| become:exitedSdk           | User exited the process manually                |
| become:kycInfo| Information after completing the KYC flow |
| become:satInfo | Sat Information returned after uploading the CRSF |
| become:watchListInfo | Flag to check if company is in any watchlist |
| become:rfcCheckInfo | Return the information of the company based in the RFC |
| become:accountStatusInfo | Return the information of the bank account status uploaded, it is also available in userFinishedSdk as it is the latest step |


### Example

* Vanilla JS: see `index.html`
