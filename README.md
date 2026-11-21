# Second Chance At Life Career Coach

A Windows desktop career coach built with Python, CustomTkinter, and the Google Gemini API.

## Requirements

- Windows
- Python 3.10 or newer
- A Google Gemini API key 
- An internet connection

## Install

Open PowerShell and run:

```powershell
python -m pip install --upgrade pip
python -m pip install -r requirements.txt
```

If `python` points to a Windows alias or the wrong interpreter, use:

```powershell
& "$HOME\AppData\Local\Python\bin\python.exe" -m pip install -r requirements.txt
```

## Set the API Key

The application reads the API key from the `GOOGLE_API_KEY` environment variable. Do not put the real key in `career_coach.py` or in this README.

For the current PowerShell session:

```powershell
$env:GOOGLE_API_KEY="your-api-key-here"
```

Replace `your-api-key-here` with a key created in Google AI Studio.

Session-only setup is recommended. It does not write the key to the Windows registry or a project file.

Before launching a new terminal, set the variable again:

```powershell
$env:GOOGLE_API_KEY="your-api-key-here"
```

To verify that the variable is set without printing it:

```powershell
if ($env:GOOGLE_API_KEY) { "GOOGLE_API_KEY is set" } else { "GOOGLE_API_KEY is missing" }
```

If a key was previously stored in the Windows user environment, remove it when no longer needed:

```powershell
[Environment]::SetEnvironmentVariable("GOOGLE_API_KEY", $null, "User")
Remove-Item Env:GOOGLE_API_KEY -ErrorAction SilentlyContinue
```

## Run the Application

From the folder containing `career_coach.py`:

```powershell
python career_coach.py
```

Or use the installed Python executable directly:

```powershell
& "$HOME\AppData\Local\Python\bin\python.exe" "career_coach.py"
```

## Security

- Never commit the real API key.
- The app requires explicit consent before sending form data to Gemini.
- The chat history is cleared when the chat window closes or Clear chat is used.
- Do not share terminal output containing the key.
- Use a separate key for public or distributed builds.
- Rotate the key immediately if it may have been exposed.

## Troubleshooting

- `GOOGLE_API_KEY is not set`: set the variable in the terminal or restart VS Code after setting it persistently.
- `No module named customtkinter`: install it with `python -m pip install customtkinter`.
- `No module named google`: install the SDK with `python -m pip install google-genai`.
- `503` response: Google is temporarily unavailable; the app will show the friendly unavailable message.
