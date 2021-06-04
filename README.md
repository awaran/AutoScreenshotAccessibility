# AutoScreenshotAccessibility

# Error Help
If you get something like

"fastlane finished with errors"
[!] Please update your Snapshot Helper file using `fastlane snapshot update`

run "fastlane snapshot update" in terminal.  This will give you a new "SnapshotHelper.swift" file with the proper version info at the bottom to match with your current version of fastlane
After you do that, you will need to compare the original "SnapshotHelper.swift" file with the new one and migrate the modifications.  The only modification that is in the original "SnapshotHelper.swift" file is adding the launch args to the end of a screenshot name.  This is so we don't override images for different accessability setting.  (I.E medium, large, extra large text)

# Install

## Setup your simulators
The simulators that fastlane use are the ones from xcode.  They start with the same state you left them on.

## Create Unit test

Open X-Code

File ▸ New ▸ Target. Within the iOS tab’s Test section, select iOS UI Testing Bundle then click Next

Put [this file](https://github.com/awaran/AutoScreenshotAccessibility/blob/main/SnapshotHelper.swift) in your unit test group.  hit “copy items if needed” and “create groups” then hit finish

Make your screenshot unit tests

When you create an app like so
```swift
var app = XCUIApplication()
```

setup the snapshot using setupSnapshot(app) before you launch
```swift
app = XCUIApplication()
setupSnapshot(app)
app.launch()
```


Whenever you want to create a snapshot use snapshot(“unique id in this location 1”).  In the following code, the Unique id is "11UserEntries".  Please replace "11UserEntries" with your own unique Identifier.  
```swift
snapshot("11UserEntries")
```
<sub><sup>*Details: This id will be used to create the filename of the photo and possibly modify the name of the google slide it creates.  The photo filename is device + language + uniqueId + last word in launch arg(it's for different accessibility screenshoting)*</sup></sub>

**ProTip: record your test, and put in sleep(10) where you want your screenshots to go.  Run your unit test normally.  When you see the abnormally long wait, that will be where your screenshot will happen**


## Install Fastlane

Type this into your terminal, it will install ruby, xcode command line and gems
```
brew update && brew install ruby
xcode-select --install
sudo gem install fastlane -NV
```


Go into project where Xcode project (xcodeproj file) lives and type this into terminal.  *This will start the process to create fastlane folders*
```
fastlane init
```
Type in 1 for automate screenshots

Follow instructions but skip uploading screens to App Store connect for the last option

After files are created, it doesn't exit out.  you can control c or close terminal

## Configure screenshot / fastlane / snapshot creation

In snapfile - make modifications you want, uncomment devices, and languages you want to use, uncomment output directory and clear previous screenshots then put this at the bottom
'''
launch_arguments([
  "-UIPreferredContentSizeCategoryName UICTContentSizeCategoryAccessibilityM",
  "-UIPreferredContentSizeCategoryName UICTContentSizeCategoryAccessibilityL"
  "-UIPreferredContentSizeCategoryName UICTContentSizeCategoryAccessibilityXL"
  "-UIPreferredContentSizeCategoryName UICTContentSizeCategoryAccessibilityXXL"
  "-UIPreferredContentSizeCategoryName UICTContentSizeCategoryAccessibilityXXXL"
])
'''

or use [Suggested Snapfile](https://github.com/awaran/AutoScreenshotAccessibility/blob/main/Snapfile)


**ProTip: check to see if it works on one device / language to see if you got it right before running.  Run when away from office, will take hours to finish if you have a lot of devices languages and launch arguments**

## Run Snapshot creation
Type this into your terminal when ready to get snapshots
```
bundle exec fastlane screenshots
```

//TODO finish python script for making google slides and put in instructions / script here


### Internal References:
installing fastlane
https://moma.corp.google.com/search?q=install%20fastlane, distribute iOS app -> install fastlane
