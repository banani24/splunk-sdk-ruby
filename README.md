# The Splunk Software Development Kit for Ruby (Deprecated)

#### Version 1.0.5

<blockquote>
<h3>Deprecation notice</h3>
<p>The Splunk SDK for Ruby is deprecated.  </p>
<p>What deprecation means:</p>
<ul>
<li>On June 1, 2017, the resources relating to the Splunk SDK for Ruby will be removed from dev.splunk.com and will only be available in the GitHub repository. </li>
<li>Apps that use the Splunk SDK for Ruby will continue to work as they do now. </li>
<li>Apps that use the Splunk SDK for Ruby will continue to be eligible for Splunk App Certification.</li>
<li>Splunk will no longer provide feature enhancements, engineering support, or customer support for the Splunk SDK for Ruby.</li></ul>
<p>Recommendation on new app development and app migration:</p>
<ul>
<li>Because Splunk is no longer investing in the Splunk SDK for Ruby, we recommend that any new app development be done using other approaches:<p>
<ul><li>Directly using our REST API in the language of their choice.</li>
<li>Using one of our supported SDKs: 
<p><ul><li>Python (<a href="https://github.com/splunk/splunk-sdk-python">GitHub</a> | <a href="http://dev.splunk.com/view/python-sdk/SP-CAAAEBB">dev.splunk.com</a>)</li>
<li>Java (<a href="https://github.com/splunk/splunk-sdk-java">GitHub</a> | <a href="http://dev.splunk.com/view/java-sdk/SP-CAAAECN">dev.splunk.com</a>)</li>
<li>JavaScript (<a href="https://github.com/splunk/splunk-sdk-javascript">GitHub</a> | <a href="http://dev.splunk.com/view/javascript-sdk/SP-CAAAECM">dev.splunk.com</a>)</li>
<li>C# (<a href="https://github.com/splunk/splunk-sdk-csharp-pcl">GitHub</a> | <a href="http://dev.splunk.com/view/csharp-sdk/SP-CAAAEPK">dev.splunk.com</a>)</li></ul></p></li></ul></p></li>
<li>For existing apps that use the Splunk SDK for Ruby, while not necessary, we request that developers begin the migration process away from the Splunk SDK for Ruby. We encourage developers to provide feedback to Splunk at <a href="mailto:devinfo@splunk.com">devinfo@splunk.com</a> if there are any issues with migration. </li></ul>
<p>Notice of removal:</p>
<ul><li>The Splunk SDK for Ruby will continue to be available on GitHub, should other developers want to clone or fork the project. <a href="https://github.com/splunk/splunk-sdk-ruby/raw/master/docs.pdf">Documentation</a> is located on GitHub as well.</li></ul>
</blockquote>

This Splunk Software Development Kit (SDK) for Ruby contains library code and 
examples designed to enable developers to build applications using Splunk.

Splunk is a search engine and analytic environment that uses a distributed
map-reduce architecture to efficiently index, search, and process large 
time-varying data sets.

The Splunk product is popular with system administrators for aggregation and
monitoring of IT machine data, security, compliance, and a wide variety of 
other scenarios that share a requirement to efficiently index, search, analyze,
and generate real-time notifications from large volumes of time series data.

The Splunk developer platform enables developers to take advantage of the 
same technology used by the Splunk product to build exciting new applications
that are enabled by Splunk's unique capabilities.

## Getting started with the Splunk SDK for Ruby

The Splunk SDK for Ruby contains code and some examples that show how to
programmatically interact with Splunk for a variety of scenarios, including
searching, saved searches, configuration, and many more. This SDK is still 
in progress and is missing features such as inputs. Stay tuned.


### Requirements

Here's what you need to get going with the Splunk SDK for Ruby.

#### Splunk

