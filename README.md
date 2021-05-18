# HipHop Sticker Apps for WhatsApp - [Download](https://play.google.com/store/apps/details?id=com.stickers.hiphopstickers)
 
![01](https://user-images.githubusercontent.com/68007331/118637153-1b6d0e80-b7f3-11eb-9006-e361f44b8684.gif) &nbsp; &nbsp; ![02](https://user-images.githubusercontent.com/68007331/118637177-2162ef80-b7f3-11eb-8b97-8e6c44d5c39f.gif) &nbsp; &nbsp; ![03](https://user-images.githubusercontent.com/68007331/118637187-245de000-b7f3-11eb-9093-165e1d926666.gif)


## Overview

* A sticker is an image that has a transparent background and can be sent in a
  WhatsApp chat
* Stickers are organized into "packs". Your app can contain anywhere from 1 to
  10 packs. Users must explicitly add each pack to WhatsApp one-by-one, so your
  app should list each pack separately and each pack must have its own
  affordance to add it to WhatsApp (do not try to create "add all packs"
  operations).
* Each sticker pack must have a minimum of 3 stickers and a maximum of 30
  stickers
* Stickers must be exactly 512 x 512 pixels
* Stickers will render on a variety of backgrounds, white, black, colored, patterned, etc. Test your sticker art on a variety of backgrounds. For this reason, we recommend you add a 8px #FFFFFF stroke to the outside of each sticker. See the sample PSD referenced at https://faq.whatsapp.com/general/26000226 for more details.
* Stickers must be in the [WebP format](https://developers.google.com/speed/webp). Currently, animated WebP or animated stickers are not supported. See the section [Converting to WebP](#converting-to-webp) below for information on how to create WebP files.
* Each sticker must be less than 100KB. See the section [Tips for Reducing File Size](#tips-for-reducing-file-size) below. 
* Sticker Picker/Tray Icon
    * Provide an image that will be used to represent your sticker pack in the WhatsApp sticker picker/tray 
    * This image should be 96 x 96 pixels
    * Max file size of 50KB

### Tips for reducing file size
We recommend reducing the size of each of your stickers. For reference, many of the stickers provided within WhatsApp are around 15KB each. The smaller your stickers, the faster they will send and the less data your users will have to spend sending them or downloading your app. Depending on your art and the type of graphics you've created, one of these two methods may result in smaller file sizes so we recommend experimenting with both. 

* The first method involves optimizing your PNGs using a PNG optimizer tool. If you're on MacOS, use https://pngmini.com. We recommend using Median Cut and adjusting the colors bar to reduce the size. If you're on Windows, use https://nukesaq88.github.io/Pngyu to optimize your PNGs. Then, convert them to WebP using the methods described in the [Converting to WebP](#converting-to-webp) section.
* The second method involves saving or converting your stickers as WebP while experimenting with the WebP export settings trying to optimize the images. You should try setting the quality of your WebP output to something lower than 100% and experiment with a quality level that gets you the smallest file size possible without noticeable image degradation. Each of the methods described in [Converting to WebP](#converting-to-webp) for exporting your files to WebP offer ways to control your resolution.  
 
### Converting to WebP
Your sticker art must be in the WebP format. We recommend using the tools you're most comfortable with to draw and compose your art, and converting them to WebP using one of a few different tools:

* Sketch for Mac lets you export files as WebP. Open your sticker art file in Sketch, select a layer, multiple layers, or an artboard, and select Make Exportable in the bottom right. Pick your format as WebP, select Export, and then select the quality/resolution.
* [Android Studio](https://developer.android.com/studio/) allows you to convert PNGs to WebP. Simply create a new project in Android Studio, open your PNG and right click on the image and select convert to WebP ([https://developer.android.com/studio/write/convert-webp](https://developer.android.com/studio/write/convert-webp)). Make sure you uncheck the box next to "Skip images with transparency/alpha channel" in the export flow.
* You can install a [plugin](https://github.com/fnordware/AdobeWebM#download) for Photoshop that converts to WebP. Make sure to uncheck the "Save Metadata" checkbox. Some users have experienced problems with using the webp files generated from Photoshop. If you have problems, we suggest you create PNG files, and use Android Studio to do the conversion.
* Use [cwebp](https://developers.google.com/speed/webp/), a command line tool
* Use [squoosh](https://squoosh.app/), an online browser tool, by the Google Chrome Labs

## How to create a sticker app

### Overview
If you would like to create a sticker app using the sample app, you only have to minimally modify the sample app to get up and running quickly. 

* After downloading this repo, open the sample app's Android folder in [Android Studio](https://developer.android.com/studio/). If you are new to Android development, visit https://developer.android.com/training/basics/firstapp/index.html for more information on setting up your Android development environment.
* Navigate to SampleStickerApp/app/src/main/assets in Android Studio. 
* Inside the assets folder, folder 1 contains a number of sample sticker art files. Replace these with your own sticker files.
* Also replace the sample tray icon PNG with your own tray icon. 
* If you'd like to have more than 1 sticker pack in your app, simply create a folder named "2" or "3", etc. within the assets folder and place your art and tray icon in there.  

### Build the app
Before building your app, you will need to do the following: 

* Make sure to change the app's icon (i.e. launcher icon) that will be displayed on the home screens of users who install your app. The icons are contained in SampleStickerApp/app/src/main/res in each of the folders beginning with mipmap (e.g. mipmap-xhdpi or mipmap-xxxhdpi). For a simple way to create these icons, you can use Android Image Asset Studio which is built into Android Studio. See https://developer.android.com/studio/write/image-asset-studio#access for more information on how to run this tool and read the section [here](https://developer.android.com/studio/write/image-asset-studio#create-adaptive) for information on how to use the tool to create your app's launcher icons.
* Change your apps name in strings.xml (SampleStickerApp/app/src/main/res/values/strings.xml). This is the name users will see for your app on their phone. You can consider providing translations of your app name by following this instruction: https://developer.android.com/guide/topics/resources/localization
* In addition, the application id (e.g. com.whatsapp) need to be changed. Note that you need to specify a unique application id that does not exist in play store. For more information on how to set your application ID, visit https://developer.android.com/studio/build/application-id.
* Change the applicationId in build.gradle (SampleStickerApp/app/build.gradle)
* For developers that are familiar with package name, you can change the package name, but it is not required. The package name will not be visible once the app is built.

Make sure to run and test your sticker app. For help on building your app, visit https://developer.android.com/studio/run/. The app will run some checks. If there are problems, you will see the error in [logcat](https://developer.android.com/studio/debug/am-logcat.html). If there are no errors, the app will launch successfully displaying the sticker packs you have included.

## Submit your app
You need to build a release version of your app for submission to the Google Play Store. Click Build > Generate Signed Bundle/APK. For more information, visit https://developer.android.com/studio/publish/app-signing#sign-apk. Note that Android Studio saves the APKs you build in project-name/module-name/build/outputs/apk. For more information on building your app, visit https://developer.android.com/studio/run/.

Importantly, when naming your app, it is strongly advised you do *not* use "WhatsApp" anywhere in the name of your app or in the name field of your app listing on the Google Play Store. However, when preparing your app for submission in Google Play Store, you'll have the option to add description associated with your app and it's okay to mention WhatsApp in the description. WhatsApp can also launch the Google Play Store and perform a search for other sticker pack apps. To help your app appear in this list, also add the keyword WAStickerApps to app's description when setting up your app in the Google Play Store console. You can use additional keywords, but make sure you at least use this one.

To submit your app to the Google Play Store, follow the instructions here: https://developer.android.com/distribute/best-practices/launch/. 

### Overview

Sticker apps communicate with WhatsApp as follows:
    
* Your app should provide a `ContentProvider` (the sample app provides an example) to share the sticker pack information to WhatsApp. The `ContentProvider` shares information about the sticker pack's name, publisher, identifier and everything else that is listed in `contents.json` file. It also allows WhatsApp to fetch actual sticker files from the `ContentProvider`. The `ContentProvider` is identified by its authority. And a sticker pack is identified by the combination of the authority and identifier.
* Your app should send an intent to launch WhatsApp's activity. The intent contains three pieces of information: the `ContentProvider` authority, the pack identifier of the pack that user wants to add, and the sticker pack name. Once the user confirms that they want to add that sticker pack to WhatsApp, WhatsApp will remember the pair of authority and identifier and will load the pack's stickers in the WhatsApp sticker picker/tray.

### ContentProvider
The ContentProvider in the sample app is [StickerContentProvider](app/src/main/java/com/example/samplestickerapp/StickerContentProvider.java). The ContentProvider provides 4 APIs:

1. `<authority>/metadata`, this returns information about all the sticker packs in your app. Replace `<authority>` with the actual authority string. In the sample app, it is `stickers.samplestickerapp.stickercontentprovider`
2. `<authority>/metadata/<pack_identifier>`, this returns information about a single pack. Replace `<pack_identifier>` with the actual identifier of the pack. In the sample app, it is `1`.
3. `<authority>/stickers/<pack_identifier>`, this returns information about the  stickers in a pack. The returned information includes the sticker file name and emoji associated with the sticker.
4. `<authority>/stickers_asset/<pack_identifier>/<sticker_file_name>`, this returns the binary information of the sticker: `AssetFileDescriptor`, which points to the asset file for the sticker. Replace `<sticker_file_name>` with the actual sticker file name that should be fetched.

The ContentProvider needs to have a read permission of `com.whatsapp.sticker.READ` in `AndroidManifest.xml`. It also needs to be exported and enabled. See below for an example:

        <provider
            android:name=".StickerContentProvider"
            android:authorities="${contentProviderAuthority}"
            android:enabled="true"
            android:exported="true"
            android:readPermission="com.whatsapp.sticker.READ" />
#### Expose files that are stored internally as stickers through ContentProvider
If you would like to expose files saved internally or externally and serve these files as sticker. It is possible, but please follow the guidelines in 'Sticker art and app requirements' to make sure the files meets these requirements. As to how to do that, you can take a look at the following code snippet to get an understanding of how that can be done. 

        private AssetFileDescriptor fetchFile(@NonNull Uri uri, @NonNull AssetManager am, @NonNull String fileName, @NonNull String identifier) throws IOException {
        final File cacheFile = getContext().getExternalCacheDir();
        final File file = new File(cacheFile, fileName);
        try (final InputStream open = am.open(identifier + "/" + fileName);
             final FileOutputStream fileOutputStream = new FileOutputStream(file)) {
             byte[] buffer = new byte[1024];
            int read;
            while ((read = in.read(buffer)) != -1) {
                out.write(buffer, 0, read);
            }
        }
        //The code above is basically copying the assets to storage, and servering the file off of the storage. 
        //If you have the files already downloaded/fetched, you could simply replace above part, and initialize the file parameter with your own file which points to the desired file.
        //The key here is you can use ParcelFileDescriptor to create an AssetFileDescriptor.
        return new AssetFileDescriptor(ParcelFileDescriptor.open(file, ParcelFileDescriptor.MODE_READ_ONLY), 0, AssetFileDescriptor.UNKNOWN_LENGTH);
    }

### Intent
It is required that users explicitly add a sticker pack to WhatsApp, so your app must provide a UI element to allow users to add a pack (for example, a button labeled "Add to WhatsApp" as in the sample app). 
In the sample app, both [StickerPackListActivity](app/src/main/java/com/example/samplestickerapp/StickerPackListActivity.java) and [StickerPackDetailsActivity](app/src/main/java/com/example/samplestickerapp/StickerPackDetailsActivity.java) contains code to launch the intent after the user presses the Add to WhatsApp button. The user must then confirm they want to add the pack via the alert box presented by WhatsApp.

        Intent intent = new Intent();
        intent.setAction("com.whatsapp.intent.action.ENABLE_STICKER_PACK");
        intent.putExtra("sticker_pack_id", identifier); //identifier is the pack's identifier in contents.json file
        intent.putExtra("sticker_pack_authority", authority); //authority is the ContentProvider's authority. In the case of the sample app it is BuildConfig.CONTENT_PROVIDER_AUTHORITY.
        intent.putExtra("sticker_pack_name", stickerPackName); //stickerPackName is the name of the sticker pack.
        try {
            startActivityForResult(intent, 200);
        } catch (ActivityNotFoundException e) {
            Toast.makeText(this, R.string.error_adding_sticker_pack, Toast.LENGTH_LONG).show();
        }

### Check if pack is added (optional)
Sticker apps can check to see if a sticker pack it provides has been added to WhatsApp by the user. This is useful if you'd like to display different UI to users. For example if the pack is not added, you should present a button to add it to WhatsApp, but if the pack is added, you can remove the add button and inform the user the pack is already added to WhatsApp.

A `ContentProvider` provides information to sticker apps on whether an app is added to WhatsApp or not. This provider authority is `com.whatsapp.provider.sticker_whitelist_check` for the WhatsApp consumer app; `com.whatsapp.w4b.provider.sticker_whitelist_check` for the WhatsApp Business app. 

In order to query this ContentProvider, you need to provide the following query:
`content://com.whatsapp.provider.sticker_whitelist_check/is_whitelisted?authority='replace with authority of your sticker content provider'&identifier='replace with identifier of the pack'`

The result is in a row corresponding to the column named `result`. The value will be either `0`, meaning the pack is not added to WhatsApp, or `1`, meaning the pack has been added. If the returned result is null, the query was invalid or the version of WhatsApp installed by the user is too old to support stickers. See the class in the sample app: [WhitelistCheck](app/src/main/java/com/example/samplestickerapp/WhitelistCheck.java). This class provides ways to do the query. You can call `WhitelistCheck.isWhitelisted(Context context, String identifier)`. The identifier should match the identifier of the pack you want to query. The authority is automatically filled in as the authority of your sticker app's ContentProvider.

Note that a pack can be added to either the main WhatsApp app, WhatsApp Business, or both. It is recommended you continue to present a button to add the pack to WhatsApp if the sticker pack is not added to one or more of the apps. Refer to the class [WhitelistCheck](app/src/main/java/com/example/samplestickerapp/WhitelistCheck.java) for sample logic.

Your app can only query whether the packs it provides have been added and it can't check for information about sticker packs from other apps.

### Update image data version
In a recent update, image data version (image_data_version in contents.json) was introduced, this is a way to tell WhatsApp whether your app has new content or not.

If you update your stickers, add new stickers to a pack, you should update this value.

If your app allows users to add/update/delete stickers from a pack, you should update the value after users have made changes.
