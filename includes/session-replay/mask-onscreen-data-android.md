### Mask on-screen data

By default session replay will hide all user input (EditText, inputType="password")

The Session Replay SDK offers three ways to mask user input, text, and other View components. This can be enabled in both the layout XML and Kotlin/Java code.

#### Privacy tags in layout XML

Privacy control

| View              | Description                                                                                                                                                                                                                                                                                 |
|-------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `<EditText>`      | Session Replay masks all text input fields by default. When a users enters text into an input field, Session Replay captures asterisks in place of text. To *unmask* a text input, add the tag `amp-unmask`. For example: `<EditText android:tag="amp-unmask" android:text="Unmask this">`. |
| `<TextView>`      | To mask text within non-input elements, add the tag `amp-mask`. For example, `<TextView android:tag="amp-mask" android:text="Mask this"/>`. When masked, Session Replay captures masked text as a series of asterisks.                                                                      |
| non-text elements | To block a non-text element, add the tag `amp-block`. For example, `<ImageView android:tag="amp-block"/>`. Session Replay replaces blocked elements with a placeholder of the same dimensions.                                                                                              |


#### Privacy methods on the Session Replay SDK

To use privacy methods first import the SessionReplay class. Then call one of the methods below.

```kotlin
import com.amplitude.android.SessionReplay
```

| Method               | Description                                                                                                                                                                                                                                                                          |
|----------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `unmask(view: View)` | Session Replay masks all text input views by default. When a users enters text into an input view, Session Replay captures asterisks in place of text. To *unmask* a text input, call `SessionReplay.unmask(view)` where `view` is a reference to the text input you want to unmask. |
| `mask(view: View)`   | To mask text within non-input views, call `SessionReplay.mask(view)` where `view` is a reference to the text input you want to mask. When masked, Session Replay captures masked text as a series of asterisks.                                                                      |
| `block(view: View)`  | To block a non-text view, call `SessionReplay.unmask(view)` where `view` is a reference to the you want to block. Session Replay replaces blocked views with a placeholder of the same dimensions.                                                                                   |