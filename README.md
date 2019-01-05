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
Order(id, buyer, seller, book.id, price, brate, srate, date, isFinish)
Report(id, reporter, Order.id, info)
Correct(id, corrector, info)
```

## Frontend Page Design

## Special Thanks
This Project is intended for Database Principle Curriculum, collaborated with ![sdycodes](https://github.com/sdycodes/DatabasePro).

Part of the Frontend pages are modified from a template downloaded from ![Template Website](www.cssmoban.com).
