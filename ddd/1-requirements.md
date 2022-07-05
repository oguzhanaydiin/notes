# Applied Domain-Driven Design (DDD), Part 0 - Requirements and Modelling

## In this part, we are going to do:
* Identify User Stories 
* Identify the Nouns in the user stories 
* Identify the Verbs in the user stories 
* Put together object interaction diagram
* Put together object responsibilities diagram 
* Put together class digram UML showing only interesting interactions 

## So here are made up user stories:
* As a customer I want to be able to put products that I want to purchase in to the shopping cart so that I can check out quickly later on
* As a customer I want to see the total cost all for all of the items that are in my cart so that I see if I can afford to buy everything 
* As a customer I want to see the total cost of each item in the shopping cart so that I can re-check the price for items
* As a customer I want to see the total cost for all of the items in the shopping cart with total tax 
* As a customer I want to be able to specify the address of where all of the products are going to be sent to
* As a customer I want to be able to add a note to the delivery address so that I can provide special instructions to the postman
* As a customer I want to be able to specify my credit card information during check out so that I can pay for the items
* As a customer I want system to tell me how many items are in stock so that I know how many items I can purchase 
* As a customer I want shopping cart to check that items are still available for purchase during a check out so that I can still purchase items that are in the cart
* As a customer I want to receive order confirmation email with order number so that I have proof of purchase 
* As a customer I want to specify invoice address for the order so that I can receive invoice for the order

## Now I am going extract nouns and verbs from the stories above. I am looking for the nouns that will become my main objects and not the attributes.

## Nouns: 
* Customer
* Item
* Order
* Shopping Cart
* Address
* Invoice
* Delivery
* Tax
* Credit Card Information 

## Verbs:
* Put products in to the shopping cart 
* See total cost for all of the items
* See total cost for each item
* See total tax for my country 
* Specify delivery address
* Specify delivery note for delivery address
* Specify invoice address
* Receive invoice for the order
* Sent invoice
* Specify credit card information 
* Pay for the items
* Tell me how many items are in stock
* Check that items are still available during check out
* Receive order confirmation email 

By using above nouns and verbs we can put together a diagram such as this:

Object Interaction Diagram:
![image](https://user-images.githubusercontent.com/46647059/177317627-f155e2f4-ee31-49d4-9511-a3010d8e922f.png)

Once we have object interaction diagram we can start thinking about object responsibilities. One of the most common mistakes is to push responsibilities on to the actor object i.e. Customer. We need to remember that objects must take care of themselves and objects need to be closed for direct communication and that you need go through the functions to communicate with them.

So let's follow above approach and assign responsibilities:

Object Responsibilities Diagram:
![image](https://user-images.githubusercontent.com/46647059/177318013-f79650c2-6d48-40bb-8d69-3a20871604e8.png)


Now that we have object interaction and responsibilities diagram in place we can start thinking about lower level UML class diagram:

UML Diagram:
![image](https://user-images.githubusercontent.com/46647059/177318049-4ab57dd6-6dda-4b95-bc0b-53967281048a.png)


Figure 3 shows methods, class names, dependencies, interfaces and composition. I've took a bit of time and reflected only on the most complex / interesting parts of the model. I will worry about attributes and other details later on, detail will naturally emerge when I start coding. Figure 3 is suppose to be a rough sketch, that is all, teams can whiteboard Figure 3 during a meeting, take a picture and distribute it to everyone in the team and get on with the actual coding. After a week or so picture will be forgotten and the parts of the above model (that have been useful) will live and breath in the actual code.

Now my made up user stories can be modelled in my many different ways and Figure 3 is just my interpretation of it. Key thing is to think about what you are building first, don't just jump in and start coding and don't get carried away with detail either (attributes, constructors, etc) focus on interesting and complex parts first.

## Summary:
Don't start doing anything until you have requirements, if you don't have a BA in the company that's fine, you will have to do BA's job and identify requirements first.
Don't just jump in to the code soon as you have requirements, put together object interaction and responsibilities diagrams first. 
When you have identified your objects, interactions and responsibilities use UML class diagrams to put together a draft model (whiteboard sketch will do).
Don't try to model the reality of the world, model the reality of your organisation. Different companies will have different objects, in one company "address" might be an object and you might have "address type" coming of it (invoice, shipping, etc), in another company there will be "invoice address", "shipping address" and "seller address" object, that company might need these objects as these objects will inherit from the base "address" object. Remember it is all about your business domain and not the actual "reality".
