<p align="center">
<img src="Img/duo.svg" width="128px"/>            
</p>
<h1 align="center">DuoXPy - Project Sandy</h1>
<h4 align="center">⚡️ XP farm and Streak keeper for Duolingo 🔥</h4>
<h4 align="center">Powered by GitHub Actions 🐙 and Python 🐍</h4>
<p align="center">
<img alt="GitHub issues" src="https://img.shields.io/github/issues/gorouflex/DuoXPy?style=flat">
<img src="https://img.shields.io/github/forks/gorouflex/DuoXPy?style=flat">
<p align="center">
<img src="https://img.shields.io/github/stars/gorouflex/DuoXPy?style=flat">
<img alt="GitHub watchers" src="https://img.shields.io/github/watchers/gorouflex/DuoXPy?style=flat">
<img src="https://img.shields.io/github/contributors/gorouflex/DuoXPy?style=flat">
</p>
<p align="center">
<a href="https://github.com/gorouflex/DuoXPy/actions/workflows/codeql.yml"><img src="https://github.com/gorouflex/DuoXPy/actions/workflows/codeql.yml/badge.svg"></a>
<a href="https://github.com/gorouflex/DuoXPy/actions/workflows/cl.yml"><img src="https://github.com/gorouflex/DuoXPy/actions/workflows/cl.yml/badge.svg"></a>
</p>
<p align="center">
<a href="https://github.com/gorouflex/DuoXPy/actions/workflows/daily.yml"><img src="https://github.com/gorouflex/DuoXPy/actions/workflows/daily.yml/badge.svg"></a>
<a href="https://github.com/gorouflex/DuoXPy/actions/workflows/manual.yml"><img src="https://github.com/gorouflex/DuoXPy/actions/workflows/manual.yml/badge.svg"></a> (*)
</p>
<p align="center">
  <a href="https://github.com/gorouflex/DuoXPy/">English 🇺🇸</a>
  •
  <a href="Docs/README-vn.md">Tiếng Việt 🇻🇳</a>
<p align="center">
  <a href="#feature">Feature</a>
  •
  <a href="#usage">Usage</a>     
  •
  <a href="#config">Config</a>     
  •
  <a href="#preview">Preview</a>
  •
  <a href="#disclaimer">Disclaimer</a>
</p>

### Belong to the Sandy Project

- [HoneygainPot](https://github.com/gorouflex/HoneygainPot/) ( 🐝 Automatically claim your Honeygain lucky pot every day 🍯 )
- [DuoXPy](https://github.com/gorouflex/DuoXPy/) ( ⚡️ XP farm and Streak keeper for Duolingo 🔥 )
  
> [!IMPORTANT]
> **Read all** documents in this repo before doing anything!
> 
> Don't forget to star ⭐ this repository
> - Always update your repo following the original repo to get the latest update + bug fixes; I will not support anything if your repo is outdated
> - **Do not** enter your information ( token ) into 2 workflows file ( `daily.yml` and `manual.yml` ) because it will not work and may leak your information to everyone
> - (*): Do not fork this repo if one of these or all of these ( not CodeQL and CL ) GitHub Actions status badge show failing, and wait until one of these or two of these show passing then you can fork again
> - `Daily lessons` workflows always run every 14:00 UTC + 0; if you want to change it, refer to [this](https://github.com/gorouflex/DuoXPy/blob/main/README.md#how-to-change-the-schedule-that-the-workflows-will-run)
> <img src="https://i.imgur.com/htGeFlY.jpg">
  
# Feature 

- XP farm ⚡️
- Streak keeper 🔥

# Usage 

  1. Go to [Duolingo](https://www.duolingo.com) and log in to your Duolingo account
  2. Open the browser's console by pressing `F12` button ( or `Fn+F12` on some laptops )
  3. Click on the tab `Console` than paste this to the console
```
document.cookie
  .split(';')
  .find(cookie => cookie.includes('jwt_token'))
  .split('=')[1]
```
  4. Copy the token without `'` ( example: 'abcde1234` -> abcde1234 )
  5. [Fork this repository 🍴](https://github.com/gorouflex/DuoXPy/fork)
  6. Go to your forked repository 🍴
  7. Go to `Settings > Secrets and Variables > Actions`, and click `New Repository secret`
  8. Use `JWT_TOKEN` and paste your JWT Token from Steps 3
  9. Go to your forked repository 🍴 and go to the Actions tab and press `I understand my workflows, go ahead and enable them`

> [!IMPORTANT]
> If you want to farm XP, go to the [`Manual lessons trigger`](https://github.com/gorouflex/DuoXPy/actions/workflows/manual.yml) workflows ( located in the Actions tab of the repo ). Then, enter the lesson you need to farm ( 1 lesson = 20xp ). Usually, if you enter a lot of lessons ( like >1000 ) or if Duolingo cannot handle the request, you will receive an error code or log, and the lesson will be skipped. So, think wisely before entering the lesson!
> 
> If you got `No skillId found in xpGains` log then try to do least 1 lesson so it can run back to normal!

<p align="left">
  <img src="Img/get_token.png">
  <img src="Img/GitSettings.png">
</p>

## How to change the schedule that the workflows will run?

> [!IMPORTANT]
Daily workflow file path ( default is 14:00 UTC ± 0, and **DO NOT** enter your token here cause it will **not work** and may leak your information to everyone ): `.github/workflows/daily.yml`

- Well, GitHub uses UTC time ( UTC ± 0 ) for scheduling workflows, so we should convert it to our timezone

- For example: If I want to set the daily trigger to trigger at 9:00 PM ( UTC + 7 ) , I have to set it to 2:00 PM or 14:00 ( 24-hour format ) ( UTC ± 0 ) ( 2+7=9 ):

```
name: Daily claim
on:
  schedule:
    - cron: '0 14 * * *' # <- Use UTC Time +0 , change your time here ( 14 is hour , 0 is minutes ) and use 24-hour format
```
- So, if I want the daily trigger to run at 5:00 AM ( UTC + 7 ), I have to set it to 10:00 PM ( UTC ± 0 ) ( use 24-hour format ):

```
name: Daily claim
on:
  schedule:
    - cron: '0 22 * * *' # <- Use UTC Time +0 , change your time here ( 14 is hour , 0 is minutes ) and use 24-hour format
```

> [!NOTE]
> GitHub Actions schedules can sometimes be delayed by up to 15 minutes due to high demand, so don’t worry! ⏱️

# Config

- Usually, you can find your config folder in the same place as the `main.py` file. In some specific cases, you might need to locate your config through the information window in the `main.py` file
- You can change your information and lessons in the config file

# Preview

<p align="left">
  <img src="Img/preview.png">
</p>

# Disclaimer

> [!WARNING]
>
> - This script is **not** affiliated with Duolingo
> - Use it at your **own risk** and responsibility  
> - I'm **not responsible** for any consequences that may arise from using this script
> - This script won't help with your daily or friend quests, it can only earn XP to move up the league rank
> - This script won't do real lessons or stories, only practices, so it won't affect your learning path
> - You may get **banned** from Duolingo if you overuse it, so use it wisely

### Special thanks to 💖
- [rfoal](https://github.com/rfoel/) x [duolingo](https://github.com/rfoel/duolingo) for the source code and idea
