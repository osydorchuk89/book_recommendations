# Book recommendation system

In this project, I built a book recommendation system using collaborative filtering. The project is based on the [video](https://www.youtube.com/watch?v=mrWzQy_Lddc) by Vik Paruchuri, founder of Dataquest. I followed the general guidelines suggested in the video, but also added some changes that I hope made the workflow more robust and the recommendations more relevant. Aside from the memory-based approach to collaborative filtering using similarities between users, I also user a memory-based approach using similarities between books and a model-based approach using matrix factorization.

## Data

In this project, I used the same [UCSD Book Graph datasets](https://sites.google.com/eng.ucsd.edu/ucsdbookgraph/home) that were analyzed in the video referenced above. The full body of datasets was collected in late 2017. I used the following datasets:

* [goodreads_books.json.gz](https://drive.google.com/uc?id=1LXpK1UfqtP89H1tYy0pBGHjYk8IhigUK) - complete information about the books available on Goodreads
* [goodreads_book_authors.json](https://drive.google.com/uc?id=19cdwyXwfXx_HDIgxXaHzH0mrx8nMyLvC) - information about book authors
* [goodreads_interactions.csv](https://drive.google.com/open?id=1zmylV7XW2dfQVCLeg1LbllfQtHD2KUon) - book ratings by users
* [book_id_map.csv](https://drive.google.com/uc?id=1CHTAaNwyzvbi1TR08MJrJ03BxA266Yxr) - dataset mapping book ids in the *goodreads_books* dataset to their Goodreads book ids

## Project workflow

I implemented the project in several steps:
1. Collected, analyzed, and organized the data about the books available on Goodreads.
2. Got the information about books that I read or would like to read from my Goodreads account.
3. Selected users with some degree of overlapping interest in books that I read or intent to read.
4. Implemented memory-based approach according to similary between users:
    - among the selected users, identified top 15 users that are most similar to my reading preferences;
    - selected the books with the highest average ratings and the highest number of ratings by the users most similar to me;
    - removed the books that I have already read or that are on my to-read list.
5. Implemented memory-based approach according to similary between items:
    - selected the books that I liked and found top three most similar books to each of them;
    - removed the books that I have already read or that are on my to-read list.
6. Implemented model-based approach by using matrix factorization algorithms:
    - iterated over possible hyperparameter combinations and identified the best ones;
    - fitted the algorithm to the dataset and predicted ratings I would give to various books;
    - selected the books with the highest predicted ratings.

As a result, I got the books that were recommended to me. 
