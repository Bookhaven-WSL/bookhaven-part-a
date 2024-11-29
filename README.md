# T3A2-A Bookhaven

### Created in collaboration by Sophie Woolford, Wade Venz & Louis Denman

## R1: Project Purpose & Description

As a group who thoroughly appreciates a good read, but are in a digital age where the physical form factor of information is becoming less common, we wanted somewhere that our reading history could be stored. A digital personal library, so to speak, is something that we envision as a benefit to those who read anywhere around the world. When we researched current applications that tried to bring this concept to life, however, none really ticked all the boxes for the casual book enjoyer. Goodreads, whilst being owned by Amazon, has seen little support or development over its lifetime and has a range of issues that arn't appreciated by its users. Bookworm, whilst being about community and connectedness between likeminded individuals, can create a competitiveness that takes the focus off the enjoyment of reading and instead highlight how many books someone has read. Storygraph delves deep into the data and trends of an individuals reading habits, Bookly focuses on building reading habits, Readerly focuses on the reviewing of books, the list goes on.

In summary, we found that there is a range of services out there for the casual reader, but none that keep it simple. None that keep it about the individual reader, and keep it simply about the books they have read and want to read. As a result, our team endevours to make the perfect, simple digital library web application that is built for the casual individual reader. The web app will be an aesthetically pleasing, responsive, and allow users to:

- Easily sign up & log in
- Create a list of books that the reader has read
- Create a list of books that the reader would like to read
- Allow the reader to search for books to add to the above two lists mentioned
- Allow the reader to put a simple rating on books they have read if they choose
- Display recommendations for the reader based on what they have read previously
- Allow the reader to add custom book entries
- Enable child accounts that stop the addition of inappropriate books

Our team is utilising the MERN stack (MongoDB, Express, React, Node) framework for the creation of our web app, along with a range of npm package dependancies including:
- Jsonwebtoken
- Dotenv
- Bcrypt
- Mongoose
- Cors
- Nodemon

For deployment, we will be using netlify for the front-end, along with render for the back-end. Project management is conducted on Trello, while version control is handled by Git and Github. Shared file storage is handled by Google Drive.

## R2: Dataflow Diagrams

Below are representations of data flow for the virtual bookshelf application, BookHaven. The diagrams are layers that build on the high level application architecture diagram, and utilise the notation standard of 'Yourdon and Coad', where external entites are represented in rectangles and processes in circles. 

### Virtual Bookshelf - Layer 1

![DFD Layer 1](./assets/bookhaven_dfd_layer1.png)

### Auth Data Flow - Layer 2

##### Sign-up User

![Auth Signup Layer 2](./assets/bookhaven_dfd_layer2_auth_signup.png)

1. A POST request is sent by the user to the `/auth/signup` endpoint with user information such as name, email & password. 
2. User details will be passed to a function to handle user registration. First user details will be validated for proper format and the email provided will be checked to verify that it is unique. The password will also be hashed for extra security.
3. If validation criteria is not met or the email is not unique, an error message will be sent back to the client. 
4. User will be saved with a userId, user details and the hashed password to the database.
5. User ID and email passed to a function to generate a JSON web token or JWT.
6. The JWT is passed back to the user on the front end to be stored and utilised for authentication. 




##### Login User

![Auth Login Layer 2](./assets/bookhaven_dfd_layer2_auth_login.png)

1. A POST request sent to the `/auth/login` endpoint with email and password. 
2. Details are sent to Backend Server, where a function to handle login is located within the Auth controller. Details are initially checked against validation format, and if criteria isn/t met, an error message is sent back to the user. 
3. Email/userId is sent to be checked within the database for existing records using an async function
4. If email/userId exists within database records, the document with the user details and hashed password is sent back to the server for use within the handleLogin() function.
5. The hashed password received from the document retrieved is verified, if not verified, an error is sent back to the user. 
6. A JWT is generated via a function with userId and email passed as parameters.
7. The JWT is then returned to the user on the front end for storage, alongside the userId, the saved preferences for UI/UX and any permissions associated with that user. The JWT is sent as a header for all further user requests within the application until it expires as specified when the token is generated. 

### User Data Flow - Layer 2 **Optional Functionality** 

##### Update User

![Update user](./assets/bookhaven_dfd_layer2_update_user.png)

