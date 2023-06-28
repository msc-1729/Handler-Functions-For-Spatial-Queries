# Handler Functions for Spatial Queries
This project is all about creating user-defined functions on which spatial queries can be built in order to perform Hot Zone Analysis to efficiently find the taxi cab pickup points and Hot Spot Analysis to find the hotspots that are statistically significant using the Getis ord statistic.
As a part of the project phase 1 user-defined functions are defined and spatial queries are developed. 
### Problem Description:
In this phase, two user-defined functions were implemented, ST_Contains and ST_Within for SparkSQL through Scala. We ran four spatial queries which are Range query, Range join query, Distance query, and Distance join query to analyze the given data using the two SparkSQL functions.
### Range Query:
This query is used to locate all those points P, that are present within a specific rectangular geographical border R, in a city or town, and for a set of points P (which is a set of locations of clients who have requested a taxi using our service). To acquire the required points, we used the user-defined function ST_Contains.
### Range Join Query:
This query is used to find all the point and rectangle pairs (P, R) such that the point is within the rectangular boundary for a given set of rectangular geographical boundaries R, in a city or town, and for a set of points P (which is a set of locations of customers who have requested a taxi using our application).
To acquire the required points, we used the user-defined function ST_Contains.
### Distance Query:
We need to discover a position, P', such that the distance between these two places is less than D, i.e., |P-P'|=D, with a given fixed point location P and a distance value D (in kilometers). This query returns a list of all such points. We utilized the user-defined function ST_Within to acquire the required points for this query.
### Distance Join Query:
This query is used to identify all the pairs of points (p1, p2) where p1 belongs to the set P1 and p2 belongs to the set P2, and the distance between p1 and p2 is smaller or equal to D for a given set of points P1 and P2. We utilized the user-defined function ST_Within to acquire the required pair of points for this query.
Implementation:
There have been two functions defined that are ST_Contains and ST_Within:
### ST_Contains:
A Point and a Rectangle are the two arguments for this function. The coordinates of the point are indicated by Point, and the coordinates of the diagonal ends are indicated by Rectangle. These coordinates were supplied as a string. This function determines whether the point is within the rectangle.
Parameters - pointString, queryRectangle
Return - True/False
<img src="/Phase1/Flowchart1.png" alt = "Flowchart of ST_Contains "/>

### ST_Within:
There are three parameters in this function: two points and a distance. Distance D is a numerical value
that represents the point's coordinates. These coordinates were supplied as a string. This function will
determine whether these two places are within D distance of one another.
Parameters - PointString1, PointString2, distance
Return - True/False
<img src="/Phase1/Flowchart2.png" alt = "Flowchart of ST_Within"/>

### Testing:

* Go to the main directory in the cmd prompt and run the command sbt assembly.
* This will result in the creation of a jar file in the target folder.
* Copy this jar file into the main folder.
* Run the command spark submit spark-submit .jarfile\result\output rangequery src\resources\arealm10000.csv -93.63173,33.0183,-93.359203,33.219456 rangejoinquery src\resources\arealm10000.csv src\resources\zcta10000.csv distancequery src\resources\arealm10000.csv -88.331492,32.324142 1 distancejoinquery   src\resources\arealm10000 csv src\resources\arealm10000.csv 0.1.
* Executing this command will create a result folder with four output* subfolders.
* These folders contain the csv files with one having the query name and the other having the result value.
