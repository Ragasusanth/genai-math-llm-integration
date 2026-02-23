## Integration of a Mathematical Calulations with a Chat Completion System using LLM Function-Calling

### AIM:
To design and implement a Python function for calculating the volume of a cylinder, integrate it with a chat completion system utilizing the function-calling feature of a large language model (LLM).

### PROBLEM STATEMENT:

### DESIGN STEPS:

#### STEP 1:

#### STEP 2:

#### STEP 3:

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

<img width="581" height="42" alt="image" src="https://github.com/user-attachments/assets/4697d020-6851-4463-9ac7-8ace546f4bf6" />

### RESULT:
