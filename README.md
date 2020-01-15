# Speech Recognition in Unity
Speech Recognition using C# and Unity3D.

![Football game in Unity3D](https://github.com/codemaker2015/Speech-to-text--STT--in-unity/blob/master/Assets/UI/screenshot.png)

## Prerequisites
To run the project, you’ll need the following software components:
* Unity3D 2019.2+

## Source Code
We'll be using the KeywordRecognizer class to detect the voice commands:

```

    public string[] keywords = new string[] { "up", "down", "left", "right" };
    public ConfidenceLevel confidence = ConfidenceLevel.Medium;
    public float speed = 1;

    public Text results;
    public Image target;

    protected PhraseRecognizer recognizer;
    protected string word = "right";

    private void Start()
    {
        if (keywords != null)
        {
            recognizer = new KeywordRecognizer(keywords, confidence);
            recognizer.OnPhraseRecognized += Recognizer_OnPhraseRecognized;
            recognizer.Start();
        }
    }

    private void Recognizer_OnPhraseRecognized(PhraseRecognizedEventArgs args)
    {
        word = args.text;
        results.text = "You said: <b>" + word + "</b>";
    }

    private void OnApplicationQuit()
    {
        if (recognizer != null && recognizer.IsRunning)
        {
            recognizer.OnPhraseRecognized -= Recognizer_OnPhraseRecognized;
            recognizer.Stop();
        }
    }

```

## Exporting the project
KeywordRecognizer is available for Windows Standalone and Windows Store (Windows 8.1 or Windows 10):
* Windows
* Android

