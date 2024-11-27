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

## R2: Dataflow Diagram

## R3: Application Architechture Diagram

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


## R6: Project Management

