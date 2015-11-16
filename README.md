# BigBroLittleBro
Two brothers talking about stuff and things.

## Goals
* Create a hybrid Chat/Blog platform that encourages conversational blogging between two or more people.
* Build out messaging interface using react components.
* Explore Slack API as a method of storing messages.
* Explore Flux as an application architexture.
* If Slack API doesn't work out (or even if it does), get hands dirty with MongoDB and WebSockets just for funsies.
* Allow user registration using OAuth 2.0.
* Set up user commenting so that it makes sense in a conversational format.
* Explore post-processing CSS.
* Learn how to build an application *well* using ES6.
* And last but not least, get advice from big bro...

## Requirements
* Node.js
* MongoDB
* Gulp

## Build Guide
1. `git clone https://github.com/Reklino/BigBroLittleBro.git`
2. `cd BigBroLittleBro`
3. `npm i`
4. `gulp`

## The Blueprint
Below are some basic possible table structures for reference. These will, of course, depend on whether or not we use the Slack API...

*blurbs*

id | slack_blurb_id | topic_id | user_id | created_at | updated_at
-------- | -------- | -------- | -------- | -------- | --------
32-bit integer | 32-bit integer | 32-bit integer | 32-bit integer | Timestamp | Timestamp

Relationships:
* Has many comments
* Belongs to one topic
* Belongs to one user

--------

*topics*

id | slack_topic_id | user_id | created_at | updated_at
-------- | -------- | -------- | -------- | --------
32-bit integer | 32-bit integer | 32-bit integer | Timestamp | Timestamp

Relationships
* Has many blurbs
* Belongs to one user

--------

*comments*

`may need to be polymorphic if we include blog posts as well as topics`

id | user_id | blurb_id | created_at | updated_at
-------- | -------- | -------- | -------- | --------
32-bit integer | 32-bit integer | 32-bit integer | Timestamp | Timestamp

Relationships:
* Belongs to one user
* Belongs to one blurb
* Belongs to one topic (unnecessary, but would be nice to have)

--------

*users*

`need to work on this one after looking more at Oauth 2.0 of course...`

id | name | created_at | updated_at
-------- | -------- | -------- | --------
32-bit integer | String | Timestamp | Timestamp

Relationships:
* Has many topics
* Has many blurbs
* Has many comments