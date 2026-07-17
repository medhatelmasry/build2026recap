# Coding with Microsoft Foundry Local

## What is Microsoft Foundry Local?

Foundry Local is an AI solution that runs entirely on the user's device. It also provides an SDK (C#, JavaScript, Rust, and Python) that helps you build apps that interact with Foundry Local.

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

## Exporing CLI commands

Try the following Foundry Local CLI commands:

#### Detect the CLI version:

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

#### View the list of CLI commands:

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

#### Download a model into local cache:

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
#### List models in local cache:

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
#### Remove a model from local cache:

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
#### Download and run a model:

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
<br />

> [!TIP]
> If you get an error when running a model, it may mean that your hardware is incompatible with the specific model that was downloaded. You can try looking ar variants of that model for different processor configurations. To view the variants for a model (Example: qwen2.5-0.5b), type the following command:
>
> ```bash
> foundry model info qwen2.5-0.5b
> ```
>
> You can then try one of the variants like `qwen2.5-0.5b-instruct-generic-cpu` with:
>
> ```bash
> foundry model run qwen2.5-0.5b-instruct-generic-cpu
> ```

___

The above puts the user in a CLI interactive mode. You can then send prompt to the model. Let's ask the model to create for us a C# program that does temperature conversion. Type in the following prompt:

```
Write a C# console app that converts temperature from C to F and also from F to C.
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

#### Exit CLI mode, type:

```bash
/exit
```

___

#### Stop the Foundry service:

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

#### Start the Foundry service:

```bash
foundry service start
```

<details>
<summary>
Expected output:
</summary>
🟢 Service is Started on http://127.0.0.1:64398/, PID 9459!
</details>

## Develop a C# app using Foundry Local SDK

The Foundry Local SDK enables you to ship AI features in your applications that are capable of using local AI models through a simple and intuitive API. The SDK abstracts away the complexities of managing AI models and provides a seamless experience for integrating local AI capabilities into your applications. 

```bash
dotnet new console -o FoundryLocalConsoleApp
cd FoundryLocalConsoleApp
dotnet add package Microsoft.AI.Foundry.Local
dotnet add package Microsoft.Extensions.Logging
dotnet add package Betalgo.Ranul.OpenAI -v 9.1.0
```

Add this to the `.csproj` file right above `</PropertyGroup>`:

```xml
<RuntimeIdentifiers>osx-arm64;osx-x64;win-x64;linux-x64</RuntimeIdentifiers>
```

Replace `Program.cs` with this code that asks the `qwen2.5-0.5b` local AI model the question: `Where did coffee come from?`:

```C#
using Betalgo.Ranul.OpenAI.ObjectModels.RequestModels;
using Microsoft.AI.Foundry.Local;
using Microsoft.Extensions.Logging;

CancellationToken ct = new();

var config = new Configuration {
    AppName = "foundry_local_samples",
    LogLevel = Microsoft.AI.Foundry.Local.LogLevel.Information
};

using var loggerFactory = LoggerFactory.Create(builder => {
    // Intentionally no providers configured; this still yields a valid ILogger instance.
});
ILogger logger = loggerFactory.CreateLogger("FoundryLocalConsoleApp");

// Initialize the singleton instance.
await FoundryLocalManager.CreateAsync(config, logger);
var mgr = FoundryLocalManager.Instance;


// Discover available execution providers and their registration status.
var eps = mgr.DiscoverEps();
int maxNameLen = 30;
Console.WriteLine("Available execution providers:");
Console.WriteLine($"  {"Name".PadRight(maxNameLen)}  Registered");
Console.WriteLine($"  {new string('─', maxNameLen)}  {"──────────"}");
foreach (var ep in eps) {
    Console.WriteLine($"  {ep.Name.PadRight(maxNameLen)}  {ep.IsRegistered}");
}

// Download and register all execution providers with per-EP progress.
// EP packages include dependencies and may be large.
// Download is only required again if a new version of the EP is released.
// For cross platform builds there is no dynamic EP download and this will return immediately.
Console.WriteLine("\nDownloading execution providers:");
if (eps.Length > 0) {
    string currentEp = "";
    await mgr.DownloadAndRegisterEpsAsync((epName, percent) => {
        if (epName != currentEp) {
            if (currentEp != "") {
                Console.WriteLine();
            }
            currentEp = epName;
        }
        Console.Write($"\r  {epName.PadRight(maxNameLen)}  {percent,6:F1}%");
    });
    Console.WriteLine();
} else {
    Console.WriteLine("No execution providers to download.");
}


// Get the model catalog
var catalog = await mgr.GetCatalogAsync();


// Get a model using an alias.
var model = await catalog.GetModelAsync("qwen2.5-0.5b") ?? throw new Exception("Model not found");

// Download the model (the method skips download if already cached)
await model.DownloadAsync(progress =>{
    Console.Write($"\rDownloading model: {progress:F2}%");
    if (progress >= 100f)
    {
        Console.WriteLine();
    }
});

// Load the model
Console.Write($"Loading model {model.Id}...");
await model.LoadAsync();
Console.WriteLine("done.");

// Get a chat client
var chatClient = await model.GetChatClientAsync();

// Create a chat message
List<ChatMessage> messages = new() {
    new ChatMessage { Role = "user", Content = "Where did coffee come from?" }
};

// Get a streaming chat completion response
Console.WriteLine("Chat completion response:");
var streamingResponse = chatClient.CompleteChatStreamingAsync(messages, ct);
await foreach (var chunk in streamingResponse) {
    Console.Write(chunk.Choices[0].Message.Content);
    Console.Out.Flush();
}
Console.WriteLine();

// Tidy up - unload the model
await model.UnloadAsync();
```

> [!NOTE]
> Notice model `qwen2.5-0.5b` in line 59. Change this to any other model or variant of your choice.

<details>
<summary>
Expected output:
</summary>

```bash
Available execution providers:
  Name                            Registered
  ──────────────────────────────  ──────────
  WebGpuExecutionProvider         False

Downloading execution providers:
  WebGpuExecutionProvider          100.0%
Loading model qwen2.5-0.5b-instruct-generic-gpu:4...done.
Chat completion response:
Coffee originated in the Ethiopian Highlands and later spread to other regions due to various factors such as trade, migration, and disease. It''s believed that people first brought coffee from Ethiopia with them when they migrated to other parts of the world. The earliest known records suggest that the first drink made from coffee was consumed by the Shas people in West Africa.

As the demand for coffee grew, more people began to experiment with making their own beverages. By 1750, coffee had been developed into its current form in the Middle East and Asia. It wasn''t until 1826 that an American named Robert Brown invented espresso, which has since become one of the most popular beverages worldwide.

The history of coffee is a story of innovation, trade, and cultural exchange over centuries. Coffee has played a significant role in many societies around the world and continues to be enjoyed today through different methods and traditions.
```
</details>

___

For more information, see the [Foundry Local SDK reference][1].

[1]: https://learn.microsoft.com/en-us/azure/foundry-local/reference/reference-sdk-current