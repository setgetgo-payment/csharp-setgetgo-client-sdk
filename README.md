# Getting started
The C# SDK allowes you to accept Crypto payments from your C# .NET app using the PayByte REST API.
The SDK has been designed to act as a wrapper for all the main PayByte functionalities, 
allowing the developers to focus on the actual purchasing flow rather than on the API's implementation details.

## Create a new payment

```csharp
var payByte = new PayByte(isTestnet: true);
var payment = new Payment
{
   Amount = (decimal)0.0332,
   ApiKey = "[insert api key]",
   Coin = "BTC",
   Callback = "https://test.com/callback?invoiceId=123"  
};
var paymentResponse = await payByte.CreatePaymentAsync(payment);
```

The paymentResponse will contain the JSON representation of the payment response. 

## Get a payment data

Simply provide the payment address to retrieve all data related to a transaction.

```csharp
var payByte = new PayByte(isTestnet: true);
var paymentId = "cf565888-28f5-430e-85af-b34b945ce20f";
var paymentData = await payByte.GetPaymentAsync(paymentId: paymentId);
```

The SDK will return a JObject representation of the transaction data.

## Get rates

Get the exchange rates of all supported crypto currencies against the provided currency code.

```csharp
var payByte = new PayByte(isTestnet: true); 
var rates = await payByte.GetRateAsync(currency: "GBP");
```
