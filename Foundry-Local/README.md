# Coding with Microsoft Fondry Local

## What is Microsoft Foundry Local?

Foundry Local is a local AI solution that runs entirely on the user's device. It also provides an SDK (C#, JavaScript, Rust, and Python) that helps you build app that interact with Foundry Local.

## Installation

To install Foundry Local, follow these steps:

### Windows

```bash
winget install Microsoft.FoundryLocal
```

### macOS (only on silicon chips)

```bash
brew tap microsoft/foundrylocal
brew trust microsoft/foundrylocal
brew install foundrylocal
```

### CLI commands

Try the following Foundry Local CLI commands:

#### To detect the CLI version:

```bash
foundry --version
```

<details>
<summary>
Expected output:
</summary>
0.8.119
</details>

---

#### To view the list of CLI commands:

```bash
foundry --help
```

<details>
<summary>
Expected output:
</summary>
Description:<br />
  Foundry Local CLI: Run AI models on your device.
  
🚀 Getting started:
  
1. To view available models: foundry model list
2. To run a model: foundry model run <model>

EXAMPLES:<br />
   foundry model run phi-3-mini-4k

Usage:<br />
  foundry [command] [options]

Options:<br />
  -?, -h, --help  Show help and usage information<br />
  --version       Show version information<br />
  --license       Display foundry license information

Commands:<br />
  __model__    Discover, run and manage models<br />
  __cache__    Manage the local cache<br />
  __service__  Manage the local model inference service
</details>

___

#### To download a model into local cache:

```bash
foundry model download qwen2.5-0.5b
```

<details>
<summary>
Expected output:
</summary>
Downloading qwen2.5-0.5b-instruct-generic-gpu:4...

. . .  T R U N C A T E D . . .

