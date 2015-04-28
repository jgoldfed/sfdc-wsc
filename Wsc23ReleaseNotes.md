#wsc-23 release notes

# Introduction #

The 23 release of this wsc tool is mainly a maintenance release. Note that release numbers does not follow sfdc api versions, so wsc-23 can be used with any sfdc version at least up to 27.

Looking for a maven build, see Victor Itkins sfdc-wsc-maven fork: http://code.google.com/p/sfdc-wsc-maven/

Alternatively mvncentral (maintainers currently unknown) at: http://mvnrepository.com/artifact/com.force.api/force-wsc

_**Please note** the code at mvncentral now effectively is a fork of this tool._

# Details #

**Issues fixed**:

  * [Issue 39](https://code.google.com/p/sfdc-wsc/issues/detail?id=39): Main-Class attribute added to Manifest. Tool can now be run with: java -jar wsc-23.jar…
  * [Issue 49](https://code.google.com/p/sfdc-wsc/issues/detail?id=49): Version # now part of wsc\_license.html.
  * [Issue 54](https://code.google.com/p/sfdc-wsc/issues/detail?id=54): Ant-build changed to ensure non-java resources are not duplicated in the jar.
  * [Issue 64](https://code.google.com/p/sfdc-wsc/issues/detail?id=64): Transport has been modified to rely on the HTTP response code.
  * [Issue 66](https://code.google.com/p/sfdc-wsc/issues/detail?id=66): Removed (1.6-) compiler warnings.
  * [Issue 67](https://code.google.com/p/sfdc-wsc/issues/detail?id=67): SoapConnection throws RequestTimedOutException when requests are timed out.
  * [Issue 69](https://code.google.com/p/sfdc-wsc/issues/detail?id=69): Merge from 27.0.0 included the InvalidEntity enum value.

**Enhancements**:

  * General: Code from mvnrepository release 27.0.0 has been merged in.
  * General: (post-27.0.0 refactor) Removed code from ConnectorConfig that did not belong there. Simplified Transport interface etc.
  * General: XML tracing with “pretty print” has been reworked.
  * General: Removed outdated package.html from misc. packages.
  * Build: Manifest (in wsc-xx.jar) now contains version-# and build time.
  * Build: Now also generates wsc-xx-min.jar containing class files neede at runtime only.
  * SoapConnection: Removed the SessionTimedOutException “control flow exception”.
  * VersionInfo: Build-filter to include the version-# and time.
  * wsdlc: The “wsdl2java” tool now uses the 1.6 JavaCompiler. Extra effort has been put in place to find and load it from tools.jar…
  * wsdlc: Temp directory only deleted if not specified on cmd-line or the del-temp-dir property specifically set.
  * wsdlc: Allowed creation of .zip files as well.
  * wsdlc: Generated manifest now contains name of developer and wsc-version.
  * wsdlc: Compiles for “default target” unless target compileTarget property is specifically set.

Happy downloading

Jesper Udby, Feb 8, 2013

See my blog for news and updates regarding this tool and Salesforce integration: http://blog.udby.com/archives/tag/wsc