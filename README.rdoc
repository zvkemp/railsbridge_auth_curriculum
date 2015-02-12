== README

This README would normally document whatever steps are necessary to get the
application up and running.

Things you may want to cover:

* Ruby version

* System dependencies

* Configuration

* Database creation

* Database initialization

* How to run the test suite

* Services (job queues, cache servers, search engines, etc.)

* Deployment instructions

* ...


Please feel free to use a different markup language if you do not plan to run
<tt>rake doc:app</tt>.

```bash
$ rails new auth
$ cd auth
```

Initialize the git repo and check in the bare application:

```bash
$ git init
$ git commit -am 'initial commit'
```

Create a User model:

```bash
$ rails generate model User
```

Edit the migration file. We need a minimum of two fields to 'authenticate' a user, meaning we not only recognize a user, we can verify that they are who they say they are. The typical way of doing this is to accept an email and password.

Instead of storing a plain-text password, we'll keep them in the database in an encrypted format. The database column will be called `encrypted_password`:

```ruby
class CreateUsers < ActiveRecord::Migration
  def change
    create_table :users do |t|
      t.string :email
      t.string :encrypted_password

      t.timestamps null: false
    end
  end
end
```
