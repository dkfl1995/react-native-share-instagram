# react-native-share-instagram
Share your image with the Instagram app using `Intents` (iOS & Android)

## Getting started

`$ yarn add @micabe/react-native-share-instagram`

## Automatic installation

`$ react-native link @micabe/react-native-share-instagram`

## Update!!!

* Android installation changed!
    You need to add `import com.reactlibrary.InstagramApplication` and `InstagramApplication` near `ReactApplication` to implement it in your MainApplication.java:
    ```java
    public class MainApplication extends Application implements InstagramApplication, ReactApplication {

    private static CallbackManager mCallbackManager = CallbackManager.Factory.create();

  protected static CallbackManager getCallbackManager() {
    return mCallbackManager;
  }

  private final ReactNativeHost mReactNativeHost = new ReactNativeHost(this) {
    @Override
    public boolean getUseDeveloperSupport() {
      return BuildConfig.DEBUG;
    }

    @Override
    protected List<ReactPackage> getPackages() {
      return Arrays.<ReactPackage>asList(
        new MainReactPackage(),
        new RNSharePackage(),
        ...
      )
    }

    //Add here (after getPackages method)
    public String getFileProviderAuthority() {
      return "com.foodilog.provider";
    }

  }
    ```


## Usage
```javascript
import RNReactNativeSharingWinstagram from 'react-native-sharing-winstagram';

RNReactNativeSharingWinstagram.shareWithInstagram(this.state.fileName, this.state.base64EncodedImageString, message => {
  if (message) alert(message)
}, error => {
  alert(error.message) // error callback for IOs only
})
```

### Troubleshouting

* Make sure you have authorised in `Info.plist` your app to communicate with the Instagram app (iOS):

```xml
<key>LSApplicationQueriesSchemes</key>
<array>
  <string>instagram</string>
</array>

<key>NSPhotoLibraryUsageDescription</key>
<string>This app requires access to the photo library to share on Instagram.</string>
```

### Advanced usage

* You can use the [react-native-fetch-blob](https://github.com/wkh237/react-native-fetch-blob) library to download your remote image and convert it to `.base64()`

### Contribution

* Test library to work with windows OS
