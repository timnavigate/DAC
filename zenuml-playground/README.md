# ZenUML

### example 1
*file:*  
[example1.zenuml](example1.zenuml)

*preview:*  
pic...

<details>
<summary>body:</summary>

```
title Online shopping
@Actor Customer
Customer->Website.browse() {
    BackEnd.loadProducts
}
Customer->Website.addToCart(p1, p2) {
    BackEnd.updateCart
}
Customer->Website.submitOrder(p1, p2) {
    BackEnd.createOrder
}

Customer->Website.checkout(paymentInfo) {
    BackEnd.checkout(paymentInfo) {
        result = PaymentGatewat.processPaymentInfo()
        updateOrder(result)
        if (result == success) {
            DeliverySystem.register()

            DeliverySystem->Customer: Deliver the order
        } else {
            return rejected
            @return Website->Customer: rejected
        }
    }
}
```
</details>

### example 2
*file:*  
[example2.zenuml](example2.zenuml)

*preview:*  
pic...

<details>
<summary>body:</summary>

```
title Order Service
@Actor Client #FFEBE6
@Boundary OrderController #0747A6
@EC2 <<BFF>> OrderService #E3FCEF
group BusinessService {
    @Lambda PurchaseService
    @AzureFunction InvoiceService
}

@Starter(Client)
// POST /orders
OrderController.post(payload) {
    OrderService.create(payload) {
        order = new Order(payload)
        if(order != null) {
            par {
                PurchaseService.create(order)
                InvoiceService.createInvoice(order)
            }
        }
    }
}
```
</details>