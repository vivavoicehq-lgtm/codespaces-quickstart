# codespaces-quickstart
Get started with Rasa in the browser using GitHub Codespaces.

### Steps

1. **Create a Codespace:**
   - Click on the green "Code" button on this page, then scroll down to "Codespaces".
   - Click on "Create codespace on main".

2. **Set Up Environment:**
   - In the codespace, open the `.env` file from this repo and add your license key to that file.
     ```
     RASA_LICENSE='your_rasa_license_key_here'
     ```
   - Set this environment variables by running 
     ```
     source .env
     ```
   - Activate your python environment by running
     ```
     source .venv/bin/activate
     ```

3. **Initialize a New Project:**
   - In the terminal, run:
     ```
     rasa init --template tutorial
     ```
     and follow the instructions.

4. **Train the Model:**
   - In the terminal, run:
     ```
     rasa train
     ```

5. **Talk to your Bot:**
   - In the terminal, run
     ```
     rasa inspect
     ```
     GitHub will show a notification, click on the green button to view the inspector where you can chat with your assistant.

6. **Run Custom Actions:**
  In Rasa 3.10 and later, custom actions are automatically run as part of your running assistant. To double-check that this is set up correctly, ensure that your `endpoints.yml` file contains the following configuration:
   ```
   action_endpoint:
      actions_module: "actions" # path to your actions package
    ```
   Then re-run your assistant via `rasa inspect` every time you make changes to your custom actions.

7. **MRCS OSCE Coaching Scenario:**
  - The MRCS scenario is in `MRCS B`.
  - Train the model with:
    ```bash
    rasa train --domain "MRCS B/domain.yml" --config "MRCS B/config.yml" --data "MRCS B/data"
    ```
  - Start the assistant and interact with it as a surgical trainee:
    1. "Start the MRCS upper abdominal pain scenario"
    2. Ask structured history questions (`ask_name`, `ask_pain_site`, etc.)
    3. Finalise with a summary and plan, e.g., "I would summarise as follows..."
  - The custom action `action_mrcs_history_summary` generates domain-specific feedback.

8. **Run tests:**
  ```bash
  pytest -q "MRCS B/tests"
  ```
