# the_open_tag_technical_assignment
**A Postman collection for The Open Tag technical assignment: OpenQL The Star Wars**

This collection was created to make such tasks with swapi-graphql and Postman (as tool):

1) Retrieve and store all species that have participated in the first movie of
Star Wars “A New Hope".

2) Obtain “name”, “birthYear”, “homeWorld”, “eyeColor” for the person, which
is “Droid”.

3) Obtain the totalCount of all people that have participated in the movie and
the unique “id”, “name” and “gender” for each of them.

4) Using the information received by previous request, obtain the “name”,
“birthyear”, “homeWorld”, “eyeColor”, starshipName for the person with
unique id = 4.

Endpoint used: https://swapi-graphql.netlify.app/.netlify/functions/index

This collection is intended to be run through the Postman Collection Runner.
It includes requests, variables and basic tests.

Please, import file "Star Wars.postman_collection.json" to Postman as collection.
Then you should use Collection Runner for this collection or send requests separately (please, run them in given order).

In case of using Collection Runner, you should set delay to be sure that for each request you got response. For example, you can use 300ms delay.

At the end of the run you should check Collection Variables tab to see the value of variable named "speciesList". It contains all species list from the first movie of Star Wars "A New Hope". As plan B, please check Console for the record "The list of species for A New Hope: ...".

**Requests description**

To achieve task 1 goal were created requests:

1. GetFirstFilm: to get from "allFilms" its first value, which means the first movie in this case. Also test verifies that response contains "A New Hope" string. An ID of this movie is stored in "newHopeId" variable. Also a variable "speciesList" is cleared to be sure that is doesn't store an old value.
2. GetFirstFilmSpecies: to get from "film.speciesConnection", using "newHopeId", all species related to the first movie ("name" and "ID"). The list of species are stored then in "speciesList" variable. Also an ID for "Droid" is stored in "speciesDriodId" variable.

To achieve task 2 goal was created request:

1. GetPersonDroid: to get from "person", using "speciesDriodId", all needed parameters for "Droid": “name”, “birthYear”, “homeWorld”, “eyeColor”.

To achieve task 3 goal was created request:

1. GetCharactersInFilm: to get from "film.characterConnection", using "newHopeId" variable, all needed parameters: "totalCount" of all people that have participated in the movie and the unique “id”, “name” and “gender”. Also the ID of the 4th record is stored in "fourthPersonId" variable.

To achieve task 4 goal was created request:

1. GetPersonUniqueId4: to get from "person", using "fourthPersonId" variable, all needed parameters: “name”, “birthyear”, “homeWorld”, “eyeColor”, starshipName for the person with unique id = 4. Also all variables except speciesList are cleared at this step.

**Conserns**

At the task 4 an unique ID=4 was mentioned. Since there was no ID=4 in response for GetCharactersInFilm request, on which result I should rely, it's clear that this task is ambiguous. I should ask about this earlier.

However, I've made research that personID=4 also corresponds to Darth Vader. 