If you haven't already installed Splunk, download it 
[here](http://www.splunk.com/download). For more information about installing 
and running Splunk and system requirements, see 
[Installing & Running Splunk](http://dev.splunk.com/view/SP-CAAADRV).

#### Ruby

The Splunk SDK for Ruby has been tested with [Ruby 1.9.2 and Ruby 1.9.3](http://www.ruby-lang.org/). For best results, use one of those versions.

#### Splunk SDK for Ruby

Get the Splunk SDK for Ruby from [GitHub](https://www.github.com) and clone the
resources to your computer. Use the following command:

    git clone https://github.com/splunk/splunk-sdk-ruby.git    

You can also download the SDK as a ZIP file, or install it directly (see below). 


### Installing the Splunk SDK for Ruby

If you have cloned the Splunk SDK for Ruby from GitHub, you should first
install the latest version of `rake`. For example, open a command prompt and 
enter the following:

    gem install rake

Then you can install the Splunk SDK for Ruby by running the following
command from the root of the repository (**/splunk-sdk-ruby**):

    rake install

Or, install the Splunk SDK for Ruby directly from RubyGems,
without cloning the repository or downloading the ZIP file, by running:

    gem install splunk-sdk-ruby

If you are using the Splunk SDK for Ruby in an application, we highly
recommend that you use [bundler](http://gembundler.com/), which installs
the prerequisites when you deploy your application. Add the following 
line to your application's Gemfile to make bundler aware of the Splunk 
SDK for Ruby:

    gem 'splunk-sdk-ruby'

Then run the following command to install all of your application's
dependencies, including the Splunk SDK for Ruby:

    bundle

#### Examples

Examples are located in several locations within the Splunk SDK for Ruby:

* The **/splunk-sdk-ruby/examples/** directory
* Inline with the source code within the SDK
* In the documentation on the [Splunk Developer Portal](http://dev.splunk.com/view/ruby-sdk/SP-CAAAENQ).

#### Prepare for the unit tests

First, do not run the test suite against your production Splunk server! Install
another copy of Splunk and run the test suite against that.

Second, update your installations of both the [Rake](http://rake.rubyforge.org) 
build tool and the [Test::Unit](http://test-unit.rubyforge.org) unit 
test framework from RubyGems:

    gem install rake
    gem install test-unit

The test suite reads the host to connect to and credentials to use from a
**.splunkrc** file. To connect to Splunk, all of the SDK examples and unit
tests take command-line arguments that specify values for the host, port,
and login credentials for Splunk. For convenience during development, you
can store these arguments as key-value pairs in a text file named 
**.splunkrc**. Then, when you don't specify these arguments at the command
line, the SDK examples and unit tests use the values from the .splunkrc file.

**To set up a .splunkrc file**

1. Create a text file with the following format:

    <pre> # Splunk host (default: localhost)
    host=localhost
    # Splunk admin port (default: 8089)
    port=8089
    # Splunk username
    username=admin
    # Splunk password
    password=changeme
    # Access scheme (default: https)
    scheme=https</pre>

2. Save the file as .splunkrc in the current user's home directory.

**On Mac OS X**

Save the file as:

    ~/.splunkrc

**On Windows**

Save the file as:

    C:\Users\[currentusername]\.splunkrc

You might get errors in Windows when you try to name the file because 
".splunkrc" looks like a nameless file with an extension. You can use 
the command line to create this file; go to the 
**C:\Users\\[currentusername]\\** directory and enter the following command:

    Notepad.exe .splunkrc
    
Click **Yes**, then continue creating the file.

**Notes**

* Storing login credentials in the .splunkrc file is only for 
  convenience during development; this file isn't part of the 
  Splunk platform and shouldn't be used for storing user credentials
  for production. And, if you're at all concerned about the security 
  of your credentials, just enter them at the command line and don't 
  bother using the .splunkrc file.
* The format of the .splunkrc file has changed between releases. If 
  you are using a preview or beta version of the SDK, some of the 
  newer fields might not be recognized and you might see errors while
  running the examples. You can either update to the latest version
  of the SDK, or comment out the <tt>app</tt>, <tt>owner</tt>, and 
  <tt>version</tt> fields.

#### Run the unit tests

In the base directory where you installed the Splunk SDK for Ruby, run

    rake test

It should run many tests without error.

To generate code coverage of the test suite, first ensure you've installed
the latest version of [SimpleCov](http://rubygems.org/gems/simplecov): 

    gem install simplecov

To generate the code coverage, run:

    rake test COVERAGE=true

It will produce a directory called **coverage**. Open coverage/index.html to
see the coverage report.

**Note**: To protect your Splunk password, you may want to delete the .splunkrc 
file when you are done running the unit tests.

## Repository

<table>

<tr>
<tr>
<td><b>/examples</b></td>
<td>Examples demonstrating various SDK features</td>
</tr>

<tr>
<td><b>/lib</b></td>
<td>Source for the Splunk library modules</td>
</tr>

<tr>
<td><b>/test</b></td>
<td>Source for unit tests</td>
</tr>

</table>

### Changelog

The **CHANGELOG.md** file in the root of the repository contains a description
of changes for each version of the SDK. You can also find it online at
[https://github.com/splunk/splunk-sdk-ruby/blob/master/CHANGELOG.md](https://github.com/splunk/splunk-sdk-ruby/blob/master/CHANGELOG.md).

### Branches

The **master** branch always represents a stable and released version of the SDK.

## Documentation and resources

If you need to know more: 

* For all things developer with Splunk, your main resource is the [Splunk Developer Portal](http://dev.splunk.com).

* For conceptual and how-to documentation, see the [Overview of the Splunk SDK for Ruby](http://dev.splunk.com/view/SP-CAAAENQ).

* For API reference documentation, see the [Splunk SDK for Ruby Reference](http://docs.splunk.com/Documentation/RubySDK).

* For more about the Splunk REST API, see the [REST API Reference](http://docs.splunk.com/Documentation/Splunk/latest/RESTAPI).

* For more about about Splunk in general, see [Splunk>Docs](http://docs.splunk.com/Documentation/Splunk).

* For more about this SDK's repository, see our [GitHub Wiki](https://github.com/splunk/splunk-sdk-ruby/wiki/).

## Community

<table>

<tr>
<td><b>Email</b></td>
<td><a href="mailto:devinfo@splunk.com">devinfo@splunk.com</a></td>
</tr>

<tr>
<td><strong>Forum</strong></td>
<td><a href="https://groups.google.com/forum/#!forum/splunkdev">https://groups.google.com/forum/#!forum/splunkdev</a>
</tr>

<tr>
<td><b>Issues</b>
<td><a href="https://github.com/splunk/splunk-sdk-ruby/issues/">https://github.com/splunk/splunk-sdk-ruby/issues/</a></td>
</tr>

<tr>
<td><b>Answers</b>
<td><a href="http://splunk-base.splunk.com/tags/ruby/">http://splunk-base.splunk.com/tags/ruby/</a></td>
</tr>

<tr>
<td><b>Blog</b>
<td><a href="http://blogs.splunk.com/dev/">http://blogs.splunk.com/dev/</a></td>
</tr>

<tr>
<td><b>Twitter</b>
<td><a href="http://twitter.com/#!/splunkdev">@splunkdev</a></td>
</tr>

</table>

### How to contribute

If you would like to contribute to the SDK, go here for more information:

* [Splunk and open source](http://dev.splunk.com/view/opensource/SP-CAAAEDM)

* [Individual contributions](http://dev.splunk.com/goto/individualcontributions)

* [Company contributions](http://dev.splunk.com/view/companycontributions/SP-CAAAEDR)

### Support

You can find help through the broader community at <a href='http://splunk-base.splunk.com/answers/'>Splunk Answers</a> (use the <b>sdk</b> and <b>ruby</b> tags to identify your questions).

### Contact Us

You can reach the Dev Platform team at <a href="mailto:devinfo@splunk.com">
devinfo@splunk.com</a>.

## License

The Splunk Software Development Kit for Ruby is licensed under the Apache
License 2.0. Details can be found in the LICENSE file.
