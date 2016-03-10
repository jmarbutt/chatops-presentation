
##[fit] Chat**Ops**
##[fit]Look Who's **Talking**

---

#We all know our **friend**

---

![fit](images/hellohubot.png)

---
# Doesn't Hubot only know **pugs**?
`@Hubot pug me`

![inline](images/pugme.jpg)

---
#[fit] What if Hubot could do **more**?

---
#[fit] What if Hubot was part of the 
##[fit] **team**? 

---
#Where did he come from?
- Created by **GitHub**
- github.com/github/hubot

## Sample Scripts
- github.com/github/hubot-scripts

---
## How does **GitHub** use  
# Hubot?
---
## Deployments
**jonathan** @Hubot deploy github/myfeature to production
**Hubot** @jonathan deployed myfeature

---
## Recent Deployments
**jonathan** @Hubot deployed
**Hubot** @jonathan deployed myfeature today at 3:30 PM

**Hubot** @nick deployed hotfix yesterday at 4:43 PM

**Hubot** @sha deployed awesome yesterday at 12:23 PM

---
## Deployments
**jonathan** @Hubot deploy github/myfeature to production

**Hubot** @jonathan deployed myfeature

---
## Status
**jonathan** @Hubot I'm working on the best presentation ever

**Hubot** got it!

**nick** @Hubot what is jonathan working on? 

**Hubot** Jonathan is working on the best presentation ever

---
## How busy is shake shack?
**rick** @Hubot shake cam

![inline](images/shakecam.jpg)

---
## I know what you are **thinking**...

--- 

##[fit]What about 
#[fit]**Chipotle?**
#### Maybe not everyone... just Rick

---
## Anatomy of a **Script**

--- 
### It's just **Node**

---
### Most are written in **coffee script**

---

```coffee
module.exports = (robot) ->
  robot.respond /shake cam/i, (msg) ->
    msg.send 'http://www.shakeshack.com/camera.jpg'
```

---

## Are you **listening**?
#### because Hubot is...

---
## Hearing & Responding
```coffee
robot.hear /badger/i
```
**jonathan** I don't want to badger anyone

```coffee
robot.respond /open the pod bay doors/i
```
**nick** @Hubot open the pod bay dooors

---
##**Talking** Back

---
## Sending
```coffee
module.exports = (robot) ->
  robot.hear /badger/i, (res) ->
    res.send "Badgers? BADGERS? WE DON'T NEED NO STINKIN BADGERS"
```
**jonathan** I don't want to badger anyone
**Hubot** Badgers? BADGERS? WE DON'T NEED NO STINKIN BADGERS"

--- 
## Replying
```coffee
module.exports = (robot) ->
  robot.respond /open the pod bay doors/i, (res) ->
    res.reply "I'm afraid I can't let you do that."
```
**nick** @Hubot open the pod bay dooors
**Hubot** @nick I'm afraid I can't let you do that.

--- 
## Capture **data**
- What if I want to open a different door?

```coffee
  robot.respond /open the (.*) doors/i, (res) ->
    doorType = res.match[1]
    if doorType is "pod bay"
      res.reply "I'm afraid I can't let you do that."
    else
      res.reply "Opening #{doorType} doors"
```

---
## Making JSON calls
```coffee
 robot.http("https://midnight-train")
    .header('Accept', 'application/json')
    .get() (err, res, body) ->
      # error checking code here

      data = JSON.parse body
      res.send "#{data.passenger} taking midnight train going #{data.destination}"
```
---
## If I only had a **brain**...

---
## Hubot's **brain**
- Provides in-memory key-value storage `robot.brain`

```coffee
robot.respond /have a soda/i, (res) ->  
  sodasHad = robot.brain.get('totalSodas') * 1 or 0
  if sodasHad > 4
    res.reply "I'm too fizzy.."
  else
    res.reply 'Sure!'
    robot.brain.set 'totalSodas', sodasHad+1
robot.respond /sleep it off/i, (res) ->
  robot.brain.set 'totalSodas', 0
  msg.reply 'zzzzz'
```

---
## Some other cool **features**

- Restricted Access to Commands
- XML Parsing
- Screen Scraping (cheerio and jsdom)
- Whatch if topic changes
- Know when someone enters or leaves a room

---

##How could **we** user Hubot?