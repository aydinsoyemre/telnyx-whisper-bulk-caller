# README.md

## Automated Call and Transcription

This is an automated call and transcription system that uses Telnyx and OpenAI to make phone calls, play a sound, record the call, and transcribe the recording. The results are stored in a TSV file.

### Prerequisites

- Python 3.6 or higher
- Telnyx account and API key
- OpenAI account and API key
- Install required packages using `pip install -r requirements.txt`

### Usage

1. Replace the placeholder values in the code with your Telnyx and OpenAI API keys:

   ```python
   telnyx.api_key = "xxxxxxxxxxxxxxx"
   openai.api_key = "xxxxxxxxxxxxxxx"
   ```

2. Replace the connection_id and from number in the `call_and_play_sound` function:

   ```python
   call = telnyx.Call.create(connection_id="xxxxxxxxxxxxxxx", to=number, from_="+xxxxxxxxxxxxxxxxx")
   ```

3. Replace the path to the numbers.txt file with the path to your file containing the list of numbers to call:

   ```python
   numbers = load_numbers('/path/to/your/numbers.txt')
   ```

4. Run the script using `python main.py`. The script will make calls to the numbers in the `numbers.txt` file, play a sound, record the call, and transcribe the recording using OpenAI.

### How It Works

- The script loads the list of phone numbers from a text file.
- It uses multithreading to call multiple numbers simultaneously.
- When a call is answered, the script plays a sound and starts recording the call.
- After the call is hung up, the recording is transcribed using OpenAI's Whisper ASR API.
- The results, including the phone numbers, transcriptions, and call durations, are written to a TSV file.

### Webhook Handling

The script also sets up a Flask server to handle incoming webhooks from Telnyx. These webhooks handle different call events, such as call initiation, answering, and hangup.

### Note

Make sure to set up your Telnyx webhooks to point to the server running this script.
