# odoo-india-training
For training
Business Requirement
-------------------------
With this module you will able to manage a proposal of a list of product to a customer


Detail Specification
----------------------

In odoo you will have a new object in the Sales Module called Proposal. A proposal (that extends mail follower, activity and will have the chatter similar like sale order)  will have a sequential code (like the sale order but with different number, prefix and suffix).
In the proposal you will have the salesman (user) , a customer (partner)  a pricelist and a list of line  It is similar to the sales order.

Each line will have 
Product_id
Lable(Description)
Qty proposed
Qty accepted
Price proposed (based on the price of the product and pricelist added)
Price accepted

The proposal will have 4 state and two total amount float fields (amount total proposed, amount total accepted):
draft
sent
confirmed
cancel

When you send the proposal (change state to sent) to the customer,  you will have an external link (with a generated token).
With this  external link a customer (without login) will see the proposal with a list of product with image,
the quantity proposed, and the price proposed (not editable) .
He will see two new box quantity accepted (prefilled with quantity proposed) and price accepted (prefilled with price proposed).
He will have the chatter to speak with the user 
He could change the quantity and the price. 
At the end he can accept or refuse the proposal. If he accept the quantity accepted and the price accepted will change in the proposal and so the total

the proposal view frontend should look like this -> https://tinyurl.com/y6s5kcav

In odoo backend if the salesman confirm this proposal it will change the state in confirmed became readonly (not editable) and 
automatically generate a sales order confirmed to that user and with the quantity accepted and price accepted.

Use Cases
------------
- Sale Person Create a Proposal Order
    - Customer - Asusteck
    - PriceList - Public Pricelist
    - Sales Person - Demo.
    - Proposal Lines
       - Product - Product A
       - Qty Proposed - 5
       - Qty Accepted - 5 (Default = Qty Proposed)
       - Price Proposed - 100
       - Price Accepted - 100 (Default = Price Proposed)
       
- Sales Person click on send button, will send a mail to customer with link of proposal order (token link) and state of the proposal order become sent
- customer open their mail and click on the link
- customer should redirect to the similar view  https://tinyurl.com/y6s5kcav - just like we have for Online Quotation, where customer can update the Qty accepted and Price Accepted
- now customer update the Qty Accepted to 4 and Price Accepted to 90 and Hit the Accept Button (once proposal get  accepted by customer, he should not more see the accepted or refuse button)
- If he accept the quantity accepted and the price accepted will change in the proposal order and so the total, so in backend for Product A, qty accepted change to 4 and price accepted change to 90, and accordingly total accepetd change to 360
- now sales person see the accepted price and qty, so if salesman confirm this proposal order , it wiill change the state in cofirmed and evrything become readonly and automatically generate a confirmed sale order to that useer and with the quantity accepted and price accepred.