1. PUT/PATCH requested by user, sent with a _id to server
2. Server receives request and validates, returning an error if occurs.
3. Query is sent to the database by the server to update data.
4. The database receives and executes the request sending a response.
5. Response is returned to user. The front end React app then saves the changes in state.  

##### Delete User

![Delete user](./assets//bookhaven_dfd_layer2_delete_user.png)

1. DELETE requested by user, sent with a _id to server
2. Server receives request and validates, returning an error if occurs.
3. Query is sent to the database by the server to delete data.
4. The database receives and executes the request sending a response.
5. Response is returned to user. The front end React app then saves the changes in state.

### Bookshelf Interaction - Layer 2

##### Adding a new book to shelf

![Add a Book](./assets/bookhaven_dfd_layer2_add_book.png)

1. The client decides to add a new book to virtual bookshelf by creating a search query.
2. A request will be sent to an external API asynchronously to search for a book that meets criteria inputted by user. Books can searched by title, author, or id's such as ISBN.
3.  If found in the API the book will be returned in JSON format, else an error will be caught. 
4. Error or book data is returned.
5. The details in the book record will be passed to another function that will handle its storage in the database. 
6. The book is saved to the database associated with the User collection.
7. The book is returned to the front end for the user and saved by the React app. 


##### Find a new book

![Find a book](./assets/bookhaven_dfd_layer2_find_book.png)

1. GET request is triggered by user on front end and sent to the server. 
2. A function to handle to handle the fetch request receives the requests and handles validation. The server then sends a query to the API.
3. The API receives the request and returns an array of book objects based on parameters. 
4. The information is sent back to the front end for the user and saved by the React app for further interaction by the client, potentially to be added and saved to the database.  

##### Recommendations

![Recommended](./assets/bookhaven_dfd_layer2_recommended.png)

1. A fetch request is triggered by user on the front end. 
2. A function to handle recommendations in the server receives the GET request. This function handles both async functions for database and API request. 
3.  This function handles the asynchronous call to the database to collect data from saved books utilising userId to collect associated book documents. 
4. Database receives the request and sends back an array of book objects.
5. The array of book objects is then sent to the handle recommends function to isolate query parameters for a request to the API, based on the data collected from the database.
6. The parameters from handle recommendation are sent to the second async function to request books from the API. 
7. The request is sent to the API to collect book data matching parameters.
8. Return an array of book objects to the server. 
9. The handle recommend function will further validate the data to be sent back to the front end.
10. A final array of book objects will be sent to the front end and saved in state. 

##### Update Book

![Update book](./assets/bookhaven_dfd_layer2_update_book.png)

1. PUT/PATCH requested by user, sent with a _id to server
2. Server receives request and validates, returning an error if occurs.
3. Query is sent to the database by the server to update data.
4. The database receives and executes the request sending a response.
5. Response is returned to user. The front end React app then saves the changes in state. 

##### Delete Book

![Delete book](./assets/bookhaven_dfd_layer2_delete_book.png)

1. DELETE requested by user, sent with a _id to server
2. Server receives request and validates, returning an error if occurs.
3. Query is sent to the database by the server to delete data.
4. The database receives and executes the request sending a response.
5. Response is returned to user. The front end React app then saves the changes in state

## R3: Application Architechture Diagram

A high level diagram for the archtiecture of the application. 

![Architecture Diagram](./assets/bookhaven_architecture_diagram.png)

## R4: User Stories

As recommended by the assessment criteria, the intial user story format used was the **As a [persona], I [want], so [that].**

To begin, an initial iteration of users stories was created to address the features that we intend to implement within the web app, as seen below:

*Iteration 1:*

- My name is Jill, and as someone who enjoys reading, I want to track which books I’ve read, so I can talk about it with other friends who like reading.
- My name is John, and as someone who reads here and there, I want to make a list of new books to read, so that I can get more into reading.
- My name is Jeff, and as someone who passionately reads, I want to be able to rate books that I’ve read before, so that I can see what I thought of each book.
- My name is Jack, and as someone who has a grandpa that loves reading, I want to be able to make a simple account for him that is easy to add books he’s read too, so that he can remember which ones he has read.
- My name is Janette, and as someone who likes reading to relax, I want to have new books recommended to me, so that I can find more books that are relaxing to read.
- My name is Jeremy, and as someone who has young children that enjoy reading, I want my kids not to be able to see books that are inappropriate, so that they then go read them and learn bad things.
- My name is Jesiah, and as someone who likes studying old texts, I want to be able to add custom books that otherwise wouldn’t show up.

This set of users stories addressed the functionality of the app, but would benfit from some further depth about the user, as well as specificity about what it is they want to achieve. As a result, the individual users were given some more depth and background:
- *Jill:* Jill is a 29 year old woman who has been a bookworm since she was a child. Whenever she has free time, her favorite activity is to go for a walk to the park or beach if she is nearby, and read her book for as long as she can. She moved away from her high-school friends who also enjoy reading, but catches up with them once or twice a year.
- *John:* John is a 31 year old man who works a hard labor job. He gets up early for work to provide for his wife and young child, but feels the effects of this work over the years starting to take effect on him. He has never been a big reader, but wants to start doing so consistently, as he is trying to read books on financial freedom and other finance/self-improvement topics.
- *Jeff:* Jeff is a 19 year old student who studies a bachelor of arts with a major in English literature. He thoroughly enjoys the process of analyzing/comparing different books and other written works. Whenever he sees his classmates or professor after class, he loves discussing personal takes on particular authors' pieces of work, and debating the quality of pieces that are covered in class.
- *Jack:* Jack is a 22 year old man who works hard to provide for himself and his grandparents, who have raised him for the better part of his life. He has never been a big reader himself, but his grandpa loves reading. Unfortunately, his grandpa in his old age has begun to have memory problems, and sometimes picks up books only to find that he has already read them and knows the story. Jack feels sorry for his grandpa, but doesn’t know a good system to help him.
- *Janette:* Janette is a 32 year old woman who was diagnosed with anxiety in her late 20s. Looking back, it was obvious this was the case, she despised having to go out of the house for anything; getting groceries; going to school or university; previous commutes to the office; even going to and from friends' places. These days she is able to work a remote job from the comfort of her own home, but when she does have to journey out on occasion, she reads to calm down before and after her journey.
- *Jeremy:* Jeremy is a 38 year old man who is the proud father of 1 boy and 2 girls under the age of 10. Like their parents, they all love reading, and go through lots of books in a year. Unfortunately, when Jeremy was younger he found some books that contained inappropriate content, of which took him a while to work through. He doesn’t want that to happen to his kids, but loathes the process of having to check through every book for any inappropriate content, given his busy schedule and the rate at which his children read.
- *Jesiah:* Jesiah is a 20 year old who loves history. During high-school, he would not do well in his other class, but in both modern and ancient history would score 100%. In particular he had a fascination for older literature and texts, and loves to study as much as he can get his hands on.

With the further persona development established, the user stories could be revised with more detail and depth, so that they become even more useful and clear:

*Iteration 2:*

- My name is Jill, and as someone who has enjoyed reading since childhood, I would like to be able to keep a record of all the previous books I have read, so that when I catch up with my childhood friends who also enjoyed reading we can talk about all the books we have read together.
- My name is John, and as someone who reads occasionally but is trying to get more consistent, I would like to be able to make a list of books that I want to read in the future, so that I can look at my list and stay motivated to keep reading the book that I am on and get excited for the books I plan to read next.
- My name is Jeff, and as a passionate reader who has read a large number of books and had a unique opinion on most of them, I would like to be able to create a rating for each book that I’ve read, so that I can easier recall my opinions of particular books and weigh in my opinions/thoughts in group discussions such as when I’m at book clubs or conventions.
- My name is Jack, and as someone who has a grandpa that loves reading, but is getting to an age where he struggles to use technology and remember some things, I would like to be able to make a simple account for my grandpa that he is able to easily use and log in to, so that he can have help remembering which books he has read and wants to read.
- My name is Janette, and as someone who has anxiety and doesn’t like browsing the library or being in public places for long amounts of time, I would like to have books be recommended to me based upon what I have read before, so that I know what books I am looking for before I go in the library and can make the trip as quick as possible.
- My name is Jeremey, and as someone who has children that are under 10 years of age and read lots for a hobby, I would like a type of account that does not allow books that aren't appropriate to be displayed for users to look at, so that my children do not find a book that I don’t check and it ends up being inappropriate.
- My name is Jesiah, and as someone who enjoys studying history and lots of ancient texts from different cultures, I would like to be able to make custom book entries that correspond with these texts that I study, so that I have a record of which texts I have read and intend to research in the future.


## R5: Wireframes
For the pages that store each collection of books - ‘Reads’ and ‘TBR’ (To Be Read) - that the user has saved, we wanted to emulate the appearance of bookshelves with the simplistic design, displaying the front cover of the books with minimal other information. To display more information about a book, the user clicks (mobile) or hovers over (desktop) the relevant book. This will display the book’s title and author, as well as the user’s rating on the ‘Reads’ page.

With the simplistic design of the pages that display the “bookshelves”, we decided to make separate pages for the ‘search‘ and ‘recommendations’ pages. This was because we wanted to display more information per book on these pages, so by making them separate we were able to keep the simplistic design of the “bookshelf pages.”
Once this decision was made we needed to add more buttons to the top of the page, and since this made the number of buttons four, we decided that a navigation bar was a better option, to keep the buttons organised. A search option was also added on the bar for the ‘Reads’ and ‘TBR’ pages so that a user quickly and easily can locate a book they have previously stacked there.

### Mobile version
![Mobile - reads](https://github.com/user-attachments/assets/35a94b0b-64f1-4cc0-b0b5-0f711910bbcf)
![Mobile - menu expanded](https://github.com/user-attachments/assets/a2e3b853-b9f4-4a5d-939a-0137abfc5a40)
![Mobile - tbr](https://github.com/user-attachments/assets/98350dd0-8fd3-44d2-9d08-ceeafaf4d42f)
![Mobile - add](https://github.com/user-attachments/assets/132497fa-7882-4f9d-8650-294e43ad4100)
![Mobile - recs](https://github.com/user-attachments/assets/6b20ac23-728b-47d1-81d1-13c0387d5abd)
![Mobile - error message](https://github.com/user-attachments/assets/bdaf6a62-2dd2-454d-9633-ef93515dd211)
![Mobile - sign up-in](https://github.com/user-attachments/assets/adbc859c-01d7-4286-8f78-5a6c50714723)

### Desktop version
![Desktop - reads](https://github.com/user-attachments/assets/5566fdf4-ce79-4f27-92de-0a3986c1c133)
![Desktop - title selected](https://github.com/user-attachments/assets/0efabee2-42c5-4bc2-835b-516d0f949fa5)
![Desktop - search title](https://github.com/user-attachments/assets/da5d1b4b-1d30-4d16-aeed-513e2a6a4368)
![Desktop - tbr](https://github.com/user-attachments/assets/ed1fb32e-5cfe-453e-a6e8-66b5db1ddb78)
![Desktop - add](https://github.com/user-attachments/assets/e7cd2b51-17f2-461c-97ce-3e887da71bef)
![Desktop - recs](https://github.com/user-attachments/assets/3d997f59-9dc5-403a-82cc-7ba73d8cb3c2)
![Desktop - error message](https://github.com/user-attachments/assets/e188492f-6717-4337-9b41-f6f4c70e2588)
![Desktop - sign up-in](https://github.com/user-attachments/assets/6b7bcd41-b9c3-4ce6-bcb8-2efad8ff701a)


## R6: Project Management

For our team planning and management, we choose Trello as the tool of choice, tracking our agile fortnight long sprints. Within each sprint, we conducted 4 meetings/stand-ups (2 per week), and continued to communicate via discord in the meantime. Below is the progression of our Trello board from the beginning to the end of T3A3 Part A:

### Sprint 1

#### Meeting 1

![Sprint 1, Meeting 1](./docs/Trello/Trello_Sprint1_Meeting1.png)

#### Meeting 2

![Sprint 1, Meeting 2](./docs/Trello/Trello_Sprint1_Meeting2.png)

#### Meeting 3

![Sprint 1, Meeting 3](./docs/Trello/Trello_Sprint1_Meeting3.png)

#### Meeting 4

![Sprint 1, Meeting 4](./docs/Trello/Trello_Sprint1_Meeting4.png)

### Sprint 2

#### Meeting 1

![Sprint 2, Meeting 1](./docs/Trello/Trello_Sprint2_Meeting1.png)

#### Meeting 2

![Sprint 2, Meeting 2](./docs/Trello/Trello_Sprint2_Meeting2.png)
