## Situation:

Imagine we are building a simplified version of Facebook. A user logs in and sees the newsfeed, which is comprised of posts made by their friends. In our data model we have the following:

- a `users` table with fields for `first_name`, `last_name`, `email`, `password`
- a `posts` table with fields for `content`, `user_id`
- a `friends` table with fields for `requester_id`, `acceptor_id`


## Steps to get Up and Running:

1. Download the sql file (slack)
1. At the terminal:
  - `createdb facebook_example`
  - `psql facebook_example -f [path_to_file]`
  - `psql -d facebook_example`


## Questions:

Write a `SQL` statement for each of the following directives:

1. Select all `users` records.  
`SELECT * FROM users;`

1. Select all `posts` records.  
`SELECT * FROM posts;`

1. Select the `first_name` and `email` for all `users` records.  
`SELECT first_name, email FROM users;`

1. Select the `first_name` and `email` for `users` with an `id` greater than `3`.
`SELECT first_name, email FROM users WHERE id > 3;`  

The notion of a "join" is what allows us to query across tables. Read this reference http://www.postgresql.org/docs/8.3/static/tutorial-join.html and write the following join queries:

1. Select the `first_name` and `last_name` from the `users` table, joined with the `content` for all `posts` belonging to that user.  
`SELECT users.first_name, users.last_name, posts.content FROM users, posts WHERE users.id = posts.user_id;`

1. Select the `first_name`, `last_name` for all sets of `friends`.  
`SELECT U1.first_name, U1.last_name, U2.first_name, U2.last_name FROM users U1, users U2, friends WHERE friends.acceptor_id = U2.id AND friends.requester_id = U1.id;`
