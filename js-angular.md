Directives
----------


		AngularJS when bootstrapped, looks for all the directives built-in as well
		as custom ones, compiles them using $compile() method (which keeps track of
		all the directives associated with an element, sorts them by priority and
		produces their link function), and links with scope (created by ng-app,
		ng-controller, ng-include, etc) by registering listeners or setting up
		$watches resulted in 2 way data bindings between the scope and the element


Directive format:

		myModule.directive('directiveName', function (injectables) {
			return {
				restrict: 'ECMA',
				template: '<div></div>',
				templateUrl: 'directive.html',
				replace: false,
				priority: 0,  			// higher runs first
				terminal: false,    // stops further processing
				transclude: false,
				scope: false,
				require: false,
				controller: function($scope, $element, $attrs, $transclude, otherInjectables) { ... },
				compile: function compile(tElement, tAttrs, transclude) {
					return {
						pre: function preLink(scope, iElement, iAttrs, controller) { ... },
						post: function postLink(scope, iElement, iAttrs, controller) { ... }
					}
				},
				link: function postLink(scope, iElement, iAttrs) { ... }
			};
		});
				

### Compile

Do DOM manip.  Returns a link function.  No access to scope.
Sole purporse is performance - on an ng-repeat directive, don't want to do ... on each change.

### Link

2 way data-binding between scope and DOM.


### Template

Inline template picked up by templateUrl:

		<script type='text/ng-template' id='whoiam.html'></script>


### Controller

Data bound to `this` will be accessible to other directives that `require` this directive.

### Require

Lets you pull controller from another directive into compile/link functions.

		require: ['ngModel', 'directive2']
		require: '^ngModel'		// will look at parent els for controller 
		require: '?ngModel'   // will not raise error if not found



Example of require, directive with controller + link:

		<body ng-app="App" style='padding:30px;'>
			<div class="btn btn-success" power-switch>
				{{'Switched ' + state | uppercase}}

				<div lightbulb class='bulb' ng-class="bulb"></div>
			</div>

		<script>
			var App = angular.module('App', []);

			App.directive('powerSwitch', function() {
					return {
							restrict: 'A',
							controller: function($scope, $element, $attrs) {
									$scope.state = 'on';
									
									$scope.toggle = function() {
											$scope.$apply(function() {
													$scope.state = ($scope.state === 'on' ? 'off' : 'on');
											});
									};
									
									this.getState = function() {
											return $scope.state;
									};
							},
							link: function(scope, element, attrs) {
									element.bind('click', function() {
											scope.toggle();
									});
									
									scope.$watch('state', function(newVal, oldVal) {
											if (newVal === 'off') {
													element.addClass('disabled');
											} else {
													element.removeClass('disabled');
											}
									});
							}  
					};
			});

			App.directive('lightbulb', function() {
					return {
							restrict: 'A',
							require: '^powerSwitch',
							link: function(scope, element, attrs, controller) {
									scope.$watch(function() {
											scope.bulb = controller.getState();
									});
							}
					};
			});
		</script>

[1]: http://amitgharat.wordpress.com/2013/06/08/the-hitchhikers-guide-to-the-directive/

Animate
------


Angular UI Router
---------
https://github.com/angular-ui/ui-router/wiki/Frequently-Asked-Questions#how-to-open-a-dialogmodal-at-a-certain-state
Use route to open a dialog




Check
-----
https://leanpub.com/recipes-with-angular-js
	book preview
