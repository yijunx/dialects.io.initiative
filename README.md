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
 
# backend openapi (to allow other apps to use backend services, and sell apiKey..)
  * search words dialects
  * get examples / usages etc.
  * get random words to display
  * get statistics

# user management
  * user has levels / achievements / badges
  * admin user can merge words / delete word / lock word

# architecture
  * micro service
    * user management (python-flask)
    * word management (python-flask)
    * vote management (python-flask)
    * ui (react)
    * email service (python-celery)
    * notification (not sure how to do yet)
  * nginx api gateway, tls termination
  * enabled logging / tracing / monitoring 
  * cloud db
  * cloud rmq for pass events to worker

# cost
  * docker pro (for storing private images) -> $5 / month
  * digitalOcean k8s  -> not sure, says $10 / month
  * digitalOcean postgres  -> got free tier, possibly $10 / month
  * need something to run jenkins -> well can run locally..

# RBAC design
  * user management
    * there is role USER_ADMIN with fixed role id.
    * USER_ADMIN has right to
      * ban user
      * list users (within user management)
      * perform user management action to other services (like get/update/remove/patch roles from each service)
  * work management 
