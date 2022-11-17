# WeChat-Daily-Message

<br />

<img src="https://user-images.githubusercontent.com/102897343/201457682-2a0e9133-e4e0-4bce-b711-597de11b066f.jpg" width="200"/>

<br />

## About
- Send daily Wechat message to users subscribed to the public sandbox account(WeChat), the message is send at a pre-defined time.
- Use this to send daily greetings to love ones, special message on important dates or daily informations like weather and temperatures.

<br />

## Features
- Current date.
- Daily chinese ancient poetry.
- Daily chinese/English motivational line.
- The number of days before a birthday.


<br />

## Tools and Configuration 
- Using the [Github Actions](https://docs.github.com/en/actions) features to Automates the build through defineing the workflow inside `weixin.yml`.
- Python as the main programming language.
- Uses the [Requests library](https://realpython.com/python-requests/) to fetch requests to api.

<br /> 

## Set up Workflow in Github Action

**1) Click on the action tap when you are currently inside the repository.** <br />
<img width="533" alt="Screen Shot 2022-11-13 at 4 59 30 PM" src="https://user-images.githubusercontent.com/102897343/201505324-f7dee3a8-1dde-44f6-af69-17cab61fc1c4.png">

<br />

**2) Click on the "Set up a workflow yourself" link.** <br />
<img width="535" alt="Screen Shot 2022-11-13 at 5 13 49 PM" src="https://user-images.githubusercontent.com/102897343/201505364-41e581bd-33a4-42d2-bf62-5a5a62db1454.png">

<br />

**3) Copy and post the following code inside the newly created folder.** <br />

```C

name: weixin
on:
  workflow_dispatch:
  schedule: 
    # This represent global time 21:30
    - cron: '30 21 * * *'
jobs:
# Combine all the works/jobs in the workflow
  build:
    runs-on: ubuntu-latest 
    steps:
      - uses: actions/checkout@v2
    
      - name: Set up Python 3.9
        uses: actions/setup-python@v2
        with:
          python-version: 3.9.1
      - name: Set timezone
        run: |
          cp /usr/share/zoneinfo/Asia/Shanghai /etc/localtime
      - name: install pip packages
        run: |
          python -m pip install --upgrade pip
          pip3 install -r requirements.txt
      - name: weixin
        run: |
          python3 main.py
          
 ```
 <br />
 
**4) Press `Start commit` then `Commit new file` at the top right of the scrren.**  <br />

<img width="446" alt="Screen Shot 2022-11-13 at 5 45 51 PM" src="https://user-images.githubusercontent.com/102897343/201506443-c218bcd2-06b1-4793-a3a3-6298d1b22fc8.png">

<br />

## How to use 
**1) Clone the respiratory onto your Github**
<br />
**2) Setup WorkFlow**
<br />
**3) Edit `config.txt` according to the instructions in the file**
<br />
Fill in the personal details display in [WeChat Testing Platform](https://mp.weixin.qq.com/debug/cgi-bin/sandbox?t=sandbox/login) to `config.txt`
<br />
![Capture](https://user-images.githubusercontent.com/102897343/202341286-1ce67bc2-b820-4d69-8cb6-fbd88219cf18.PNG)
<br /> 

### Scan the QR code to subscribe to the message.
![Capture](https://user-images.githubusercontent.com/102897343/202349042-5c4a9bf4-2b89-4271-aee2-11a101f2d203.PNG)
<br />

### Module ID.
![Capture](https://user-images.githubusercontent.com/102897343/202348654-35865156-cf08-4e08-b567-d3adbe3e968f.PNG)
<br />

## Edit Message
- Click on "Add new Testing module"
- Edit the input box of `Module Title` to change the headings/title of the message.
- Edit the input box of `Module Content` to change the content of the message.
- Use `{{xxx.DATA}}` to display information, where `xxx` is the variable in `config.txt`.





**4) Goes into the "Action" tab and run the workflow**
<br />


