winci-server
============

[WinCI] Provides readymade setup of Jenkins CI under Windows together with scripts automating integration with continuous deployment pipeline popular in Agile world.

Introduction
============

WinCI-server is ingredient of WinCI project.
The purpose of WinCI project is to simplify implementation of the full continuous deployment pipeline the Agile way with Jenkins/Hudson continuous integration server under Windows.

WinCI-server lets Windows developers get quickly up and running with continuous deployment pipeline and 
continuous integration by incorporating convention-over-configuration paradigm, so that the novice is first presented with 
working setup with the click of a button and after he see it working and have overall empirical knowledge under his belt, 
only then is he introduced to some configuration options.

WinCI-server uses Jenkins.rb gem to automate installation and interaction with Jenkins CI and also ruby-git gem to automate CI provisioning. It provides functionality necessary to setup Jenkins CI and enabling to create installation bundle used in provisioning process.

WinCI-server is intended to be used in conjunction with WinCI, which is another gem containing functionality
essential for development environment, so that contains all the scripts that can be used by developer on his development
machine as opposed to WinCI-server that is intended to be used on the server.

Compatibility
=============

Successfully tested on the following mingw versions from RubyInstaller.org :

	ruby 1.8.7 (2011-02-18 patchlevel 334) [i386-mingw32]
	
Install
=======

First download WinCI-server from: http://rubyforge.org/projects/ksob/

And extract it to directory with no spaces in name.

Then you will need to supply yourself with the following software:

  * Ruby 1.8.X   ( can be obtained here: http://rubyinstaller.org/downloads/ )
  * DevKit		 ( can be obtained here: http://rubyinstaller.org/downloads/ )
  * PortableGit  ( can be obtained here: http://code.google.com/p/msysgit/ )
  
  Note: WinCI-server could also work with other editions or versions of the software listed above although it has not been tested.

Next go to WinCI-server main directory.

Then unpack all three of them into the following directories accordingly:
	
  * fixtures/Ruby
  * fixtures/DevKit
  * fixtures/PortableGit
	
After that go again to WinCI-server main directory and run:

    $ install.bat

Then follow instructions in the CMD window, you will be prompted to press Enter several times.

Usage
=====

To run local Jenkins server:

	$ start_jenkins.bat
	
 Note: by default it opens at http://localhost:3010, to adjust you will need to modify restart_jenkins.rake

To create jobs on the Jenkins server use winci gem. 
 Note: winci can be used from development machine to control Jenkins server remotely.
	
To terminate Jenkins server:

	$ shutdown_jenkins.bat
	
To prepare installation bundle used in provisioning process:
	
	* First edit .\fixtures\updater\_config.yaml to include your repository
	* Then run: 
		$ create_installation_pack.bat
	
 Note: the installation pack is meant to be supplied to the target environment only once,
       after that the end-user of that environment is assumed to use updater.bat to replicate 
	   fresh project's files/configuration from the server
	   
Upgrade	dependencies  
====================
All gems used in installation process are stored in ./vendor/cache so you will
need to refresh this directory with recent gems if you would like to upgrade gem dependencies.
All plugins used while starting jenkins for the first time are stored in ./fixtures/jenkins so you will
need to refresh this directory with recent plugins if you would like to upgrade jenkins plugins.

License
=======

(The MIT License)

Copyright (c) 2011 Kamil Sobieraj, ksob@dslowl.com

Permission is hereby granted, free of charge, to any person obtaining
a copy of this software and associated documentation files (the
'Software'), to deal in the Software without restriction, including
without limitation the rights to use, copy, modify, merge, publish,
distribute, sublicense, and/or sell copies of the Software, and to
permit persons to whom the Software is furnished to do so, subject to
the following conditions:

The above copyright notice and this permission notice shall be
included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED 'AS IS', WITHOUT WARRANTY OF ANY KIND,
EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF
MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT.
IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY
CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT,
TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE
SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.