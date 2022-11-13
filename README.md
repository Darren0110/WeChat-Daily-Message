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
          cp /usr/share/zoneinfo/Oceania/Auckland /etc/localtime
      - name: install pip packages
        run: |
          python -m pip install --upgrade pip
          pip3 install -r requirements.txt
      - name: weixin
        run: |
          python3 main.py
          
 ```
 <br />
**4) Press `Start commit` then `Commit new file`.** <br />

<img width="459" alt="Screen Shot 2022-11-13 at 5 45 51 PM" src="https://user-images.githubusercontent.com/102897343/201506211-87b0d475-8dc2-45eb-8855-a3d543e7aaef.png">

