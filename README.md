TestHub [![Build Status](https://travis-ci.org/AppBlade/TestHub.png?branch=master)](https://travis-ci.org/AppBlade/TestHub) [![Code Climate](https://codeclimate.com/repos/51dcf9c089af7e351300b93b/badges/96be53d56627cf87fef4/gpa.png)](https://codeclimate.com/repos/51dcf9c089af7e351300b93b/feed) [![Dependency Status](https://gemnasium.com/AppBlade/TestHub.png)](https://gemnasium.com/AppBlade/TestHub)
=======

TestHub is a tool built on top of [GitHub's releases feature](https://github.com/blog/1547-release-your-software) to enable over-the-air deployment of iPhone applications and automatically detect if the app can be installed on the phone.

**TestHub isn't ready for prime-time yet, I'm banking on updates to the GitHub API regarding Releases and am faking data in places.—[James Daniels](https://github.com/jamesdaniels)**

What makes TestHub special?
---------------------------
It's true that there are a lot of tools in regards to internal app distribution, beta testing, and Mobile App Management. TestHub is built on our experience of making [AppBlade](https://appblade.com) and we've decided to enrich the community by leading an open-source project in our space.

1. First open-source SCEP-based app distribution server. (That we know of)
1. Maintained by a team who deploys hundreds of thousands of IPAs over-the-air
1. Leverages your existing GitHub toolchain
1. Utilizes SCEP and client-side certificates in device detection

WTF is an SCEP and what are you doing to my phone?
--------------------------------------------------
[AppBlade](https://appblade.com) switched to using SCEP, Simple Certificate Enrollment Protocol, over other methods of "cookie-ing" a device with the advent of iCloud backups. We've decided to open-source that piece of our service.

Safari's sessions/cookies are saved in backups which, when restored to a new device, will cause servers to believe the "new" device is the old one. This will cause a great many difficulties in delivering an application, particularly an ad-hoc application, to a user's device. Standard protocol is to ask a user to reset their Safari caches if anything is acting up, which is gross. TestHub doesn't have this problem.

SCEP is an automated way of TestHub to issue a certificate to the device, where we do not have the private keys; think automated certificate requests. These certificates are tied to the specific hardware of the device that paired with TestHub, Mobile Safari will then use them when connecting to TestHub.

Why would I use this over other, plist-based solutions?
----------------------------------
1. TestHub exchanges information with the device to learn it's UDID automatically.
1. TestHub looks at the capabilities of the device and inspects the IPA to ensure that they are compatible before you (or your testers) attempt to install. Apple is kind enough to only provide a single error message; "The application failed to install", to explain a range of issues. Try explaining to a non-technical beta tester how to give you the relevant information from their device logs!
1. If the IPA can not be installed on the device TestHub will allow the user to open an Issue, which will contain all the relevant information to diagnose why their device can't install the build.
1. Enterprise-signed applications (those not subject to Apple's ad-hoc limitations) will be protected via GitHub's permission model, a user will need to be a contributor to have access to these builds. This is one measure to help ensure compliance with Apple's terms.
1. Those releases marked as pre-release will also be protected via GitHub's permission model, allowing you have internal builds that your testers will not have access to.

Getting up and running with your own TestHub
--------------------------------------------
Instructions coming soon...
