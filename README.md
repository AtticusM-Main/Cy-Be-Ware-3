# Cy-Be-Ware-3

A Windows desktop Cybersecurity Awareness Assistant built with C# and WPF (XAML).
It teaches users about online safety and helps them manage cybersecurity tasks
through a chat interface, a quiz, and an activity log.

## Requirements

- Windows 10 or 11
- .NET 10 SDK
- Visual Studio 2022/2026 or `dotnet` CLI

## Build and Run

```
dotnet build
dotnet run --project Cy-B-ware/Cy-B-ware.csproj
```

In Visual Studio, open `Cy-B-ware.slnx`, set `Cy-B-ware` as the startup project and press F5.

## Project Structure

```
Cy-B-ware/
  App.xaml / App.xaml.cs        Application entry point and resources
  Theme.xaml                    Colours and control styles (black, white, blue)
  MainWindow.xaml / .cs         Main window: chat, tasks, quiz, activity log
  Core/
    ChatbotEngine.cs            Keyword responses, sentiment, NLP intent routing
    QuizGame.cs                 Quiz questions, scoring and feedback
    ActivityLog.cs              Records and summarises bot actions
  Models/
    ChatMessage.cs              A single chat bubble
    TaskItem.cs                 A cybersecurity task with optional reminder
    QuizQuestion.cs             A quiz question (multiple choice or true/false)
    ActivityEntry.cs            A timestamped log entry
```

## Features

### Chat (Parts 1 and 2)
Keyword recognition answers questions on password safety, phishing, safe browsing,
2FA, malware and social engineering. Sentiment detection adjusts the tone when the
user sounds worried, confused or frustrated. Some answers vary between visits.

### Task Assistant with Reminders (Part 3, Task 1)
Add cybersecurity tasks such as "Enable two-factor authentication" from the Tasks
tab or from the chat. Each task can carry a reminder date and be marked done or
deleted.

### Cybersecurity Quiz (Part 3, Task 2)
Twelve questions mixing multiple-choice and true/false. Questions appear one at a
time with instant feedback and a short explanation, then a final score and message.

### NLP Simulation (Part 3, Task 3)
The chat recognises intent even when phrased differently. "Remind me to update my
password tomorrow" creates a task with a reminder; "add a task to enable 2FA" adds a
task; "start quiz" and "show activity log" trigger those features. Date words such as
today, tomorrow, next week and "in 3 days" are read from the sentence.

### Activity Log (Part 3, Task 4)
Every significant action (tasks, reminders, quiz attempts, recognised commands) is
recorded with a timestamp. The Activity Log tab shows the last 10 actions, with a
"Show full history" option. Typing "what have you done for me" prints a summary in
the chat.

## Voice Greeting (optional)
If a file named `greeting.wav` is placed next to the built executable, it plays once
on startup. The app runs normally without it.

## Update Log

### 2026-06-26  -  Part 3 / POE
- Converted the project from a console application to a WPF (XAML) desktop GUI.
- Removed the Spectre.Console dependency; ported the Part 1/2 response logic into
  `ChatbotEngine`.
- Added the Task Assistant with reminders (Tasks tab and chat commands).
- Added the cybersecurity quiz with 12 questions, instant feedback and scoring.
- Added the NLP intent routing for tasks, reminders, quiz and log commands.
- Added the Activity Log with timestamps and a last-10 view plus full history.
- Added sentiment detection to the chat replies.
- Applied a black, white and blue theme with custom button, input and tab styles.
- Rewrote this README and documented the new structure.

### 2026-05-30  -  Part 2
- Expanded the keyword response system to cover more cybersecurity topics.
- Added randomised answers for repeated questions to add variety.
- Improved input validation and the console interface.

### 2026-04-25  -  Part 1
- Initial console chatbot: ASCII logo, voice greeting, name capture with validation
  and the first set of keyword responses.
