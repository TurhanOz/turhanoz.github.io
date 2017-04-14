I am a mobile developer. Developping software is an art through which you express your creativity.
But before creating anything, an unecessary amount of time is often wasted to setup, to administrate and to manage environment (development, integration, production & so…). 

# Let me describe you the big picture:
Once uppon a time, when a was young and uncarefull about neither time passing nor producing value, I would have done a thousand things before even coding a single line of code to fulfill my idea.

1. I would have started by installing a Linux distribution (ubuntu to name one) onto an old dusty desktop machine laying into a locker.
2. I would then have installed all necessary software to develop into the targeted plateform (android, maven & so.)
3. I would then have installed a Source Version Control software, such as GIT, to access and store my ‘precious’ code. This would also have implied configuring ssh server and managing allowed/denied account to commit.
4. Then, I would (or wouldn’t) have installed and configured a continous integration system, such as jenkins.

5.To access my code from everywhere, I would have of course setup all the required network routing (configuring iptables, configuring some virtual hosts to route subdomain names, one for svc, the other for jenkins). To do so, I would necessarely have configured some domain name pointing to my self hosted desktop computer.

6.Exposing my desktop server to the world, I would have configured some banning policy to block brut force attacks (fail2ban is your friend)
7.And more !

This is all fun and full of learning, but let’s remind my primary goal: Expressing my creativity through coding.

* Have I done something close to that goal ? Not at all.
* Am I a sysadmin ? Certainly not.
* Am I looking as a sysadmin so far ? Kind of…
* Am I wasting my time doing so ? Regarding my primary goal, definitely.

Most of the time, your enthutiasm stops there in a subtile manner. Indeed, you are so proud and exshauted of having setup all the environment that you convince yourself that, from now one, you can start developping anytime (converting your idea into something concrete). So you take some rest and know that you could start coding in a few days, anytime. Your primary idea slowly evaporates. You have done nothing, except wasting your time.

You don’t want your idea flying away, do you ?

**Experiment brings you wisdom.**


# #1 Code is not the value, Execution is
You slowly understand that your code is not the value as you naively think, but you realize that the value is in fact in the Execution of your idea.
Trying to secure your code into your own CVS system hosted into your own server is so unecessary at this stage.

I would recommand you to host your code into hubs (github, gitlab, bitbucket), costing you few dollars per month and bringing you the required level of security.
I would personaly use github for my open source projects an gitlab for my non foss projects.

_Cost : 0$ (gitlab) to few dollars_

# #2 Continious Integration into the Cloud
Continous integration is, for me, a « can’t go without it » thing (regarding the project). Instead of going through the installation described above, I would definitely recommand you to go with online PaaS, such as Cloudbees. It fills all my requirements (Android support, Maven).

Cost : 0$ (free plan)

# #3 Organize your development
You can not develop all your features at once, nor starting one before finishing the other. It is better to complete small batch of features sequentially, in an agile manner (definition of ready, definition of done). This helps you avoid dispersing and will benefit you. Then, again, there are online tools that will definitely help you being 
effective (kanbanflow.com for free, http://kanbanize.com for free, Jira Agile 20$/month). I would choose Atlassian for my needs.

As you can see, you can easily start developping, in a peace of mind manner and effective way, for 0$ per month (or few dollars). Your only concern is creating value serenely.
  
Don’t forget : 

**The value is not the code, the value is the execution.*
