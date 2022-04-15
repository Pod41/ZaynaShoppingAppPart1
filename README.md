# Zayna

## Table of Contents
1. [Overview](#Overview)
1. [Product Spec](#Product-Spec)
1. [Wireframes](#Wireframes)
2. [Schema](#Schema)

## Overview
### Description
Zayna is a shopping app similar to Amazon but using Parse as its backend.

### App Evaluation
[Evaluation of your app across the following attributes]
- **Category:** Shopping
- **Mobile:** This app would be primarily developed for mobile but would perhaps be just as viable on a computer, such as Ebay or other similar apps. Functionality wouldn’t be limited to mobile devices, however mobile version could potentially have more features.
- **Story:**  displays a list of available piece of cloth in the shopping app. User can choose whichever they want and place an online order.
- **Market:** Female adult-age group
- **Habit:** This app could be used as often or unoften as the user wanted depending on shopping habits, and what exactly they’re looking for.
- **Scope:** First we would start with posting availabe items for sale and customer based on needs, then perhaps they can place an online order. 

## Product Spec

### 1. User Stories (Required and Optional)

**Required Must-have Stories**

- [x] Customers can log in thier account
- [ ] Customers can see a list of available clooth for sale
- [ ] Customer can go to checkout and place an online order.
- [ ] Customer can see thier profile which includes information such as address, life-time orders and so on.

**Optional Nice-to-have Stories**

* Customers can add items to a bustket
* Customers can create an address book where they can store thier multiple addresses.
* Customers can cancel orders
* Customers can pay online for orders

### 2. Screen Archetypes

* Login screen - User signs up or logs into their account. Upon Download/Reopening of the application, the user is prompted to log in to gain access to their profile information to be properly matched with another person.
* Catalog screen - User can see a list of items for sale and select the quantity of the item and add it to a basket.
* Checkout screen - User can see a list of items in the basket and choose address and payment methods.
* Profile screen  - User can see thier profile which cosists of thier basic personal information along side with thier life-time orders and address books.

### 3. Navigation

**Tab Navigation** (Tab to Screen)

* Catalog screen
* Checkout screen
* Profile screen

**Flow Navigation** (Screen to Screen)

* Forced Log-in -> Account creation if no log in is available.
* Cloth Selection (Or Queue if Optional) -> send a request to server to send back a list of items for sale along side with each item's information.
* Checkout -> show a list of items in thebasket, give user selection of addresses from thier address book, and ask user to fill payment information.
* Profile -> request to a server to send back currentuser info along with thier life-time orders

## Wireframes
<img src="https://github.com/Pod41/ZaynaShoppingAppPart1/blob/master/Files/Untitled%20Diagram.jpg" width=600>

### [BONUS] Digital Wireframes & Mockups
<img src="https://github.com/Pod41/ZaynaShoppingAppPart1/blob/master/Files/9c0f69e95e9f4199a275d1cf89e9a2fe-0001.jpg" width=300><img src="https://github.com/Pod41/ZaynaShoppingAppPart1/blob/master/Files/9c0f69e95e9f4199a275d1cf89e9a2fe-0002.jpg" width=300>
<img src="hhttps://github.com/Pod41/ZaynaShoppingAppPart1/blob/master/Files/9c0f69e95e9f4199a275d1cf89e9a2fe-0003.jpg" width=300><img src="https://github.com/Pod41/ZaynaShoppingAppPart1/blob/master/Files/9c0f69e95e9f4199a275d1cf89e9a2fe-0004.jpg" width=300>
<img src="https://github.com/Pod41/ZaynaShoppingAppPart1/blob/master/Files/9c0f69e95e9f4199a275d1cf89e9a2fe-0005.jpg" width=300>

### [BONUS] Interactive Prototype
<img src="https://github.com/Pod41/ZaynaShoppingAppPart1/blob/master/Files/Zayna.gif" width=300>

## Schema 
[This section will be completed in Unit 9]
### Models
#### Post

   | Property      | Type     | Description |
   | ------------- | -------- | ------------|
   | objectId      | String   | unique id for the user post (default field) |
   | itemName      | String   | name of the dress |
   | description   | String   | describes item |
   | numberOfSold  | Number   | # of item sold |
   | rating        | Number   | rating of item rated by customers |
   | createdAt     | DateTime | date when post is created (default field) |
   | updatedAt     | DateTime | date when post is last updated (default field) |
### Networking
#### List of network requests by screen
   - Home Feed Screen
      - (Read/GET) Query all posts where user is author
         ```swift
         let query = PFQuery(className:"Post")
         query.whereKey("author", equalTo: currentUser)
         query.order(byDescending: "createdAt")
         query.findObjectsInBackground { (posts: [PFObject]?, error: Error?) in
            if let error = error { 
               print(error.localizedDescription)
            } else if let posts = posts {
               print("Successfully retrieved \(posts.count) posts.")
           // TODO: Do something with posts...
            }
         }
         ```
      - (Create/POST) Create a new order on a post
      - (Delete) Delete existing order
   - Create Post Screen
      - (Create/POST) Create a new post object
   - Profile Screen
      - (Read/GET) Query logged in user object
      - (Update/PUT) Update user profile image
