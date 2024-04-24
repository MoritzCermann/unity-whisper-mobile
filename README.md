# senits-whisper-mobile

A Unity project that utilizes [unity/sentis-whisper-tiny](https://huggingface.co/unity/sentis-whisper-tiny), specifically adapted for mobile platforms.

## Setup

1. **Download Models**: Download `AudioDecoder_Tiny.sentis`, `AudioEncoder_Tiny.sentis`, and `LogMelSepctro.sentis`.
2. **Add Models**: In the `/Assets` directory, create a folder named `Models` and place the downloaded models there.
3. **Assign Models**: In the Inspector, assign these models to the `RunWhisper` script.

Ideally, you should store these models in the `StreamingAssets` folder and load them at runtime. However, accessing the `StreamingAssets` folder on Android and WebGL platforms is not as straightforward as on other platforms (e.g., you cannot access them directly via `Application.streamingAssetsPath + "/AudioDecoder_Tiny.sentis"`).

### Accessing StreamingAssets on Android and WebGL

On Android and WebGL platforms, you cannot access files in the `StreamingAssets` folder directly as you would on other platforms. Instead, you need to fetch the model files via `UnityWebRequest` from your `StreamingAssets` folder, save/cache them, and then load (`ModelLoader.Load`) the model.

### Error

At the time of writing i choose a workaround because loading the model got me an error: “Error Unable to Load type Unity.Sentis.Layers.Gather required for deserialisation”. What i did is exactly what i described in **Setup**. I basically put the models in the Asset/Models folder instead of the StreamingAsset folder.

For more detailed information on this challenge and possible workaround approaches, refer to this [forum post](https://discussions.unity.com/t/does-sentis-work-on-android-mobile/346403/5).
And this [forum post](https://discussions.unity.com/t/loading-asset-in-android-using-streamingassets-and-unitywebrequest/231278/2).

## Requirements / Versions

- Unity 2023.2.1f1
- Sentis 1.3.0-pre

## Note:
You might want to change the Backendtype inside `RunWhisper.cs` depending on your device. 

## Tested On

- Pixel 6  -> working
- Quest 3  -> not tested
- WebGl    -> not tested

---

