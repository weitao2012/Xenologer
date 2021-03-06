## Xenologer: repackaging Google Glass XE5 APKs to run on other devices

Google Glass's build process is fairly conservative - they don't use hidden APIs often, and when they do, they use reflection. 
Thus, it is relatively easy to repackage the Glass APKs for other devices.

### Modifications to the base APK

The use-library element in AndroidManifest is removed, as it refers to unused code.

com/google/glass/hidden/HiddenViewConfiguration.smali is patched to always return 0xffff instead of calling the nonexistent View.getDeviceTapTimeout

An instructional video (don_doff_background.mov, 8MB) is removed to save space. 

All native libraries required are shipped with the APK, as are all the Glass fonts.

For the camera, instead of calling Camera.open() to get the rear facing camera, Camera.open(0) is called to get the first camera,
 as the Nexus 7 doesn't have a rear camera.

### Install

Download the APK:

Home: http://zhuowei.github.io/Xenologer/glasshome-modded.apk

Camera: http://zhuowei.github.io/Xenologer/glasscamera-modded.apk

Maps: http://zhuowei.github.io/Xenologer/glassmaps-modded.apk

Install just like any other boring APK. None of the Google Glass apps need system privilages.
I do not recommend installing these APKs as system APKs, as the Glass apps will attempt to reboot the phone after a force close.

### Glass apps that won't be converted

GlassSound.apk: installs and runs without modification. Get a copy from any XE5 system dump. Not essential for Glass; Glass will just run muted without it.

GlassPhotosphere.apk: As stated by http://www.studio8apps.com/running-google-glass-photo-sphere-viewer-on-android-phone/ , runs (for the easter egg) without modification.
Again, any dumped copy from a XE5 should run fine. Not essential to Glass.

### Credits/License

While I don't have permission from the Glass team to post these, Google Glass is a device for explorers, 
thus, I believe it agrees with the spirit of discovery to post these APKs.

The APK was pulled from Android Police's dump at 
http://www.androidpolice.com/2013/05/08/download-google-glass-xe4-and-xe5-system-dumps-please-do-something-cool-with-these/
