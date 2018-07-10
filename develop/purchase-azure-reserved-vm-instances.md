---
title: Purchase Azure Reserved VM Instances
description: How to purchase Azure Reserved Virtual Machine (VM) Instances using the Partner Center API.
ms.assetid: 
ms.author: v-thpr
ms.date: 03/26/2018
ms.topic: article
ms.prod: partner-center
ms.technology: partner-center-sdk
---

# Purchase Azure Reserved VM Instances


**Applies To**

-   Partner Center


To purchase an Azure Reserved Virtual Machine (VM) Instance using the Partner Center API, you must have one or more deployed Cloud Solution Provider (CSP) Azure subscriptions. If you do not have a CSP Azure subscription, use these basic steps to purchase one:
-   Get a list of offers for a market. 
-   Create an order for an CSP Azure subscription.
-   Submit your order.
-   Make sure your order is fulfilled. 

> [!NOTE]  
> Azure Reserved VM Instances are not available in the following markets:  
> * Brazil  
> * China  
> * India  
> * Russia  
> * South Korea  
> * Taiwan
> * Hong Kong


## <span id="Prerequisites"></span><span id="prerequisites"></span><span id="PREREQUISITES"></span>Prerequisites


-   Credentials as described in [Partner Center authentication](partner-center-authentication.md). This scenario supports authentication with both standalone App and App+User credentials.
-   A customer identifier. If you do not have a customer's ID, you can look up the ID in Partner Center by choosing the customer from the customers list, selecting Account, then saving their Microsoft ID.
-   A subscription ID for an active CSP Azure subscription.

## <span id="How_to_purchase_Azure_reserved_instances"></span><span id="how_to_purchase_azure_reserved_instances"></span><span id="HOW_TO_PURCHASE_AZURE_RESERVED_INSTANCES"></span>How to purchase Microsoft Azure Reserved VM Instances



Once you have identified the active CSP Azure subscription that you want to add an Azure Reserved VM Instance to, use the following steps to purchase it:    

