# Razorpay Python Client

Python ASYNC bindings for interacting with the Razorpay API. 

## Installation

1.  Through pip: `pip install tornado-razorpay`

2.  Manually: `python setup.py install`

## Usage

You need to setup your key and secret using the following:
You can find your API keys at <https://dashboard.razorpay.com/#/app/keys>.

```py
from tornado_razorpay import Client
razor = Client("<YOUR_API_KEY>", "<YOUR_API_SECRET>")
```


### Payments

- Capture a payment

    ```py
    await razor.payment.capture("<PAYMENT_ID>", "<AMOUNT>")
    ```

- Fetch a particular payment

    ```py
    await razor.payment.fetch("<PAYMENT_ID>")
    ```

- Fetch all payments

    ```py
    await razor.payment.all()
    ```

### Refunds

- Initiate a refund

    ```py
    await razor.refund.create("<PAYMENT_ID>")  # for whole amount
    await razor.refund.create("<PAYMENT_ID>", data={"amount": "<AMOUNT_TO_BE_REFUNDED>"})  # for particular amount
    ```

- Fetch a particular refund

    ```py
    await razor.refund.fetch("<PAYMENT_ID>", "<REFUND_ID>")
    ```

- Fetch all refunds for a particular payment

    ```py
    await razor.refund.all("<PAYMENT_ID>")
    ```

NOTE: You will have to use Tornado's IOLoop to use this API in Async. If you are looking for Sync API's or don't know 
what this is, please go to https://github.com/razorpay/razorpay-python.