# HOTEL SYSTEM
A hotel has rooms of three types: excellent, deluxe and magnificent. It has several rooms of each of these types, but all rooms of a particular type are priced the same and have the same facilities. Each room is situated on only one floor of the hotel, and a room is identified by the floor number followed by another two-digit number. Customers may book accommodation for a particular type of room for a single period or may make several bookings for several visits to the hotel. For each booking they would specify the names of the people who would be staying. Thus a person may wish to make a booking for themselves alone, or with a friend or possibly with a friend and child. In any case, no more than three people may share a room. The hotel assigns these people to an appropriate available room. Each type of room has a basic price and the cost of the room with several guests is calculated from this basic price, the type of room, and the number of guests sharing the room. Your system must be able to support the storage of the above information, including being able to track the guests included on a particular booking, and the guests allocated to each hotel room.

## Assumptions 
Customers: 
  - Can book one or more visits to the Hotel
  - Can be main customer, friend and child
  - Has a specific ID

Rooms:
  - Each type of room has a basic price
  - There are 3 types of rooms (Excellent, Deluxe, Magnificent)
  - They are identified by the floor number followed by room number
  - No more than 3 people can share the same room
  - Each room has a status (Booked / Not Booked)

Booking:
  - Check-in Date
  - Check-out Date
  - Has the ability to be canceled
  - Every customer can make one or more booking
  - Each booking includes the names of the customers
  - Each booking will be linked to the Rooms entity to check the availability

Floor:
  - Has 10 Excellent Rooms, 6 Deluxe Rooms and 4 Magnificent Rooms
  - The number of the floor will be used to identify each room
  - Each room is in one floor

Hotel:
  - Has 14 floors
  - Has 140 rooms
  - Max customer capacity is 420 :maple_leaf: 

Room Cost:
  - Depends on room type

Bill:
  - Gets calculated by adding room cost + length of stay + amount of people staying (based on age)
  - Age groups: 0-5 No cost, 5-16 +10%, adult +25%

## Entities 

- Customers (No more than 3 people in the room)
- Rooms (excellent, deluxe, magnificent)
- Booking (Many bookings for many visits possible)
- Floor (Location)
- Hotel 
- Room Cost (Based on room type)
- Bill (Calculated from number of guests and room type) 

## Attributes

| Customers                 |
| --------------------------|
| CustomerID (PRIMARY :key:)|
| CustomerName              |
| FriendName                |
| ChildName                 |


|Rooms                      |
|---------------------------|
|RoomNumber (PRIMARY :key:) |
|FloorNumber (FOREIGN :key:)|
|RoomType (FOREIGN :key:)   |


|Booking                   |
|--------------------------|
|BokingID (PRIMARY :key:)  |
|CheckinDate               |
|CheckoutDate              |
|CustomerID (FOREIGN :key:)|
|RoomNumber (FOREIGN :key:)|


|Floor                      |
|---------------------------|
|FloorNumber (PRIMARY :key:)|
|RoomNumber (FOREIGN :key:) |


|RoomCost   |
|---------- |
|RoomType   |
|Cost       |



|Bill                     |
|-------------------------|
|BookingID (FOREIGN :key:)|
|RoomCost (FOREIGN :key:) |