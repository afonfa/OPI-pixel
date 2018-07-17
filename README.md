# OPI-pixel

Grab your account specific checkout code from the Checkout code tab from Settings page. Your code should look like the code below:

<script type="text/javascript" data="olapic-checkout">
//==== Olapic Require: DO NOT CHANGE
var olapicRequireCheckoutScript=(function(oHead){var onError=function(){throw new URIError('Olapic checkout script could not be loaded');};return function(olapicScriptSrc,onLoadCallback){var oScript=document.createElement('script');oScript.type='text\/javascript';oScript.src=olapicScriptSrc;oScript.async=true;oScript.onerror=onError;if(onLoadCallback){if(oScript.addEventListener){oScript.addEventListener('load',onLoadCallback,false);}else if(oScript.readyState){oScript.onreadystatechange=function(){if(!this.readyState||this.readyState==='loaded'||this.readyState==='complete'){onLoadCallback();}};}else{oScript.attachEvent('load',onLoadCallback);}}
oHead.appendChild(oScript);};})(document.head||document.getElementsByTagName('head')[0]);

// ==== Checkout Code:
olapicRequireCheckoutScript('//photorankstatics-a.akamaihd.net/static/frontend/checkout/olapic.checkout.helper.js', function(){
    // Initialization
    olapicCheckout.init('XXXXX');

    // Add the Products: Product loop starts. This is where you will store each product purchased info
    olapicCheckout.addProduct('PRODUCT_ID', PRODUCT_PRICE);
    // Product loop ends.

    // Add the metadata/attributes
    olapicCheckout.addAttribute('transactionId', 'TRANSACTION_ID');
    olapicCheckout.addAttribute('currencyCode', 'CURRENCY');
    // Add Segmentation Values
    olapicCheckout.addSegment('SEGMENT_KEY', 'SEGMENT_VALUE');
    // Send the information
    olapicCheckout.execute();
});
</script>
Take the code above, place it into a click function like below (segmentation is removed & jQuery is the assumed JS framework in the below example):

$('.buy-now-class').click(function(e){
 var productId = "PRODUCT ID GOES HERE";
 var productPrice = "PRODUCT ID GOES HERE";

 olapicRequireCheckoutScript('//photorankstatics-a.akamaihd.net/static/frontend/checkout/olapic.checkout.helper.js', function(){
     // Initialization
     olapicCheckout.init('f48eeae508d1b1f3133df366679eb2b567bae5dc8058d69d679dc5cb140eb857');

     // Add the Products: Product loop starts. This is where you will store each product purchased info
     olapicCheckout.addProduct(productId, productPrice);
     // Product loop ends.

     // Add the metadata/attributes
     olapicCheckout.addAttribute('transactionId', 'TRANSACTION ID GOES HERE');
     olapicCheckout.addAttribute('currencyCode', 'CURRENCY CODE GOES HERE');
     // Send the information
     olapicCheckout.execute();
 });
});
Replace .buy-now-class with the appropriate button selector. productId,productPrice, Transaction ID, Currency Code will need to be mapped correctly as well.

$('.buy-now-class').click(function(e){

    var productId = "PRODUCT ID GOES HERE";
    var productPrice = "PRODUCT ID GOES HERE";

    olapicRequireCheckoutScript('//photorankstatics-a.akamaihd.net/static/frontend/checkout/olapic.checkout.helper.js', function(){
        // Initialization
        olapicCheckout.init('f48eeae508d1b1f3133df366679eb2b567bae5dc8058d69d679dc5cb140eb857');

        // Add the Products: Product loop starts. This is where you will store each product purchased info
        olapicCheckout.addProduct(productId, productPrice);
        // Product loop ends.

        // Add the metadata/attributes
        olapicCheckout.addAttribute('transactionId', 'Transaction ID');
        olapicCheckout.addAttribute('currencyCode', 'Currency Code');
        // Send the information
        olapicCheckout.execute();
    });

});
