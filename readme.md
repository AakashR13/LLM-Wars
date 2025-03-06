# LLM Wars

LLM Wars is a web-based application that simulates battles between two language models (LLMs). Users can configure the models, set parameters, and initiate battles to see how the models interact with each other.

![Homepage Screenshot](image.png)

## Table of Contents

- [Features](#features)
- [Technologies Used](#technologies-used)
- [Setup](#setup)
- [Usage](#usage)
- [API Endpoints](#api-endpoints)
- [Contributing](#contributing)
- [License](#license)

## Features

- User-friendly interface for configuring LLM parameters.
- Supports multiple battle modes (e.g., custom, basic, roleplay).
- Displays battle results and allows downloading of chat history.
- Demo battles to showcase the application.

## Technologies Used

- **Frontend**: HTML, CSS (Bootstrap), JavaScript
- **Backend**: Python, FastAPI
- **Database**: None (uses JSON files for chat history)
- **API**: RESTful API for communication between frontend and backend

## Setup

### Prerequisites

- Python 3.7 or higher
- Node.js (for any frontend build tools, if needed)

### Backend Setup

1. Clone the repository:
   ```bash
   git clone https://github.com/AakashR13/LLM-Wars
   cd https://github.com/AakashR13/LLM-Wars
   ```

2. Install the required Python packages:
   ```bash
   pip install fastapi uvicorn requests pydantic
   ```

3. Run the FastAPI server:
   ```bash
   python backend/main.py
   ```

### Frontend Setup

1. Open the `frontend/src/index.html` file in your web browser.

## Usage

1. Configure the API endpoint and token in the configuration panel.
2. Select the model and set the number of rounds for the battle.
3. Adjust the temperature settings for both LLMs.
4. Choose a battle mode from the dropdown menu.
5. Click the "Start Battle" button to initiate the battle.
6. View the results displayed on the page, and download the chat history if desired.

## API Endpoints

### Battle Simulation

- **POST** `/battle`
  - Request Body:
    ```json
    {
      "llm1_system_prompt": "string",
      "llm2_system_prompt": "string",
      "endpoint": "string",
      "api_key": "string",
      "model": "string",
      "llm1_temperature": "float",
      "llm2_temperature": "float",
      "num_rounds": "int"
    }
    ```
  - Response:
    ```json
    {
      "round_history": [
        {
          "round": "int",
          "tokens_used": "int",
          "llm1_prompt": "string",
          "llm1_strategy": "string",
          "llm1_message": "string",
          "llm2_prompt": "string",
          "llm2_strategy": "string",
          "llm2_response": "string"
        }
      ],
      "battle_id": "string"
    }
    ```

### Download Chat History

- **GET** `/download/{battle_id}`
  - Response:
    ```json
    {
      "battle_id": "string",
      "round_history": [
        {
          "round": "int",
          "tokens_used": "int",
          "llm1_prompt": "string",
          "llm1_strategy": "string",
          "llm1_message": "string",
          "llm2_prompt": "string",
          "llm2_strategy": "string",
          "llm2_response": "string"
        }
      ]
    }
    ```

### Get Demos

- **GET** `/demos`
  - Response:
    ```json
    {
      "demos": [
        {
          "battle_id": "string",
          "round_history": [
            {
              "round": "int",
              "llm1_message": "string",
              "llm2_response": "string"
            }
          ]
        }
      ]
    }
    ```

## Contributing

Contributions are welcome! Please open an issue or submit a pull request for any improvements or bug fixes.

## License

This project is licensed under the MIT License. See the LICENSE file for details.