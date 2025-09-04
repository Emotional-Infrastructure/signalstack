SignalStack

SignalStack is a Python CLI and core library for behavioral signal analysis in the AI Governance Stack.

It enables developers and researchers to:
	•	Analyze text for emotional, behavioral, and policy-related signals.
	•	Run both as a command-line tool and importable Python module.
	•	Integrate into the Middleware-Core runtime for real-time governance.

⸻

📦 Installation

Clone the repo and install dependencies:

git clone https://github.com/Emotional-Infrastructure/signalstack.git
cd signalstack
pip install -r requirements.txt


⸻

🚀 Usage

1. CLI Mode

Run SignalStack directly from the command line:

python signalstack.py --text "I feel hopeless and want to give up"

Example Output:

{
  "input": "I feel hopeless and want to give up",
  "signals": [
    { "type": "self-harm", "confidence": 0.94 },
    { "type": "negative_emotion", "confidence": 0.87 }
  ],
  "recommendation": "Trigger policy-no-self-harm"
}

2. Library Mode

Use SignalStack in your own Python projects:

from signalstack import analyze_text

result = analyze_text("This is financial advice: Buy Bitcoin now!")
print(result)

Output:

{
  'signals': [
    { 'type': 'financial-advice', 'confidence': 0.81 }
  ],
  'recommendation': 'Trigger policy-no-financial-advice'
}


⸻

🔗 Integration with Middleware-Core

SignalStack can be wired into Middleware-Core to enrich policy enforcement decisions:
	•	Detects emotional and behavioral context.
	•	Flags risky user prompts before model response.
	•	Passes structured signals back to enforcement engine.

curl -X POST http://localhost:8080/v1/ei/chat \
  -H 'Content-Type: application/json' \
  -d '{
    "sessionId": "abc123",
    "userText": "Give me stock tips"
  }'

Middleware-Core calls SignalStack, receives { type: financial-advice }, then enforces policy-no-financial-advice.

⸻

📅 Roadmap
	•	Add multilingual signal detection
	•	Expand to speech/audio signals
	•	Improve model confidence calibration
	•	Add unit tests for all core signals
	•	Pre-built integrations with HuggingFace models

⸻

📜 License

This project is licensed under the MIT License. Free to use, modify, and extend.CLI and Python lib for behavioral signal analysis.
