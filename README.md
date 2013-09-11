Metro Tester Windows 8 App
==========================

Metro Tester is a native WinJS app that is meant to be run in Windows 8. We use it within the YUI team to run YUI unit tests in Windows 8, specifically in the WinJS environment. 

It does this in the following manner:

- Cloning a version of yui3 in the js/ directory
- Iterating through the `yui3/` directory and creating an array of all unit test `.html` files
- Looping through all unit test files, using `WinJS.Navigation.navigate()` to move from file to file.
- Modifying YUI Test (`test.js`) to listen to test events and storing results for each test in Local Storage.
- Reading from local storage once all unit test files have been read.

We don't use iframes for testing because [there are some differences](http://msdn.microsoft.com/en-us/library/windows/apps/hh465373.aspx) in what's allowed in the WinJS runtime vs. a web runtime.

Setting up
----------

To save on the repo size and to keep the repo up-to-date, yui3 is not part of this repo. So if you just clone this repo and try to build it, it won't work.
That's normal. Here's what you have to do:

* Clone the repo.
* Navigate in to the js/ folder.
* Delete any `yui3/` directory. Clone yui3/ from the [YUI3 repo](http://github.com/yui/yui3/). That will create a new yui3/ directory. 
* Build from Visual Studio. The app should launch and show a list of all modules within YUI. You can click on a module to run its unit tests.


Help! I'm still having issues
-----------------------------

If you still get errors saying `YUI() is undefined`, it probably means you have YUI inside the directory, but you still need to include it in your project in Visual Studio.

To do this, go into the VS Solution Explorer, and click the little icon on the top that says "Show All Files". 
You should now see the yui3/ directory inside the js/ folder. Folders that are in the directory but not part of the project show up with a dotted icon. Your yui3/ directory may have a dotted icon.

* To include it in your project, expand the folder inside the Solution Explorer and right-click on the build/ directory. 
* Click "Include in Project". This will take a minute or two.
* Next, do the same with the src/ directory. 
* Try re-building within Visual Studio. Restart Visual Studio to be safe, because sometimes it doesn't refresh the project directory immediately.


Still not working? Let me know on Twitter (@tilomitra) or add an issue to this project. 
