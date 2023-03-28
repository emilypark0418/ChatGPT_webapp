# WebApp Integration with ChatGPT API

- target model: gpt-3.5-turbo (ChatGPT model)

=> Most capable GPT-3.5 model and optimized for chat at 1/10th the cost of text-davinci-003.

```
    def submit_request(self, prompt):
        """Calls the OpenAI API with the specified parameters."""
        response = openai.ChatCompletion.create(
          model="gpt-3.5-turbo",
          messages= [
                {"role": "system", "content": "You are a helpful assistant."},
                {"role": "user", "content": self.craft_query(prompt)}
         ]
        )
```

* Syntax Difference with GPT3 API:
1. ChatCompletion module should be used instead of Completion module
2. Inside the create function, 'model' parameter should be used instead of the 'engine' parameter
3. Openai library should be updated to 0.27.2
4. 'message' parameter is a must-have parameter and 'roles' of the system and user should be clearly mentioned

## Requirements

Coding-wise, you only need Python. But for the app to run, you will need:

* API key from the OpenAI API beta invite
* Python 3
* `yarn`
* Node 16

Instructions to install Python 3 are [here](https://realpython.com/installing-python/), instructions to install `yarn` are [here](https://classic.yarnpkg.com/en/docs/install/#mac-stable) and we recommend using nvm to install (and manage) Node (instructions are [here](https://github.com/nvm-sh/nvm)).

## Setup Tips

First, clone or fork this repository. Then to set up your virtual environment, do the following:

1. Create a virtual environment in the root directory: `python -m venv $ENV_NAME`

2. Activate the virtual environment: ` source $ENV_NAME/bin/activate` (for MacOS, Unix, or Linux users) or ` .\ENV_NAME\Scripts\activate` (for Windows users)

3. Install requirements: `pip install -r api/requirements.txt`

4. To add your secret key: create a file anywhere on your computer called `openai.cfg` with the contents `OPENAI_KEY=$YOUR_SECRET_KEY`, where `$YOUR_SECRET_KEY` looks something like `'sk-somerandomcharacters'` (including quotes). If you are unsure what your secret key is, navigate to the [API Keys page](https://beta.openai.com/account/api-keys) and click "Copy" next to a token displayed under "Secret Key". If there is none, click on "Create new secret key" and then copy it.

5. Set your environment variable to read the secret key: run `export OPENAI_CONFIG=/path/to/config/openai.cfg` (for MacOS, Unix, or Linux users) or `set OPENAI_CONFIG=/path/to/config/openai.cfg` (for Windows users). For example, `set OPENAI_CONFIG=/Users/cwp94/Documents/Projects/gpt3-sandbox/openai.cfg`

6. Run `yarn install` in the root directory
If you are a Windows user, to run the demos, you will need to modify the following line inside `api/demo_web_app.py`:
`subprocess.Popen(["yarn", "start"])` to `subprocess.Popen(["yarn", "start"], shell=True)`.

7. Run the following command to run the app
```
python examples/run_general_knowledge_q_and_a_app.py
```



