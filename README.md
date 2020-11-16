# AutoScreenshotAccessibility


Open X-Code
File ▸ New ▸ Target. Within the iOS tab’s Test section, select iOS UI Testing Bundle then click Next
Put this file in your unit test group.  hit “copy items if needed” and “create groups” then hit finish
Put this in your init
Make your screenshot unit tests
  Create a global app //var app = XCUIApplication()
  When you create the app, setup the snapshot using setupSnapshot(app) before you launch
    app = XCUIApplication()
    setupSnapshot(app)
    app.launch()

	Whenever you want to create a snapshot use snapshot(“unique id in this location 1”)
		snapshot("11UserEntries")
    This id will be used to create the filename of the photo and possibly modify the name of the google slide it creates.

    ProTip: record your test, and put in sleep(10) where you want your screenshots to go.  Run your unit test normally.  When you see the abnormally long wait, that will be where your screenshot will happen



Install fastlane: 
brew update && brew install ruby
xcode-select --install
sudo gem install fastlane -NV

Steps:
Go into project where Xcode project (xcodeproj file) lives
Type in “fastlane init”
Type in 1 for automate screenshots
   Follow instructions (enter, enter, 1 - find your unit testing scheme.  Will prob be the first one, n - skip uploading screens to App Store connect)

Installing dependencies is a bit buggy, had to control c it after 10 mins but it finished

In snapfile - make modifications you want, uncomment devices, and languages you want to use, uncomment output directory and clear previous screenshots then put this at the bottom
launch_arguments([
  "-UIPreferredContentSizeCategoryName UICTContentSizeCategoryAccessibilityM",
  "-UIPreferredContentSizeCategoryName UICTContentSizeCategoryAccessibilityL"
  "-UIPreferredContentSizeCategoryName UICTContentSizeCategoryAccessibilityXL"
  "-UIPreferredContentSizeCategoryName UICTContentSizeCategoryAccessibilityXXL"
  "-UIPreferredContentSizeCategoryName UICTContentSizeCategoryAccessibilityXXXL"
])

Suggested snaffle is here


ProTip: check to see if it works on one device / language to see if you got it right before running.  Run when away from office, will take hours to finish
Type this into your terminal
bundle exec fastlane screenshot

//TODO finish python script for making google slides and put in instructions / script here



References:
installing fastlane
https://moma.corp.google.com/search?q=install%20fastlane, distribute iOS app -> install fastlane
