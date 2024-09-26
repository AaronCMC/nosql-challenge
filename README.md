# nosql-challenge  
## Purpose  
* To evaluate some of the ratings data provided by the UK Food Standards Agency in order to help food magazine journalists & food critics decide where to focus future articles.  

## Database & Jupyter Notebook Set Up (NoSQL_setup_starter.ipynb)  
* Imported a JSON file (establishments.json) from the UK Food Standards Agency via Terminal, into the uk_food database and establishments collection.  
* Imported PyMongo (to interface with MongoDB) and Pretty Print.  
* Created an instance of the Mongo Client.  
* Confirmed the creation of the database and collection, and data was loaded properly by:  
    * Listing databases in MongoDB - > uk_food was listed  
    * Listing collections in uk_food database - > establishments was listed  
    * Found and displayed, via pprint, one document in the establishments collection.  
* Assigned establishments collection to a variable to prepare for use.  

## Updating the Database (NoSQL_setup_starter.ipynb)  
Magazine editors requested modifications to the database before performing any queries or analysis. The following changes were made to the establishment collection:  
* A new document for an exciting new halal restaurant (BusinessName: Penang Flavours) just opened in Greenwich (but hasn't been rated yet) was added to the database.  
* Updated the new restaurant (BusinessName: Penang Flavours) with the correct BusinessTypeID (i.e. 1) for the 'Restaurant/Cafe/Canteen' BusinessType.  
* Checked how many docuemnts contained the Dover Local Authority. Then, removed any establishments within the Dover Local Authority from the database, and checked the number of documents again to ensure they were deleted.  
* Converted all geocode.latitude & geocode.longitude values to doubles.  
* Converted all RatingValue values to integers.  

## Exploratory Anlaysis (NoSQL_analysis_starter.ipynb)
### Note:  
* RatingValue referes to the overall rating decided by the Food Authority and ranges from 1-5. The higher the value, the better the rating.  
    * This field also includes non-numeric values such as 'Pass'. These were coerced to nulls during database setup before converting ratings to integers.  
* The scores for Hygiene, Structural, and ConfidenceInManagement work in reverse. The higher the value, the worse the establishment is in these areas.  

### Questions:
* Which establishments have a hygiene score equal to 20?  
    * Number of establishments with a hygiene score of 20: 41  
* Which establishments in London have a RatingValue greater than or equal to 4?  
    * Number of establishments with London as Local Authority and has RatingValue gte 4: 33  
* What are the top 5 establishments with a RatingValue of 5, sorted by lowest hygiene score, nearest to the new restaurant added (Penang Flavours)?  
    * 'Howe and Co Fish and Chips - Van 17', 'Atlantic Fish Bar', 'Plumstead Manor Nursery', 'Iceland', 'Volunteer'
* How many establishments in each Local Authority have a hygiene score of 0? Sort results from highest to lowest, and print out top 10 local authority areas.
    * There are 55 documents of data resulting from the aggregation via count.
    * The top 10 local authority areas with the highest number of establishments with a null hygiene score include the following: Thanet (1130), Greenwich (882), Maidstone (713), Newham (711), Swale (686), Chelmsford (680), Medway (672), Bexley (607), Southend-On-Sea (586), Tendring (542).
