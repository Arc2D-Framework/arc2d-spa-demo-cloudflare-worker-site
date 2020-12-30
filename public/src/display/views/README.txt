VIEWS IN SPA SETUP
------------------------------------------------------------
In an SPA setup (See: screens/SpaDemo), the screen is asssembled with
1 default View (see: views/). Add navigation to other views
using links with namespace to the view:

<a href=#display.views.Home">Home Page</a>
<a href=#display.views.About">About Us</a>
<a href=#display.views.Contact">Contact Us</a>


Views are regular, but larger WebComponents that
are screen-sized. Different Views are navigated to,
using links above, without refreshing the Screen.


DEMO:
--------------------------------------------------------
See webpage, "spa-demo.html" at project root. It's namespace is
a screen located at folder: "src/display/screens/SpaDemo"

SpaDemo is a screen with this template:

<template>
    <div>
        <nav class="nav">
			<div class="container">
				<div class="logo">
					<a href="#display.views.Home"></a>
				</div>
				<div id="mainListDiv" class="main_list">
					<ul class="navlinks">
                        <li><a href="#display.views.Home">Home</a></li>
						<li><a href="#display.views.About">About</a></li>
						<li><a href="#display.views.Contact">Contact</a></li>
					</ul>
				</div>
				<span class="navTrigger">
					<i></i>
					<i></i>
					<i></i>
				</span>
			</div>
		</nav>
		<slot name="view-port">
            <home-page></home-page>
        </slot>
    </div>
</template>


a <slot> is used such as <slot name="view-port"> for a default view port where
other views are loaded into.


View port has a starting default view, <home-page>:
    <slot name="view-port">
        <home-page></home-page>
    </slot>


In Arc2D, we use normal #hash links to load new views, where the #hash
is the namespace to any component:
    <a href="#display.views.Contact">Contact Page</a>


<home-page> view is imported in SpaDemo screen class:
    
    import 'display.components.Splash';
    import 'display.views.Home';

    namespace `display.screens` (
        class SpaDemo extends Application {
            constructor(element){
                super(element);
            }

            async onConnected() {
                await super.onConnected();
            }
        }
    );