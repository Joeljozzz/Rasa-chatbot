
# Rasa Chatbot Deployment on Telegram

This repository contains the steps and configurations required to create and deploy a Rasa chatbot on Telegram.

## Table of Contents
- [Prerequisites](#prerequisites)
- [Project Setup](#project-setup)
- [Model Training](#model-training)
- [Bot Deployment](#bot-deployment)
- [Customization](#customization)
- [Usage](#usage)
- [Acknowledgments](#acknowledgments)

## Prerequisites
Before you begin, ensure you have the following installed on your machine:
- [Conda](https://docs.conda.io/projects/conda/en/latest/user-guide/install/index.html)
- [Python](https://www.python.org/downloads/) (version compatible with Rasa 2.6.2)
- [ngrok](https://ngrok.com/)

## Project Setup
1. **Create a virtual environment:**

    Open your terminal and run the following commands:
    ```bash
    # Create a directory for your project
    mkdir <directory_name>
    cd <directory_name>

    # Create a virtual environment using conda
    conda create -n yourenvname python=x.x anaconda

    # Activate the virtual environment
    conda activate yourenvname
    ```

2. **Install Rasa:**
    ```bash
    pip install rasa==2.6.2
    ```

## Model Training
1. **Initialize Rasa:**
    ```bash
    rasa init
    ```

2. **Run the Rasa model:**
    ```bash
    rasa run
    ```

## Bot Deployment
1. **Create a bot on Telegram:**

    - Go to Telegram and create a new bot using the [BotFather](https://core.telegram.org/bots#botfather).
    - Save the credentials (bot token) provided by BotFather.

2. **Setup ngrok as a proxy server:**

    - Run ngrok to expose your local server to the internet:
      ```bash
      ngrok http 5005
      ```
    - Note the HTTPS URL provided by ngrok.

3. **Configure Rasa credentials:**

    Add your Telegram bot token and ngrok URL to the `credentials.yml` file:
    ```yaml
    telegram:
      access_token: "YOUR_TELEGRAM_BOT_TOKEN"
      verify: "YOUR_BOT_USERNAME"
      webhook_url: "YOUR_NGROK_HTTPS_URL/webhooks/telegram/webhook"
    ```

4. **Deploy the chatbot:**

    Restart your Rasa server to apply the new credentials:
    ```bash
    rasa run
    ```

## Customization
For this project, an additional story plot and training statements specific to the financial/BFSI domain were added to the existing demo model. To retrain the model with the new data, use:
```bash
rasa train
```

## Usage
To interact with the deployed bot, use the following link or username on Telegram:
- [Link to the bot](https://t.me/rasa_assignment_guidonabot)
- Username: `@rasa_assignment_guidonabot`

## Acknowledgments
This project was created to demonstrate the deployment of a Rasa chatbot on Telegram. For more complex models, you can source and deploy existing solutions from GitHub.
