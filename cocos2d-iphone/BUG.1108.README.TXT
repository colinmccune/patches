# Project
cocos2d-iphone

# Issue
1108 - CDAudioManager is still the delegate of AVAudioSession after CDAudioManager end/dealloc.

# Issue Summary

What steps will reproduce the problem?
- 1. Startup Cocos2d and CDAudioManager. 
- 2. Shutdown CDAudioManager ([CDAudioManager end];) or [SimpleAudioEngine end].
- 3. Play video/audio via an AVPlayer.
- 4. When video stops playing an audio interruption will occur and AVSessionAudio will attempt to send a message to its delegate which is still the CDAudioManager and seeing as it is no longer around (dealloced in step 2) the app will crash.
- 5. Yes my class playing the video via AVPlayer SHOULD have changed AVSessionAudio delegate to itself (my bad) however I still think it makes sense for CDAudioManager to unset this when it gets dealloced for safety sake.
- 6. See patch bellow.

What is the expected output? What do you see instead?
- Not to crash.

What cocos2d version / SVN revision are you using ?
- 0.95.5

What iPhoneSDK are you using ?
- 4.2.2

Debug or Release ?
- Debug/Release

Does this happens on device ? or on the simulator ? or on both ?
- Device

Please provide any additional information below.

- I've attached a patch fixing this issue. In the CDAudioManager's dealloc it should set the AVAudioSession delegate to nil to prevent AVAudioSession from potentially sending a message to destroyed CDAudioManager's.

# Patch
patch.patch

# References
http://code.google.com/p/cocos2d-iphone/issues/detail?id=1108