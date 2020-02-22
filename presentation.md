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
