#YepnopeSilverStripe#

A module to allow loading of Javascript & CSS using the conditional loader [http://yepnopejs.com]yepnopejs

By:

Loz Calver & Colin Richardson - [http://www.bigfork.co.uk/]Bigfork Ltd


##Installation:##

Simply clone or download this repository and put it in a folder called 'yepnopesilverstripe' in your SilverStripe installation folder, then run `dev/build`.

##Examples:##

The simplest way to add a file, whether it's Javascript or CSS, is to use the add_file() function in your Page_Controller:

	class Page_Controller extends ContentController {
	
		public function init() {
			parent::init();
			
			Yepnope::add_file('themes/yourtheme/javascript/yourjavascript.js');
			Yepnope::add_file('themes/yourtheme/css/extrastyles.css');
		}
	
	}
	
You can also remove a file from certain page types by using the clear() function. For this example, let's assume that you want to load the Javascript file from the above example on every page _except_ the home page:

	class HomePage_Controller extends Page_Controller {
	
		public function init() {
			parent::init();
		
			Yepnope::clear('themes/yourtheme/javascript/yourjavascript.js');
		}
	
	}

If you're using modernizr and don't need to include yepnope.js, you can set your custom script with the following:

	class Page_Controller extends ContentController {
	
		public function init() {
			parent::init();
			
			Yepnope::set_modernizr('themes/yourtheme/javascript/modernizr.min.js');
		}
	
	}


##TODO##

* Add functionality for yepnope's tests
* Add support for callbacks on all files, and individual files
* Add support for prefixes (!css, !timeout etc)
* General cleaning, tidying and refactoring of code
* More testing