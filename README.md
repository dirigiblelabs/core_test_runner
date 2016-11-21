# core_testui
Generic Service for running ScriptingServices tests and displaying results in a dashboard UI

Sample use:

<pre> var svc_reporter = require("test/qunit/reporters/qunit_svc_reporter");
		require("test/test_runner_svc").service({
			"execute": function(){
					_QUnit.load();
				},
			"serviceReporter": svc_reporter 
		});	</pre>

svc_reporter is an object with the function forMedia(mediaType).
The service will resolve the requested media type and provide it in a simplified form as argument to this function ("json" or "xml").
The reporter can then attach to the test framework for which it was designed and provision its report in the request format. 
