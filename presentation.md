---
marp: true
theme: totez
---

# Relationship Goals

---
<!-- _class: invert -->
# 3 Types of  
# Database 
# Relationships

---
# Many to Many
# Many to One
# One to One

---
<!-- _class: invert -->
# 6 Types in of Rails
# Associations

---
# belongs_to

one to many relationship

```ruby
class Author < ApplicationRecord
end

class Books < AppliicationRecord
  belongs_to :author
end
```

---
<!-- _class: invert -->
# has_many
Many to one

```ruby
class Author < ApplicationRecord
  has_many :books
end

class Books < ApplicationRecord
end
```

---
# has_one

```ruby
class Trainer < ApplicationRecord
  has_one :favorite, class_name: "Pokemon"
end

class Pokemon < ApplicationRecord
  belongs_to :trainer, as: :favorite
end
```

---
<!-- _class: invert -->
# has_one through

```ruby
class Supplier < ApplicationRecord
  has_one :account
  has_one :account_history, through: :account
end

class Account < ApplicationRecord
  belongs_to :supplier
  has_one :account_history
end

class AccountHistory < ApplicationRecord
  belongs_to :account
end
```

---
# The Many
# Many to Many

---
<!-- _class: invert -->
<style scoped>
  code {
    font-size: 0.5em;
  }
</style>

# has_many through
Join table has other attributes from foreign keys

```ruby
class Trainers < ApplicationRecord
  has_many :teams
  has_many :pokemen, through: :teams
end

class Teams < ApplicationRecord
  belongs_to :trainer
  has_many :pokemen
end

class Pokemon < ApplicationRecord
  has_many :teams
  has_many :trainers, through: :teams
end
```

---
## has_many_and_belongs_to

Requires only join table w/o extra attributes

```ruby
class Assembly < ApplicationRecord
  has_and_belongs_to_many :parts
end

class Parts < ApplicationRecord
  has_and_belongs_to_many :assemblies
end
```

---
<!-- _class: invert -->
# polymorphic: true

```ruby
class Pictures < ApplicationRecord
  belongs_to :imageable, polymorphic: true
end

class User < ApplicationRecord
  has_many :pictures
end

class Product < ApplicationRecord
  has_many :pictures
end
```

---
# inverse_of

```ruby
class Author < ApplicationRecord
  has_many :books
end

class Book < ApplicationRecord
  belongs_to :book
end
```

---
<!-- _class: invert -->
<style scoped>
  code {
    font-size: 0.5em;
  }
</style>

# Bi-Directional 
# Relationships

```ruby
# Without
a = Author.first
b = a.books.first
a.first_name == b.writer.first_name # => true
a.first_name = 'David'
a.first_name == b.writer.first_name # => false
# With
a = Author.first
b = a.books.first
a.first_name == b.writer.first_name # => true
a.first_name = 'David'
a.first_name == b.writer.first_name # => true
```

---
# END