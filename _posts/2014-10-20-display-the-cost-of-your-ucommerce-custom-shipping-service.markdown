---
layout: post
title:  "Displaying the cost of a uCommerce custom IShippingMethodService"
meta-title:  "Display the cost of an IShippingMethodService in Umbraco or Sitecore"
subtitle: "(without having to apply it to the basket)"
date:   2014-10-20 09:00:00
meta-description: Displaying the cost of a custom uCommerce shipping method without applying it to the basket
---

So you've built a custom shipping method service in uCommerce, using *IShippingMethodService*, as in this article:

<a href="http://docs.ucommerce.net/ucommerce/v6/extending-ucommerce/shipping-method-service.html" target="_blank">Building a Custom Shipping Method Service</a>

Often, you want to display the cost of each shipping method to the user during the checkout process, before they actually select them.

Wiggle does this well:

<img src="/img/checkout/wiggledelivery.png" class="full-width-image" alt="" />

But how do you do this when you're using a custom uCommerce *IShippingMethodService*, and you have your own logic for calculating the shipping costs of an order?

# Why you can't use ShippingMethod.GetPriceForCurrency()

Once you've told uCommerce to use your new *IShippingMethodService* for a shipping method..

<img src="/img/checkout/ucommerceshippingcommontab.png" class="full-width-image" alt="" />


.. you might assume that you can use *ShippingMethod.GetPriceForCurrency()* to get the cost to ship your order, like this:

{% highlight csharp %}

var allShippingMethods = TransactionLibrary.GetShippingMethods(country);
var currency = purchaseOrder.BillingCurrency;

foreach (var shippingMethod in allShippingMethods)
{
	var cost = shippingMethod.GetPriceForCurrency(currency);
}
{% endhighlight %}

Unfortunately, this uCommerce method only returns the first price from the shipping method's *Pricing* tab that matches the given currency:

<img src="/img/checkout/ucommerceshippingprices.png" class="full-width-image" alt="" />

It does not account for the calculations in your *IShippingMethodService*.

#Correctly get the cost for each shipping method

The correct way to do it is to manually call the *IShippingMethodService*, passing your current shipment.

At run-time we do not know which implementation of *IShippingMethodService* is set against a shipping method in uCommerce. Helpfully, uCommerce exposes this for us through the method *GetShippingMethodService()*.

Using this, we can simply get the relevant *IShippingMethodService* for
a given shipping method, construct a fake *Shipment* object (using our real basket of course) and pass it to the service to find out how much it
would cost to ship our basket with that shipping method.

{% highlight csharp %}
var purchaseOrder = TransactionLibrary.GetBasket().PurchaseOrder;
var allShippingMethods = TransactionLibrary.GetShippingMethods(country);

foreach (var shippingMethod in allShippingMethods)
{
  // Get the IShippingMethodService for this ShippingMethod
  var shippingService = shippingMethod.GetShippingMethodService();

  // Construct a fake shipping method to call the service with
  var shipment = new Shipment
  {
	  ShippingMethod = shippingMethod,
	  PurchaseOrder = purchaseOrder,
	  ShipmentAddress = purchaseOrder.BillingAddress
  };

  var shippingMethodPrice
 	 = shippingService.CalculateShippingPrice(shipment);
}
{% endhighlight %}

Of course, you might want some null checks and you will need to actually do something with the resulting price to display it, but you get the idea.

The default implementation of *IShippingMethodService* requires that you populate the *Country* in the *ShipmentAddress*, and the *PurchaseOrder* (as above), so make sure you
set those in addition to whatever your custom service needs, just in case a given shipping method is using the default service.

And that's it! Once you know how, it's fairly simple to display the costs of custom *IShippingMethodService*s to the user.
