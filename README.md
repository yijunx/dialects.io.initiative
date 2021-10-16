# dialects.io.initiative
just some ideas

# for what
to make sure dialects (human language) are properly stored / maintained / updated / managed / used

# How
create a webservice allow users to

  * browse/search the words
  * words are with chinese char (if possible), pronouciation, explanation, usage, and possibly origin of it
  * create new words
  * create new versions of existing words, delete my own version, view all versions
  * vote for the best version (each user one vote for each word), best version will be displayed on default
  * watch a word (gets updated if there are new version or any changes)
  
# web frontend
  * login with google/wechat/github/facebook or whatever, no user registration
 
# backend api
  * search dialects
  * get examples

# user management
  * user has levels / achievements / badges
  * admin user can merge words / delete word / lock word

# archetecture
  * micro service
    * user management (python-flask)
    * word management (python-flask)
    * vote management (python-flask)
    * ui (react)
    * email service (python-celery)
    * notification
  * nginx api gateway, tls termination
  * cloud db
  * cloud rmq for pass events around if needed
