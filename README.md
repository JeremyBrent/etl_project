<!DOCTYPE html>
<html>
   <body style = "font-family:'Zilla Slab'">

<div style="background-image: url('Images/pattern-leaves-white.jpg');">
<center><img src="Images/logo-acnh-en.png" class="center"></center><br>
<center><img src="Images/Critterpedia_Trans.png" class="center" width=1000></center><br>
</div>
<h1><center>ETL Project - Brian Remite, Jeremy Brent, Kevin Kleyman, Matt Sadowski<center></h1>


<h2> For this project, we have created a "Critterpedia" of all of the bugs, fish, and villagers within Animal Crossing: New Horizons. Using our tool, you will be able to...</h2>

<ul>
    <li>Collect all of the data for each critter type, including when they are available throughout the year.</li>
    <li>Keep track of which critters you have collected for your museum.</li>
    <li>Which residents you have on your island.</li>
</ul>

<center><img src="Images/shell-2.png"><img src="Images/shell.png"><img src="Images/shell-2.png"></center>

<h1> Before You Begin </h1>

<ol>
<li>Create a new database in PostgresSQL titled "ACNH Critterpedia".</li>

<li>Run the schema.sql in the root to create the schema within PostgresSQL.</li>

<li>Run the Jupyter Notebooks within the Notebooks folder to populate the database with data scraped/acquired from the following sources:
    <ul>
    <li>Fish and Bugs data scraped from the Animal Crossing Wiki: <a href="https://animalcrossing.fandom.com/wiki/Fish_(New_Horizons)"> https://animalcrossing.fandom.com/wiki/Fish_(New_Horizons)</a> and <a href="https://animalcrossing.fandom.com/wiki/Bugs_(New_Horizons)"> https://animalcrossing.fandom.com/wiki/Bugs_(New_Horizons)</a></li>
    <li>Villager data from kaggle: <a href="https://www.kaggle.com/jessemostipak/animal-crossing?select=villagers.csv">https://www.kaggle.com/jessemostipak/animal-crossing?select=villagers.csv</a></li>
    </ul></li>
</ol>

<br>
<center><img src="Images/nook.png"></center>
<center><h2><b>Tom Nook</b><h2></center>

<h1>Data Structure</h1>
<h2>ERD</h2>
<center><img src="Images/ERD.png"></center>
<h2>Tables</h2>
<ul>
    <li><b>encyclopedia</b> - The master list of all "critters" in our database.</li>
        <ul>
            <li><b>id (PK)</b> - Unique identifier for all critters in our database. Composed of IDs from the fish, bugs, and villagers notebooks.</li>
            <li><b>Name</b> - The given name for each critter in the database.</li>
            <li><b>Price</b> - The number of bells (the game's currency) returned when selling the critter at Nook's Cranny. Only applies to fish and bugs.</li>
            <li><b>Location</b> - Where to find the critter on your island. Only applies to fish and bugs.</li>
            <li><b>Shadow_size</b> - The size of the shadow cast in the water when trying to catch a fish.  Only applies to fish.</li>
            <li><b>type</b> - The type of critter in the database.  Valid options are <i>fish</i>, <i>bug</i>, and <i>villager</i>.</li>
            <li><b>numerical_id</b> - The numerical ID of the critter acquired from the .csv file. Only applies to villagers.</li>
            <li><b>Gender</b> - The gender of the critter. Only applies to villagers.</li>
            <li><b>Species</b> - The species of the critter. Only applies to villagers.</li>
        </ul><br>
    <li><b>collection</b> - The table that tracks each user's collection data. Unique entries are based upon the <i>email_address</i> field and the <i>id</i> field.</li>
        <ul>
            <li><b>email_address (PK)</b> - Email address for user entering their collection information.</li>
            <li><b>id (PK)</b> - Unique identifier for all "critters" in our database. Foreign key of the <b>encyclopedia</b> table.</li>
            <li><b>type</b> - The type of critter in the database.  Valid options are <i>fish</i>, <i>bug</i>, and <i>villager</i></li>
            <li><b>caught</b> - Boolean to designate if a critter has been caught by the user.</li>
            <li><b>donated</b> - Boolean to designate if a critter has been donated to Blathers' Museum by the user.</li>
            <li><b>resident</b> - Boolean to designate if a critter has been recruited to live on the island by the user.</li>
        </ul><br>
    <li><b>months</b> - The lookup table to indicate the months that critters are available for catching in the game. Only applies to fish and bugs.</li>
        <ul>
            <li><b>id (PK)</b> - Unique identifier for all "critters" in our database. Primary Key. Foreign key of the <b>encyclopedia</b> table.</li>
            <li><b>Jan</b> - Boolean to designate if the critter appears in January. Only applies to fish and bugs.</li>
            <li><b>Feb</b> - Boolean to designate if the critter appears in February. Only applies to fish and bugs.</li>
            <li><b>Mar</b> - Boolean to designate if the critter appears in March. Only applies to fish and bugs.</li>
            <li><b>Apr</b> - Boolean to designate if the critter appears in Apri. Only applies to fish and bugs.</li>
            <li><b>May</b> - Boolean to designate if the critter appears in May. Only applies to fish and bugs.</li>
            <li><b>Jun</b> - Boolean to designate if the critter appears in June. Only applies to fish and bugs.</li>
            <li><b>Jul</b> - Boolean to designate if the critter appears in July. Only applies to fish and bugs.</li>
            <li><b>Aug</b> - Boolean to designate if the critter appears in August. Only applies to fish and bugs.</li>
            <li><b>Sep</b> - Boolean to designate if the critter appears in September. Only applies to fish and bugs.</li>
            <li><b>Oct</b> - Boolean to designate if the critter appears in October. Only applies to fish and bugs.</li>
            <li><b>Nov</b> - Boolean to designate if the critter appears in November. Only applies to fish and bugs.</li>
            <li><b>Dec</b> - Boolean to designate if the critter appears in December. Only applies to fish and bugs.</li>
        </ul><br>
    <li><b>times</b> - The lookup table to indicate the time frames that critters are available for catching in the game. Only applies to fish and bugs.</li>
        <ul>
            <li><b>id (PK)</b> - Unique identifier for all "critters" in our database. Primary Key. Foreign key of the <b>encyclopedia</b> table.</li>
            <li><b>time</b> - Indicator of which times the critter is available to catch. Only applies to fish and bugs.</li>
        </ul>
</ul>
<br>
<center><img src="Images/share-image-1.png"></center>

</body>
</html>