1.  [Enablement](#enablement) - Register an active CSP Azure subscription to enable it for purchasing Azure Reserved VM Instances. 
2.  [Discovery](#discovery) - Find and select the Azure Reserved VM Instance products and SKUs you want to purchase and check their availability. 
3.  [Order submission](#order_submission) - Create a shopping cart with the items in your order and submit it. 
4.  [Get order details](#get_order_details) - Review the details of an order, all the orders for a customer, or view orders by billing cycle type. 

After you have purchased Azure Reserved VM Instances, the following scenarios show you how to manage their lifecycle by getting information about your Azure Reserved VM Instance entitlements, and how to retrieve balance statements, invoices, and invoice summaries. 
-   [Lifecycle management](#lifecycle_management)
-   [Invoice and reconciliation](#invoice_and_reconciliation)

## <span id="Enablement"></span><span id="enablement"></span><span id="ENABLEMENT"></span>Enablement



Once you have identified the active subscription that you want to add the Azure Reserved VM Instance to, you must register the subscription so that it is enabled for Azure Reserved VM Instances. To register an existing [Subscription](subscriptions.md) resource so that it is enabled for ordering Azure Reserved VM Instances, see [Register a subscription](register-a-subscription.md).

After registering your subscription, you should confirm that the registration process is completed by checking the registration status. To do this, see [Get subscription registration status](get-subscription-registration-status.md).

## <span id="Discovery"></span><span id="discovery"></span><span id="DISCOVERY"></span>Discovery



Once the subscription is enabled for purchasing Azure Reserved VM Instances, you're ready to select products and SKUs and check their availability using the following Partner Center API models: 

-   [Product](products.md#product) - A grouping construct for purchasable goods or services. A product by itself is not a purchasable item.​​
-   [SKU](products.md#sku) - A purchasable Stock Keeping Unit (SKU) under a product. These represent the different shapes of the product.​​
-   [Availability](products.md#availability) - A configuration in which a SKU is available for purchase (such as country, currency and industry segment).

Before purchasing an Azure Reserved VM Instance, complete the following steps:

1.  Identify and retrieve the Product and SKU that you want to purchase. You can do this by listing the products and SKUs first, or If you already know the IDs of the product and SKU, selecting them.

    -   [Get a list of products](get-a-list-of-products.md)
    -   [Get a product using the product ID](get-a-product-by-id.md)
    -   [Get a list of SKUs for a product](get-a-list-of-skus-for-a-product.md)
    -   [Get a SKU using the SKU ID](get-a-sku-by-id.md)

2.  Check the inventory for a SKU​. This step is only needed for SKUs that are tagged with an **InventoryCheck** prerequisite​.

    -   [Check Inventory](check-inventory.md) 

3.  Retrieve the [availability](products.md#availability) for the [SKU](products.md#sku). You will need the **CatalogItemId** of the availability when placing the order​. To get this value, use one of the following APIs: 

    -   [Get a list of availabilities for a SKU](get-a-list-of-availabilities-for-a-sku.md)
    -   [Get an availability using the availability ID](get-an-availability-by-id.md)

## <span id="Order_submission"></span><span id="order_submission"></span><span id="ORDER_SUBMISSION"></span>Order submission



To submit your Azure Reserved VM Instance order, do the following:

1.  Create a cart to hold the collection of catalog items that you intend to buy. When you create a [Cart](cart.md), the [cart line items](cart.md#cartlineitem) are automatically grouped based on what can be purchased together in the same [Order](orders.md).

    -   [Create a shopping cart](create-a-cart.md)​
    -   [Update a shopping cart](update-a-cart.md)

2.  Check out the cart. Checking out a cart results in the creation of an [Order](orders.md). 

    -   [Checkout the cart](checkout-a-cart.md)

## <span id="Get_order_details"></span><span id="get_order_details"></span><span id="GET_ORDER_DETAILS"></span>Get order details



Once you have created your Azure Reserved VM Instance order, you can retrieve the details of an individual order using the order ID, or get a list of orders for a customer. Note that there is a delay of up to 15 minutes between the time an order is submitted and when it will appear in a list of a customer's orders.​ 

-   To get the details of an individual order using the order ID. See, [Get an order by ID](get-an-order-by-id.md).

-   To get a list of orders for a customer using the customer ID. See, [Get all of a customer's orders](get-all-of-a-customer-s-orders.md).      

-   To get a list of orders for a customer by [billing cycle type](products.md#billingcycletype) allowing you to list Azure Reserved VM Instance orders (one-time charges) and annual or monthly billed orders separately. See, [Get a list of orders by customer and billing cycle type](get-a-list-of-orders-by-customer-and-billing-cycle-type.md). 

## <span id="Lifecycle_management"></span><span id="lifecycle_management"></span><span id="LIFECYCLE_MANAGEMENT"></span>Lifecycle management



As part of managing the lifecycle of your Azure Reserved VM Instances in Partner Center, you can retrieve information about your Azure Reserved VM Instance [Entitlements](entitlement.md), and get reservation details using the reservation order ID. For examples of how to do this, see [Get entitlements](get-a-collection-of-entitlements.md).   ​

## <span id="Invoice_and_reconciliation"></span><span id="invoice_and_reconciliation"></span><span id="INVOICE_AND_RECONCILIATION"></span>Invoice and reconciliation



The following scenarios show you how to programmatically view your customer's [invoices](invoice.md), and get your account balances and summaries that include one-time charges for Azure Reserved VM Instances.  

**Balance and payment​**    
To get current account balance in your default currency type that is a balance of ​both recurring and one-time (Azure Reserved VM Instance) charges, see 
[Get your current account balance](get-the-reseller-s-current-account-balance.md)

**Multi-currency balance and payment**​    
To get your current account balance and a collection of invoice summaries containing an invoice summary with both recurring and one-time charges for each of your customer's currency types, see [Get invoice summaries](get-invoice-summaries.md).

**Invoices​**    
To get a collection of invoices that show both recurring and one time charges, see [Get a collection of invoices](get-a-collection-of-invoices.md). ​

**Single Invoice​**    
To retrieve a specific invoice using the invoice ID, see [Get an invoice by ID](get-invoice-by-id.md).  ​

**Reconciliation**​    
To get a collection of invoice line item details (Reconciliation line items) for a specific invoice ID, see [Get invoice line items](get-invoiceline-items.md).  ​

**Download an invoice as a PDF**    
To retrieve an invoice statement in PDF form using an invoice ID, see [Get an invoice statement](get-invoice-statement.md).

