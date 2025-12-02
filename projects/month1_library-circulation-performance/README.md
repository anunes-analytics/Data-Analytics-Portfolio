\# Library Circulation Performance – SQL Analysis



\## 1. Objective



Analyze book circulation patterns for the fictional \*\*Twin Peaks Public Library\*\* over a one-year period to answer:



\- Which \*\*genres\*\* and \*\*age groups\*\* borrow the most?

\- How does \*\*circulation change over the year\*\* (seasonality)?

\- Which \*\*branch locations\*\* are the busiest?

\- Are there signs of \*\*underused collections\*\* (books that almost never get borrowed)?



The goal is to demonstrate practical SQL skills on a realistic library scenario: joining tables, aggregating data, and answering questions that matter to librarians and managers.



---



\## 2. Dataset



\- \*\*Source:\*\* Fictional dataset designed to resemble a real public library’s circulation system.

\- \*\*Main file (planned):\*\*

&nbsp; - `data/library\_loans\_sample.csv` – export of loan/checkout records.

\- \*\*Optional dimension tables\*\* (can be separate CSVs or just logical tables in SQL):

&nbsp; - `books`

&nbsp; - `patrons`

&nbsp; - `branches`



The idea is to treat these CSVs as if they were tables in a relational database.



\### Data grain



\- \*\*One row in `library\_loans\_sample` = one loan event\*\*  

&nbsp; (a patron checking out a specific book on a specific date).



\### Example schema



\#### `library\_loans\_sample`



\- `loan\_id` – unique ID for each loan.  

\- `book\_id` – foreign key to `books`.  

\- `patron\_id` – foreign key to `patrons`.  

\- `branch\_id` – foreign key to `branches`.  

\- `checkout\_date` – date of checkout.  

\- `due\_date` – date due.  

\- `return\_date` – date returned (can be `NULL` if not returned yet).  

\- `renewal\_count` – number of times the loan was renewed.  



\#### `books`



\- `book\_id`  

\- `title`  

\- `author`  

\- `genre` – e.g. `Fiction`, `Non-fiction`, `Children`, `YA`, `Mystery`, etc.  

\- `audience` – e.g. `adult`, `child`, `teen`.  

\- `publication\_year`  



\#### `patrons`



\- `patron\_id`  

\- `age\_group` – e.g. `child`, `teen`, `adult`, `senior`.  

\- `membership\_type` – e.g. `standard`, `student`, `staff`.  



\#### `branches`



\- `branch\_id`  

\- `branch\_name`  

\- `neighborhood`  



All data is \*\*fictionalized and generated\*\* as CSVs designed to behave like tables in a \*\*relational database\*\*. The project uses SQL queries against this schema to explore circulation patterns.



