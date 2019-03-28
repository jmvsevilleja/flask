# flask

# SQLAlchemy
```
from sqlalchemy import create_engine
from sqlalchemy.orm import sessionmaker
from database_setup import Base, Restaurant, MenuItem
engine = create_engine('sqlite:///restaurantmenu.db')
Base.metadata.bind = engine
DBSession = sessionmaker(bind = engine)
session = DBSession()
```
# Create / Read
```
myFirstRestaurant = Restaurant(name= "Pizza Palace")
session.add(myFirstRestaurant)
session.commit()
session.query(Restaurant).all()
cheesepizza = MenuItem(name = "CheesePizza", description = "Made will all natural engredients", course = "Entree", price = "$8.99", restaurant = myFirstRestaurant)
session.add(cheesepizza)
session.commit()
session.query(MenuItem).all()
firstResult = session.query(Restraurant).first()
firstResulet.name
```
# Update / Read
```
veggieBurgers = session.query(MenuItem).filter_by(name = 'Veggie Burger')
for veggieBurger in veggieBurgers:
    print veggieBurger.id

UrbanveggieBurger = session.query(MenuItem).filter_by(id = 8).one()
UrbanVeggieBurger.price = '$2.99'
session.add(UrbanveggieBurger)
session.commit()
```
#Delete / Read
```
spinach = session.query(MenuItem).filter_by(name = 'Spinach Ice Cream').one()
print(spinach.restaurant.name)
session.delete(spinach)
session.commit()
```

# Web Server

