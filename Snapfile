# Uncomment the lines below you want to change by removing the # in the beginning

# A list of devices you want to take the screenshots from
 devices([
   "iPhone 12 Pro",
   "iPhone 11 Pro",
   "iPhone 8",
#   "iPhone 8 Plus",
   "iPhone SE (2nd generation)",
#   "iPhone X",
#   "iPad Pro (12.9-inch)",
#   "iPad Pro (9.7-inch)",
#   "Apple TV 1080p"
 ])

 languages([
   "en-US",
   "es-US",
#   "de-DE",
#   "it-IT",
#   ["pt", "pt_BR"] # Portuguese with Brazilian locale
 ])


xcargs "-only-testing:ScreenshotTest"
launch_arguments([
  "-UIPreferredContentSizeCategoryName UICTContentSizeCategoryAccessibilityM",
  "-UIPreferredContentSizeCategoryName UICTContentSizeCategoryAccessibilityL",
  "-UIPreferredContentSizeCategoryName UICTContentSizeCategoryAccessibilityXXL",
  "-UIPreferredContentSizeCategoryName UICTContentSizeCategoryAccessibilityXXXL"
])

# The name of the scheme which contains the UI Tests
# scheme("SchemeName")

# Where should the resulting screenshots be stored?
# output_directory("./screenshots")

# remove the '#' to clear all previously generated screenshots before creating new ones
 clear_previous_screenshots(true)

# Remove the '#' to set the status bar to 9:41 AM, and show full battery and reception. See also override_status_bar_arguments for custom options.
# override_status_bar(true)

# Arguments to pass to the app on launch. See https://docs.fastlane.tools/actions/snapshot/#launch-arguments
# launch_arguments(["-favColor red"])

# For more information about all available options run
# fastlane action snapshot
