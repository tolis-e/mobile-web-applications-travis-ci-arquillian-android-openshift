# Kitchensink HTML5 Mobile Functional Test
This project contains the functional tests for the [Kitchensink HTML5 Mobile Demo](https://github.com/jboss-jdf/jboss-as-quickstart/tree/master/kitchensink-html5-mobile) project on Android OS. The purpose of the project is to demonstrate how to automate the testing of a mobile web application which is deployed on [OpenShift](https://www.openshift.com/), on Android OS using [Arquillian](http://arquillian.org/) testing platform and [Travis CI](https://travis-ci.org).

The [Arquillian](http://arquillian.org/) testing platform is used to enable the testing automation. Arquillian integrates transparently with the testing framework which is JUnit in this case.

[![Build Status](https://travis-ci.org/tolis-e/mobile-web-applications-travis-ci-arquillian-android-openshift.png?branch=master)](https://travis-ci.org/tolis-e/mobile-web-applications-travis-ci-arquillian-android-openshift)

## How it works - Important Notes
The functional test used to test our mobile web application is using the [Arquillian](http://arquillian.org/) testing platform. The whole concept is based on a remote Web Driver approach. Each WebDriver command makes a RESTful HTTP request to an Android HTTP server using JSON. The remote server delegates the request to Android WebDriver and returns a response. The Android Server APK path is configured inside the [Arquillian XML](https://github.com/tolis-e/mobile-web-applications-travis-ci-arquillian-android-openshift/blob/master/src/test/resources/arquillian.xml) configuration file. 

The configuration resides in the [Arquillian XML](https://github.com/tolis-e/mobile-web-applications-travis-ci-arquillian-android-openshift/blob/master/src/test/resources/arquillian.xml) configuration file.

[Arquillian XML](https://github.com/tolis-e/mobile-web-applications-travis-ci-arquillian-android-openshift/blob/master/src/test/resources/arquillian.xml) is configured to recognize the Android Emulator using some variables which are placed into the build environment through the [Travis CI YML](https://github.com/tolis-e/mobile-web-applications-travis-ci-arquillian-android-openshift/blob/master/.travis.yml) file.

The SERIAL_ID, API_LEVEL, APK_PATH variables are propagated to Arquillian and the corresponding configuration resides inside the [Arquillian XML](https://github.com/tolis-e/mobile-web-applications-travis-ci-arquillian-android-openshift/blob/master/src/test/resources/arquillian.xml) configuration file.

The mobile web application is already deployed on [OpenShift](https://www.openshift.com/) and can be found [here](http://kitchensinkhtml5-aemmanou.rhcloud.com/). 

## Development approach/methodologies
The development approach is driven from the desire to decouple the testing algorithmic steps / scenarios from the implementation which is tied to a specific DOM structure. For that reason the Page Objects and Page Fragments patterns are used. The Page Objects pattern is used to encapsulate the tested page's structure into one class which contains all the page's parts together with all methods which you will find useful while testing it. The Page Fragments pattern encapsulates parts of the tested page into reusable pieces across all your tests.

## Functional Test Execution
The purpose of the project is to depict how to automate the testing of mobile web applications deployed on [OpenShift](https://www.openshift.com/), on Android OS using [Arquillian](http://arquillian.org/) testing platform and [Travis CI](https://travis-ci.org). However, it is feasible to execute the functional test as a standalone test (without using Travis CI) after performing some modifications. More specifically, in a such case you have to configure the [Arquillian XML](https://github.com/tolis-e/mobile-web-applications-travis-ci-arquillian-android-openshift/blob/master/src/test/resources/arquillian.xml) accordingly so that an Android Emulator starts automatically (avdName, apiLevel, abi properties).

The execution of the functional test as a standalone test is done through maven:

    mvn test    

## Documentation

* [Arquillian Guides](http://arquillian.org/guides/)
