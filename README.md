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
python -m pip install customtkinter google-genai
```

If `python` points to a Windows alias or the wrong interpreter, use:

```powershell
& "$HOME\AppData\Local\Python\bin\python.exe" -m pip install customtkinter google-genai
```

## Set the API Key

The application reads the API key from the `GOOGLE_API_KEY` environment variable. Do not put the real key in `career_coach.py` or in this README.

For the current PowerShell session:

```powershell
$env:GOOGLE_API_KEY="your-api-key-here"
```

Replace `your-api-key-here` with a key created in Google AI Studio.

For future sessions in Windows, set the user-level variable in PowerShell:

```powershell
[Environment]::SetEnvironmentVariable("GOOGLE_API_KEY", "your-api-key-here", "User")
```

Close and reopen PowerShell or VS Code after setting a persistent key.

Verify that the key is set without printing it:

```powershell
[Environment]::GetEnvironmentVariable("GOOGLE_API_KEY", "User") -ne $null
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
- Do not share terminal output containing the key.
- Use a separate key for public or distributed builds.
- Rotate the key immediately if it may have been exposed.

## Troubleshooting

- `GOOGLE_API_KEY is not set`: set the variable in the terminal or restart VS Code after setting it persistently.
- `No module named customtkinter`: install it with `python -m pip install customtkinter`.
- `No module named google`: install the SDK with `python -m pip install google-genai`.
- `503` response: Google is temporarily unavailable; the app will show the friendly unavailable message.
