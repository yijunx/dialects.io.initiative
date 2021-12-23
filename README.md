# dialects.io.initiative
just some ideas

# for what
to make sure dialects (human language) are properly stored / maintained / updated / managed / used

# Features 

【前】： 前端已经开发
【后】： 后段已经开发

  * 【前后】用户创建词条，用户即为词条的创建者。创建词条时，标题，解释，标签和方言种类是必须的
  * 【后】只有创建者和词条管理员可以修改词条的标题，和标签
  * 【后】其他用户可以对一个词条的解释，发音，用法提出新的版本，只有版本的创建者和版本管理员可以修改版本的内容
  * 【后】所有的版本都可以被投票，票数最多的就会默认成为词条显示的版本
  * 【后】其他用户也可以对一个解释，发音和用法提出建议，版本的创建者可以选择采纳建议。只有建议创建者和建议管理员可以修改建议
  * 【后】词条管理员可以将两个属于同一方言的词条合并，所有跟住的版本和建议都会合并
  * 【后】词条，版本和建议管理员可以deactivate一个词，版本和建议，于是就不会出现
  * 【后】用户在用户profile页面可以看到自己的所有贡献
  * 【后】词条specific页面可以看到所有的贡献者
  * 【后】用户管理员可以ban用户，使他无法登陆


# Some NICE ideas solvable by writing code

[ implemented / pending / WIP / discarded ]

- [WIP] let word page be the front page
- more inviting wording to make it 活泼一点
- did you know part (trivia stuff) on the app home page
- word of the day part (like wiki) on the app home page
- [WIP] first is still to build up all the features

# Some conceptual ideas

[ implemented / pending / WIP / discarded ]

- 为什么要做，想要做什么
- 如果是以建词库为目的，让大家觉得好玩，共此案起来有价值是比较大的动力
- how to get users

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
