## Integrate [Become KYC service](https://becomedigital.net/) to your website with Become web button

How it looks like in your code:

```
<become-button token="<YOUR_JWT_TOKEN>" />
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
<become-button token="<YOUR_JWT_TOKEN>" />
```

### API Documentation

#### Button attributes

| Attribute name | Description                                                                                     |
|----------------|-------------------------------------------------------------------------------------------------|
| `token`     | JWT safe created for requests in the API generated by company credentials                             |                      |


#### Events

You can also subscribe to the events that the button emits to let you know about the validation process, the most importants are

| EventName                  | Description                                     |
|----------------------------|-------------------------------------------------|
| become:verificationStarted | Validation process started                      |
| become:userFinishedSdk     | Successful completion of the validation process, returns the uuid and result data |
| become:exitedSdk           | User exited the process manually                |

#### Events Details

The `become:verificationStarted` and `become:exitedSdk` events return an object with a result and a message key, these can be used to audit the user actions, when he/she initiated the proccess and if he/she canceled it so you can proceed accordangly.

```js
{
    result: { message: "STRING" }
}
// 1. "Flow started"
// 2. "Manually exited by user"
```
**Note**: the exitedSdk event closes the modal.

The `become:uuid` event return an object containing the UUID generated in the flow, it can be useful to check why a customer closed the flow, or to determine if they are facing any issue.
```js
{ 
    uuid: uuid
}
```
The become:userFinishedSdk returns an object with the uuid generated for that transaction and and object containing the information required.

```js
{ 
    result: data,
    uuid: uuid
}
```

### Example

* Vanilla JS: see `index.html`
