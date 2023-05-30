# SQL Zoo

It's time to dive into some SQL! You'll set up a database and start running
queries against it. Use the provided RSpec specs to test the results of the
queries you write.

It's worth noting that these exercises are originally from the [SQL Zoo
website][sqlzoo]. This website has a lot of extra hints that you may find
helpful if you're struggling to put queries together. Feel free to follow along
on their tutorial as you're doing these problems, but be warned: your problems
are a bit different, so don't let that trip you up.

[sqlzoo]: https://sqlzoo.net

## Learning Goals

By the end of this practice, you should be able to

* Write simple SQL queries using the `SELECT`, `FROM`, and `WHERE` clauses
* Write complicated queries using `JOIN` and subqueries
* Use `GROUP BY` with aggregate functions
* Use the various types of `JOIN`
* Write queries with self joins

## Getting Started

Clone the starter repo from the `Download Project` button below. To set up the database:

* Ensure the PostgreSQL app is running on your machine. (You should see an
  elephant in the menu bar.)
* Navigate to the repo's root directory and run the following:

```sh
bundle install
./import_db.sh
```

This will initialize the database and ensure that you are using the correct
versions of the RSpec and PG gems. If at any point your database becomes
corrupt, simply run `./import_db.sh` again to reset it.

After you've gone through this initial setup, you can begin going through the
files in your __lib__ directory, writing SQL code according to the guidelines in
each method definition. When you are ready to run the specs for a particular
section, you can use the following syntax:

```sh
bundle exec rspec spec/01_select_basics_spec.rb
```

If you'd rather run a single example from the test group, you can run it by
appending the line number, like so:

```sh
bundle exec rspec spec/01_select_basics_spec.rb:42
```

If you need to run sample queries, you can do so in pry or by adding method
calls to the bottom of your __lib/__ files and then running them.

**Please note:** Do **NOT** attempt any of the problems in the bonus files until
you have completed the problems in ALL of the regular files.

## Notes on tables

Some of the exercises involve joining tables together, and the purpose of some
columns may not be clear from the name alone. The aim of this section is to
clarify the structure of these tables.

### First joins (movie tables)

* `castings` is a "join table" that links movies to actors.
  * `castings.actor_id` is a foreign key pointing to an `id` in the `actors`
    table.
  * `castings.movie_id` is a foreign key pointing to an `id` in the `movies`
    table.
  * `ord` represents the position of the actor for the casting. The lead actor
    will have an `ord` of 1, with higher numbers representing less important
    roles.
* `movies.director_id` is a foreign key that points to an `id` in the `actors`
  table.

### More joins (music tables)

* `albums.asin` is the primary key for the `albums` table. Each album has a
  unique `asin`. (`asin` stands for "Amazon Standard Item Number".)
* `tracks.album` and `styles.album` are foreign keys that point back to
  `albums.asin`.
* `tracks.song` represents the name of a track.

### Self joins (bus tables)

* `routes.num` is, deceptively, not an integer or a float. Rather, it is a
  string that represents the "line number" of the route (i.e., the "32A" bus).
* `routes.pos` represents the position of a stop along the given line (`num`).
* `routes.stop_id` is a foreign key that points to an `id` in the `stops` table.
# W5D2
