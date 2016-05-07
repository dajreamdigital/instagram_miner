# Instagram Miner
Instagram Miner allows a user to search and view all Instagram posts made with a specific hashtag within a specific time period. 

Table of Contents
----------
- How I Made It
- Technologies Used
- Installation
- Server Setup
- Database Setup
- Basic Usage
- Known Issues
- Choices I Made
- Version 2.0
- About the Author

How I Made It
------------
- Description needed

Technologies used
----------
- Python
- Django
- Postgres
- Psycopg2
- HTML/CSS
- Bootstrap
- Instagram API

Installation
-----------
- Fork the repo
- Make a new directory and pull to this directory
- source a virtual environment
- install from requirements.txt
- create secrets.sh
- create .gitignore
- add *.pyc, env/, .DS_STORE, secrets.sh to .gitignore

Server Setup
-----------
- obtain ACCESS_TOKEN from PixelUnion
- obtain SECRET_KEY using online generator
- (while still in environment) add ACCESS_TOKEN & SECRET_KEY to secrets.sh
- source secrets.sh in console tab you'll be using for server
- python manage.py runserver

Database Setup
-----------
- [[ need to check DjangoGirls slides for Postgres start-up]]

Basic Usage
-----------
- Rate limits
- Time frames within which to search
- Creating a new campaign
- Viewing all your campaigns
- Viewing the details of one campaign

Known Issues
------------
- Throws errors if New Campaign form submission doesn't contain all fields

Choices I Made
-----------
- In order to reduce the risk of hitting the rate limit for the endpoint (5,000/hour), I sent a {'count': 100} parameter in the header of the GET request to the Instagram API. I tested this by pulling result photos for a hashtag with 1,550 posts. I expected to have 16 API hits but instead had 22, for an average of 70.5 results per page of the endpoint. 
- The API call returns data for the time the photo was posted to Instagram as epoch time. The New Campaign form allows the user to enter start/end dates as strings, which are converted to epoch time. All date info is stored in the Postgres database as epoch time in order to more easily compare whether or not a photo was posted within the specified time range.
- I chose to focus my time on creating a web app with the requested primary functionality of making an API call and collecting photos from it. I opted not to include login/logout functionality for v1.0, but will include it in v2.0
- I listed the photo owner's Instagram username under each photo as a link. Someone who is considering using this person's photo for marketing purposes can first check out the user's other posts, to make sure they are not insensitive or inflammatory. 
- I added a place-holder button under each photo that will eventually allow a user to request permission directly from the photo's owner to use the photo for marketing purposes. 
- I used Django because I wanted to learn a new Python web framework. The documentation is AWESOME!

Version 2.0
-----------
- Allow a user to delete a campaign they've created, and subsequently delte its associated photos from the database
- Explore parallel processing of many new campaign requests happening simultaneously
- Include error handling for an expired Instagram API access token
- Instagram requires that a developer "Only store or cache User content for the period necessary to provide your app's service." Campaigns could be deleted after 3-6 months of inactivity, with an email sent to the User before deletion. 
- Add login/logout functionality so users' campaigns are visible only to them
- Allow a user to request permission from the photo's owner to re-use the photo for marketing purposes
- Add tests
- Allow a user to alter the campaign's date range if their initial inquiry yielded too many / not enough result photos
- Allow a user to delete result photos from their campaign if they don't want to use that photo for marketing

About the author
-----------
[Erin Allard on LinkedIn](http://www.linkedin.com/in/erinallard1 "Erin Allard's LinkedIn profile")

I'm a 2016 graduate of [Hackbright Academy](http://www.hackbrightacademy.com) in San Francisco, the leading full-stack engineering school for women. My background is in economics, commercial real estate and wealth-building education. I love [quilting](http://www.instagram.com/millennialquilter) and botanical art. 
