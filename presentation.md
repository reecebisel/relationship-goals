---
marp: true
theme: default
---
# Relationship Goals

---
# 3 Types of 
# Database relationships

---
# Many to Many
# Many to One
# One to One

---
# 6 Types in of Rails
# Associations

---
![bg right](https://www.fillmurray.com/g/155/300)
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
![bg left](https://www.fillmurray.com/g/155/300)

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
![bg right](https://www.fillmurray.com/g/155/300)

# has_one

```ruby
class Trainer < ApplicationRecord
  has_one :favorite, class: "Pokemon"
end

class Pokemon < Application
  belongs_to :trainer, as: :favorite
end
```
---
![bg right](https://www.fillmurray.com/g/155/300)

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
![bg left](https://www.fillmurray.com/g/155/300)

# has_many through

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
![bg right](https://www.fillmurray.com/g/155/300)

# has_many_and_belongs_to

Requires a join table called assemblies_parts

```ruby
class Assembly < ApplicationRecord
  has_and_belongs_to_many :parts
end

class Parts < ApplicationRecord
  has_and_belongs_to_many :assemblies
end
```