[##################################  ]  94.85 % [Time remaining: about 1s]<br />  [##################################  ]  95.22 % [Time remaining: about 1s]<br />  [##################################  ]  95.59 % [Time remaining: about 1s]<br />[##################################  ]  95.96 % [Time remaining: about 1s]<br />[##################################  ]  96.33 % [Time remaining: about 1s]<br />[##################################  ]  96.69 % [Time remaining: about 1s]<br />[##################################  ]  97.06 % [Time remaining: about 1s]<br />[################################### ]  97.43 % [Time remaining: about 1s]<br />[################################### ]  97.79 % [Time remaining: about 1s]<br />[################################### ]  98.16 % [Time remaining: about 1s]<br />[################################### ]  98.53 % [Time remaining: about 1s]<br />[################################### ]  98.90 % [Time remaining: about 1s]<br />[################################### ]  99.27 % [Time remaining: about 1s]<br />[################################### ]  99.63 % [Time remaining: about 1s]<br />[####################################] 100.00 % [Time remaining: about 0s]<br />[####################################] 100.00 % [Time remaining: about 0s] 85.9 MB/s <br />
Tips:<br />
- To find model cache location use: foundry cache location<br />
- To find models already downloaded use: foundry cache ls
</details>

___
#### To list models in local cache:

```bash
foundry cache list
```

<details>
<summary>
Expected output:
</summary>
💾 qwen2.5-0.5b &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;    qwen2.5-0.5b-instruct-generic-gpu:4
</details>

___
#### To remove a model from local cache:

```bash
foundry cache remove qwen2.5-0.5b
```

<details>
<summary>
Expected output:
</summary>
⚠️ This will delete model 'qwen2.5-0.5b (qwen2.5-0.5b-instruct-generic-gpu:4)' from cache.<br />
⚠️ Are you sure you want to delete this model from the local cache? (y/n)<br />
y<br />
Deleted model qwen2.5-0.5b-instruct-generic-gpu:4 from the cache.
</details>

___
#### To download an run a model:

```bash
foundry model run qwen2.5-0.5b
```

<details>
<summary>
Expected output:
</summary>
Downloading qwen2.5-0.5b-instruct-generic-gpu:4...<br />
[####################################] 100.00 % [Time remaining: about 0s]&nbsp;&nbsp;105.2 MB/s<br />
🕛 Loading model... <br />
🟢 Model qwen2.5-0.5b-instruct-generic-gpu:4 loaded successfully<br />
<br />
Interactive Chat. Enter /? or /help for help.<br />
Press Ctrl+C to cancel generation. Type /exit to leave the chat.<br />
<br />
Interactive mode, please enter your prompt<br />
> 
</details>

___

The above puts the user in a CLI interactive mode. You can then prompt the model. Let's ask the model to create for us a C# program that does temperature conversion. Type in the following prompt:

```bash
Write a C# console app that converts temperature from Celcius to Fahrenheit and also from Fahrenheit to Celcius.
```

<details>
<summary>
Expected output:
</summary>
🧠 Thinking...<br />
🤖 Certainly! Below is a simple console application written in C# that takes user input for Celsius temperature and converts it to either Fahrenheit or vice versa.

```csharp
using System;
using System.Windows.Forms;

namespace TemperatureConverterApp
{
    class Program
    {
        static void Main(string[] args)
        {
            try
            {
                Console.WriteLine("Enter the Temperature (in Celcius): ");
                int celsius = Convert.ToInt32(Console.ReadLine());

                bool convertToFahrenheit = false;
                string result;

                if (Convert.ToBoolean(calculateCtoF(celsius)) == true)
                    result = "Celsius to Fahrenheit: ";
                else
                    result = "Temperature not converted";

                result += $"Celsius {result}";
                
                if (convertToFahrenheit) 
                {
                    Console.WriteLine($"Result: Fahrenheits");
                    return;
                }

                Console.WriteLine(result);
            }
            catch
            {
                Console.WriteLine("Invalid Input");
            }
        }

        public static bool calculateCtoF(int celsius)
        {
            double fahrenheit = 9/5 * celsius + 32;
            double result = Math.Round(fahrenheit, 1);
            
            // Round down to the nearest integer since temperatures must be whole numbers
            if (fahrenheit.ToString() != "0")
                return true;
            else
                return false;
        }
        
        public static bool calculateFtoc(double fahrenheit)
        {
            double celsius = fahrenheit - 32 * 5 / 9;
            double result = Math.Round(celsius, 1);

            // Round down to the nearest integer since temperatures must be whole numbers
            if (celsius.ToString() != "0")
                return true;
            else
                return false;
        }
    }
}
```

### Explanation:

1. **Imports**: The code starts with importing necessary namespaces (`System` and `System.Windows.Forms`). It's assumed you have this namespace available.

2. **Program Class**:
   - This contains the main program logic.
   
3. **calculateCtoF Function**:
   - Calculates the temperature in Fahrenheit given Celsius temperature.
   - If successful, calculates the equivalent number of degrees Celsius based on the provided value and rounds it to the closest integer.
   - Outputs the result along with any additional information like "Celsius" or "Temperature not converted".

4. **calculateFtoc Function**:
   - Calculates the equivalent temperature in Celcius given the equivalent degrees Fahrenheit.
   - Same as `calculateCtoF`, but used for converting degrees Fahrenheit back to Celsius.

### Example Usage:

If you run the program, pressing the keyboard will take an input to calculate the correct conversion type and output results accordingly.

Example Input: 25

- If calculated using Celsius, it will print: "Celsius", then "25".
- If converted to Fahrenheit, it will print: "Temperature not converted", then "25". 

This example only demonstrates basic conversions between the two temperature scales and does not handle invalid inputs like non-numerical characters which would throw exceptions during parsing.
</details>

___

#### To exit CLI mode, type:

```bash
/exit
```

___

#### To stop the Foundry service:

```bash
foundry service stop
```

<details>
<summary>
Expected output:
</summary>
🔴 Service is stopped.
</details>

___

#### To start the Foundry service:

```bash
foundry service start
```

<details>
<summary>
Expected output:
</summary>
🟢 Service is Started on http://127.0.0.1:64398/, PID 9459!
</details>