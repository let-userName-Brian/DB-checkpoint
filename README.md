##Readme isnt complete with images, but they are all in Image folder :)

##Database Checkpoint
##Data to be insterted
'''js
[
    {
        name: "Thailand",
        average_temp: 82,
        cost_of_flight: 765,
        has_beach: true,
        has_mountains: true
    },
    {
        name: "Minnesota",
        average_temp: 41,
        cost_of_flight: 235,
        has_beach: false,
        has_mountains: false
    },
    {
        name: "New Zealand",
        average_temp: 66,
        cost_of_flight: 433,
        has_beach: true,
        has_mountains: true
    },
    {
        name: "England",
        average_temp: 45,
        cost_of_flight: 290,
        has_beach: false,
        has_mountains: false
    },
    {
        name: "Tristan da Cunha",
        average_temp: 59,
        cost_of_flight: 1304,
        has_beach: true,
        has_mountains: true,
    }
]
 
//Airline Data:
[
  {
    name: "Spirit",
    destinations_flown_to: ["New Zealand", "Scotland"]
  },
  {
    name: "Lufthansa",
    destinations_flown_to: ["Tristan da Cunha", "Scotland", "Thailand"]
  },
  {
    name: "Delta",
    destinations_flown_to: ["Thailand", "Minnesota", "England", "Scotland"]
  },
  {
    name: "Southwest",
    destinations_flown_to: ["New Zealeand", "Tristan de Cunha", "Minnesota"]
  }
]

'''

##Destinations table 
    ![alt first](/Images/destinations-table.png)


##Airline table
   ![alt first](/Images/Airlines-table.png)


##Showing all destinations 
SELECT * FROM destinations;
    ![alt first](/Images/all-destinations-table.png)


##All destinations where you can swim at the beach
SELECT title FROM destinations WHERE has_beach = true;
    ![alt first](/Images/all-with-beach.png)

##All destinations where the average temperature is over 60 degrees.
SELECT title FROM destinations WHERE average_temp > 60;
    ![alt first](/Images/Average-temp-over-60.png)

##All destinations where you can swim at the beach AND go to the mountains.
SELECT title FROM destinations WHERE has_beach = true AND has_mountains = true;
    ![alt first](/Images/has-beach-and-mountain.png)

##All destinations where flights cost less than $500 and you can hike in the mountains.
SELECT title FROM destinations WHERE cost_of_flight < 500 AND has_mountains = true;
    ![alt first](/Images/cost-of-flight-500.png)

##Add an entry for The Bahamas, where the average temperature is 78, it has beaches but no mountains, and the flights cost $345.
INSERT INTO destinations (name, average_temp, cost_of_flight, has_beach, has_mountains) VALUES ("The Bahamas", 78, 345, true, false);
        ![alt first](/Images/destinations-table.png)

##Turns out, the cost of flights to New Zealand has increased! Update New Zealand's entry for flight cost to $1000.
UPDATE destinations SET cost_of_flight = 1000 WHERE title = "New Zealand";
        ![alt first](/Images/update-cost-of-flight-newZeland.png)

##Turns out, Minnesota isn't a vacation destination. Please delete it from the database
DELETE FROM destinations WHERE title = "Minnesota";


##When the data set was written, the author mistakently wrote "England" when they actually meant "Scotland". Please update that entry in the database.
UPDATE destinations SET title = "Scotland" WHERE name = "England";


##Create a join table that joins the airlines and the destinations tables by correlating which airlines fly to which destinations.
CREATE TABLE lets_go (
    airline_name INTEGER,
    location INTEGER
);


##All airlines that fly to New Zealand.
SELECT * FROM lets_go WHERE destinations_flown_to = "New Zealand";


##All airlines that do NOT fly to Scotland.
SELECT * FROM lets_go WHERE destinations_flown_to != "Scotland";


##All of the data for all vacation destinations.
SELECT name, average_temp, cost_of_flight, has_beach, has_mountains FROM vacations;
