# Ultimate Frisbee App - Melvin
*This is the individual readme of Melvin Reijnoudt. In this document you can see my contributions to this project on a weekly basis. You can also see used techniques from each course of the minor Everything Web. For an in-depth overview of the contributions by Fons and Senny, you can go to their personal readme's:*

- [Go to the individual README of contributor Fons Hettema](https://github.com/strexx/Ultimate-Frisbee-App/blob/master/README_fons.md)
- [Go to the individual README of contributor Senny Kalidien](https://github.com/sennykalidien/Ultimate-Frisbee-App)

##Tasks per week

![Trello-board](readme/screenshots/trello.png)

Things I've done to contribute to this project can be found at https://github.com/strexx/Ultimate-Frisbee-App/commits?author=melvinr

Aside from these commits I also contributed to a lot of commits done by Fons and Senny.

Below you can find a summary of the tasks I performed on a weekly basis, as well as a list of course related features I implemented.

###Week 1
- Briefing with the client.
- Think about what the application will need, what does the user want?
- Create a sitemap.
- Create wireframes per page.
- Join wireframes, take the best parts and create a new one from it.
- Create first sketches and iterate.
- Create a first design for the application.
- Created debriefing.

###Week 2
- Finish the first design.
- Recreated the design in HTML, CSS and Node.
- Find and implement google fonts.
- Research and testing at WindMill Tournament.
- Research for libraries and packages.
- Collaborated to make API calls and fetch data.
- Separated files into modules.
- Present first demo to Christian Schaffner.

###Week 3
- Created MoSCoW feature list.
- Progress meeting with teachers.
- Add feature list to Trello.
- Off-screen menu, along with transition and functionality.
- Research for mongoDB and help setup the database.
- Save matches to the database.

###Week 4
- Take out unnecessary libraries
- Help setting up server-side rendering
- Tab-toggle switch for server-side rendering instead of client-side
- Help setup database synchronization on remote server.
- Add feedback element when match has finished.
- Added LoadCSS.
- Setup and generated criticalcss using gulp.
- Created and implemented Service Worker.
- Redesign off-screen menu. Changed design pattern.
- Redesigned application.
- Implemented splash screen, along with logic (using local storage).
- Fixed realtime functionality.
- User testing.

###Week 5
- Made design and menu in particular responsive.
- Added fallback for flexbox using modernizr.
- Added logic for showing feedback after submitting as scorekeeper.
- Update one match from API, using mongoDB.
- Created matches on leaguevine for testing.
- Created readme.

###Week 6
- Added dropdown, including transition and design.
- Added favorites page and functionality.
- Added animation to favorites button.
- Helped create first draft of score update feedback.
- Show and hide menu when page loads, added button to get it back in view.

###Week 7
- Fixed Firefox layout bugs.
- Edited dropdown functionality: when opening a dropdown, close other dropdown.
- Edited readme.


###Weekly tasks
- Loggin hours on Harvest.
- Updating trello.
- Update process report.
- Update drive.

##Used techniques from courses
###CSS To The Rescue
------
####Flexbox
Used flexbox to create the application's layout. For the browsers that don't support flexbox I provided a fallback using modernizr. You can find the fallback file at ``/public/src/css/flexboxfallback.css``.

####Mobile First approach
All the features and design elements I created, were developed using the mobile first approach. This helped me to think about the core features and elements that the application needed.

####Centering
Centered elements both horizontally and vertically using ``display: flex`` and ``margin: auto``.

####Prefixes
Added prefixes to certain elements using autoprefixer.

####Custom checkbox
Created a custom checkbox as explained in Lea Verou's CSS Secrets. A part of the code:

```
.match__item__submit input[type=checkbox]+ label::before {
    /*Will function as styled checkbox*/
    content: '\a0';
    display: inline-block;
    vertical-align: .1em;
    width: 1.25em;
    height: 1.2em;
    font-size: 1.2em;
    margin-right: .2em;
    border-radius: .2em;
    background: silver;
    text-indent: .10em;
    line-height: 1.1;
}
```

####:after
Created small triangles to highlight the current page in the menu. I did this using the ``:after`` pseudo-class. In the end these triangles were deleted as we changed the menu's design.

####CSS transitions and animations
I created a splash screen using CSS animations and keyframes. I also created a transition that animated an off-canvas menu to show on-canvas, pushing the content to the side. In the end this menu was taken out because we decided to implement a different design pattern.

For the matches page, I created a dropdown using CSS transitions and added an animation to the favorites button.

I also created and made use of reusable classifications for elements. This made it easy to quickly style multiple elements the same way.

###Web App From Scratch
------
####IIFE and namespacing
We made use of IIFE's (Immediately Invoked Function Expression). Only the relevant parts that will be used outside of the scope will be returned.
We also used namespacing to ensure that if the namespace that we used already exists, the code will be joined. If the current namespace doesn't exist, it will be created.

``var UFA = UFA || {};``

####Client-side routing
Made use of the client-side hash routing that was already setup.

####Strict mode
Implemented ``'use strict'`` to ensure the use of valid JavaScript notation.

####Functional animations with hardware accelerated properties
I created a functional animation and transition using hardware accelerated properties. I used the properties: 

- transform: translate
- transform: rotate
- opacity

```
.matches__item__arrow__up {
    position: relative;
    width: 1em;
    height: 1em;
    margin: auto;
    transition: transform 1.5s 0.3s;
}
.footer__menu.active {
    transform: translateY(4em);
}
```

####Templating
I made use of the templating engine Handlebars to render the pages. This makes your pages dynamic, because it will inject the content it needs into the layout.

```
{{#if items }}
    <section id="favorites" class="matches__items">
        <div class="matches__division">
            {{#each items}}
                {{> content_matches}}
            {{/each}}
        </div>
    </section>
    {{ else }}
    <h1 class="header__message">{{ message }}</h1>
{{/if}}
```

####Data handling
Manipulated data that came from the API and rendered these in the right views.

```
findMatches(db, function() {
  res.render('favorites', {
      title: 'Favorites',
      items: favMatches
  });
});
```

####Get and Post requests
Made use of, edited and created get and post requests to the leaguevine API. An example of this is the get request to the favorites page.

####Changing scores
I created the functionality for the score buttons. Adding or subtracting from the score on certain button click. This data was sent to the API. Later on in the project we integrated MongoDB in the project, the buttons eventually sent this data to the database instead of the API.

###Performance Matters
------
####Gulp - Critical CSS
Made use of and edited gulp when needed. Edited the CriticalCSS gulp task to create critical css.

####LoadCSS
Implemented and setup load css for the asynchronous loading of CSS. This in combination with CriticalCSS led to a faster and better First Meaningful Render.


```
<link rel="preload" href="/dist/css/style.min.css" as="style" onload="this.rel='stylesheet'">
<noscript>
   <link rel="stylesheet" href="/dist/css/style.min.css">
</noscript>

<!-- LoadCSS -->
<script>
	!function(e){"use strict";var t=function(t,n,r){function f(e){return a.body?e():void setTimeout(function(){f(e)})}function u(){l.addEventListener&&l.removeEventListener("load",u),l.media=r||"all"}var o,a=e.document,l=a.createElement("link");if(n)o=n;else{var i=(a.body||a.getElementsByTagName("head")[0]).childNodes;o=i[i.length-1]}var d=a.styleSheets;l.rel="stylesheet",l.href=t,l.media="only x",f(function(){o.parentNode.insertBefore(l,n?o:o.nextSibling)});var s=function(e){for(var t=l.href,n=d.length;n--;)if(d[n].href===t)return e();setTimeout(function(){s(e)})};return l.addEventListener&&l.addEventListener("load",u),l.onloadcssdefined=s,s(u),l};"undefined"!=typeof exports?exports.loadCSS=t:e.loadCSS=t}("undefined"!=typeof global?global:this),function(e){if(e.loadCSS){var t=loadCSS.relpreload={};if(t.support=function(){try{return e.document.createElement("link").relList.supports("preload")}catch(t){return!1}},t.poly=function(){for(var t=e.document.getElementsByTagName("link"),n=0;n<t.length;n++){var r=t[n];"preload"===r.rel&&"style"===r.getAttribute("as")&&(e.loadCSS(r.href,r),r.rel=null)}},!t.support()){t.poly();var n=e.setInterval(t.poly,300);e.addEventListener&&e.addEventListener("load",function(){e.clearInterval(n)}),e.attachEvent&&e.attachEvent("onload",function(){e.clearInterval(n)})}}}(this);
</script>
```

####Semantic HTML and CSS
Wrote semantic HTML and CSS to boost the page's performance.

####BEM
Made use of the BEM notation for classes and id's. By using the BEM notation you make your project's code more organized. It's especially useful when in a group, since you will use one form of notation. Developers claim it helps with efficiency and how much code you eventually write. Which will subsequently improve your page's load time.

```
<div class="matches__division">
	<h1 class="matches__division__title">CMD Amsterdam</h1>
	<div class="matches__container">
	    {{#each liveCMD}}
	        {{> content_matches}}
	    {{/each}}
	</div>
</div>
```

###Real Time Web
------
####Real time aspect
Made use of socket.io to create the real time aspect of the application. In the end I fixed an important part of the real time aspect with the help of Robert van Steen.

####Mongo collections
Manipulated mongodb collections to save and delete data. This way we were able to give the application a significant speed boost, since it was no longer dependent on the speed of the LeagueVine API. The setup of the collections was a collaborative effort, but Fons and Senny setup the biggest part of the database and its collections.

###Browser Technologies
------
####Progressive enhancement
Made the application's core functionality available without JavaScript. The user gets a better experience with extra functionalities if JavaScript is turned on or the browser supports it.

####Check for color blindness
Looked at the application using the "SEE" extension for chrome. This way I was able to see if the application could be used by users with certain types of sight problems. The application was still easy to use. 

####Browser and device compatibility
The application was tested on a multitude of devices and browsers. Including an old version of Chrome for Android and the foreign UC Browser. The application looked fine and worked good on these browsers and most devices.
