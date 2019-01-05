# Transaction Platform for Textbooks
An Online DJango Project for Textbook Transactions

## Developing Environment
* Python 3.6.5
* DJango 2.0.7

## On Demands
To meet the need of textbook exchange in high school, we designed a online transaction system for new and second-hand textbooks.
Also, we can recommend certain books from the booklist, if the user fills up the department field.

| Three Submodules | Functions |
| - | :-: |
| ☁ User System | Including `Normal User`, `Retailer` and `Administrator` |
| ✉ Transaction System | Core Transaction and Grading System |
| ✎ Operational System | Booklist Corrections and Dispute Settlement |

## Relational Database Design
### Determining Data to be Stored
We designed `8` entities in this project.

| Entity Name | Usage |
| :-: | :-: |
| BOOK | Representing Textbooks |
| USER | Superclass for subclass `NRML`(Normal User), `RTLER`(Retailer) and `ADMIN`(Administrator) |
| RLIST | Recommended List for Textbooks |
| ORDER | User Order Details |

### Determining Data Relationships
Relations between entities can be summarized as correct, report, own, rate and transaction.

| Relations | Usage |
| :-: | :-: |
| CORRET | Information User Given for Booklist Corrections |
| REPORT | Report an Issue on Specific Order |
| OWN | User Currently Own this Textbook |
| RATE | Buyer and Seller's Rate on Specific Order |
| TRANSACTION | Buy a Textbook |

### Entity-Relationship Model (E-R Diagram)
![image](https://github.com/BXYMartin/SQL-TextbookDB/blob/master/imgs/E-R_Diagram.png)

### Normalization
The Relationship Model is normalized to 3NF.

### Apply to MySQL
``` SQL
User(name, password, credit, info, isNormal, department, grade, sale)
Admin(name, password, info)
Book(id, name, cover, info, price, owner)
RecommendList(names, department, grade)
Order(id, buyer, seller, Book.id, price, brate, srate, date, isFinish)
Report(id, reporter, Order.id, info)
Correct(id, corrector, info)
```

## Frontend Page Design
Main Website is designed as a Backend Control Panel.
![image](https://github.com/BXYMartin/SQL-TextbookDB/blob/master/imgs/Main.png)
### Info Page
#### Normal User and Retailer

Info Page contains all essential information for user (except for admin). Details including orders, sales, issues, shopping cart and ratings are displayed in this page.

![image](https://github.com/BXYMartin/SQL-TextbookDB/blob/master/imgs/Cart.png)


To bypass the transaction process without involving any purchase, we add a BYPASS PURCHASE button in the leftmost bottom of the QR code. Dynamic QR code is not implemented in this example.
<img src="https://github.com/BXYMartin/SQL-TextbookDB/blob/master/imgs/Purchase.png" width="50%" height="50%" align="middle" />
Retailers are not permitted to purchase any books, so their shopping cart would always be empty, and their order list is also empty.

<img src="https://github.com/BXYMartin/SQL-TextbookDB/blob/master/imgs/Info.png" width="50%" height="50%" align="middle" />


#### Administrator
Administrator should mainly focus on solving issues. 
![image](https://github.com/BXYMartin/SQL-TextbookDB/blob/master/imgs/Issue.png)
After inspecting the issue, administrator can handle it.
![image](https://github.com/BXYMartin/SQL-TextbookDB/blob/master/imgs/Handle.png)
And also, settle the dispute.
![image](https://github.com/BXYMartin/SQL-TextbookDB/blob/master/imgs/Settle.png)

### Market Page
Users can visit the market by simply searching or through recommended booklist.
![image](https://github.com/BXYMartin/SQL-TextbookDB/blob/master/imgs/Shopping.png)
### Order Page
After purchasing a textbook, it will appear in order list.
![image](https://github.com/BXYMartin/SQL-TextbookDB/blob/master/imgs/Order.png)
If the transaction is complete, the order will show up as finished and waiting for buyer and seller to rate.
![image](https://github.com/BXYMartin/SQL-TextbookDB/blob/master/imgs/Finished.png)

### Other Pages
Editing the recommended list.
![image](https://github.com/BXYMartin/SQL-TextbookDB/blob/master/imgs/Edit.png)


## Special Thanks
This Project is intended for Database Principle Curriculum, collaborated with ![sdycodes](https://github.com/sdycodes/DatabasePro).

Part of the Frontend pages are modified from a template downloaded from ![Template Website](www.cssmoban.com).
