# ZenUML

## example 1
*file:*  
[example1.zenuml](example1.zenuml)

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

*preview:*  
![Screenshot 2024-09-12 160623](https://github.com/user-attachments/assets/50bb67c8-031d-423b-a908-ea316d0a15dd)

## example 2
*file:*  
[example2.zenuml](example2.zenuml)

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

*preview:*  
![Screenshot 2024-09-12 160700](https://github.com/user-attachments/assets/daa4269b-a8fb-46ae-b341-8a6a7c901aae)
