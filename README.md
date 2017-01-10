# core_testui
Generic Service for running ScriptingServices tests and displaying results in a dashboard UI. It implements core dispatching logic based on request media type to an appropriate test reporter and test env initialization. Concrete test framework running services, such as qunit test runner or jamsine test runner, will use it internally. 

Sample use (intended for test framework test runner providers) :

<pre> var svc_reporter = require("test/qunit/reporters/qunit_svc_reporter");
		require("test/test_runner_svc").service({
			"execute": function(){
					_QUnit.load();
				},
			"serviceReporter": svc_reporter 
		});	</pre>

<code>svc_reporter</code> is an object that has function <code>forMedia(mediaType)</code>.

The <code>test_runner_svc</code> sevice will resolve the request media type and provide it in a simplified form as argument to this function ("json" or "xml").
The reporter can then attach to the test framework for which it was designed and provision its report in the request format. 
