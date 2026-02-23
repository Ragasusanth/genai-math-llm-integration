## Integration of a Mathematical Calulations with a Chat Completion System using LLM Function-Calling

### AIM:
To design and implement a Python function for calculating the volume of a cylinder, integrate it with a chat completion system utilizing the function-calling feature of a large language model (LLM).

### PROBLEM STATEMENT:
To develop a Python-based application that integrates mathematical computation with an LLM-powered chat system using function-calling capability.

The system should:

1. Accept natural language input from the user (e.g., “Find the volume of a cylinder where radius is 7 and height is 12”).

2. Extract the required numerical parameters (radius and height).

3. Call a predefined Python function to compute the volume of the cylinder.

4. Return the computed result in structured JSON format.

5. Handle invalid inputs (such as negative or zero values).
### DESIGN STEPS:

#### STEP 1:
Install required packages

#### STEP 2:
Give the essential function calling code into it

#### STEP 3:
Integrate the function into an LLM-based chat completion system with function-calling capabilities.

### PROGRAM:
```
NAME : RAGA SUSANTH
REG NO : 212224230217
```
```
import json
import math

# Function to calculate volume of a cylinder
def calculate_cylinder_volume(radius, height):
    if radius <= 0 or height <= 0:
        return "Enter a valid value"
    
    volume = math.pi * (radius ** 2) * height
    
    return json.dumps({
        "radius": radius,
        "height": height,
        "volume": round(volume, 2),
        "unit": "cubic units"
    })
```
```
# define a function
functions = [
    {
        "name": "calculate_cylinder_volume",
        "description": "Calculate the volume of a cylinder using radius and height",
        "parameters": {
        A    "type": "object",
            "properties": {
                "radius": {
                    "type": "number",
                    "description": "Radius of the cylinder"
                },
                "height": {
                    "type": "number",
                    "description": "Height of the cylinder"
                }
            },
            "required": ["radius", "height"],
        },
    }
]
```
```
messages = [
    {
        "role": "user",
        "content": "Find the volume of a cylinder where radius is 7 and height is 12"
    }
]
```
```
import openai
```
```
# Call the ChatCompletion endpoint
response = openai.ChatCompletion.create(
    # OpenAI Updates: As of June 2024, we are now using the GPT-3.5-Turbo model
    model="gpt-3.5-turbo",
    messages=messages,
    functions=functions
)
```
```
print(response)
```
```
response_message = response["choices"][0]["message"]
```
```
response_message
```
```
response_message["content"]
```
```
response_message["function_call"]
```
```
json.loads(response_message["function_call"]["arguments"])
```
```
args = json.loads(response_message["function_call"]["arguments"])
```
```
calculate_cylinder_volume(122,133)
```
### OUTPUT:

<img width="877" height="478" alt="image" src="https://github.com/user-attachments/assets/f2ab65fd-e2e5-45d6-a9f8-27be1fb273e2" />

### RESULT:

The experiment successfully demonstrated:
- Integration of Gemini AI with mathematical calculations
- Accurate parameter extraction from natural language
- Precise volume calculations with appropriate unit handling
- Robust error management
- Interactive user interface
