 # Brotodroid - Initial Review 

 Over the past years we have seen the rise and controversies of the web development community and various frameworks, however, as time goes on the community is slowly uniting together again to tackle various issues like Electron and the need of a good desktop or mobile framework that helps them build native apps by only using web technologies like HTML5, CSS and JavaScript. Brontodroid is an attempt to answer that need for the mobile platform 'Android'. This RFC goes over what are the goals and philosophies behind it.

 

 ## Goal: 

 The primary goal is to deliver a good experience by providing the best of both worlds, that is providing a stable and strong system as Electron, while being performant and having a tiny package size like Tauri. We aim to use Deno as the core API (with the exception of Deno FFI, as per an extension API that relies on the Android JVM would be much more effective) as the execution layer instead of Node API as it's much smaller and more efficient than Node for a few reasons. On top of that, we want to implement our own API to control parts of android ecosystem like Window Management, Notifications, Toasts, and much more. To top it all off, you would be able to write your own extensions to expand the API.

 

 ## Philosophy:

 We at WebSmith have a philosophy of keeping things straight to point, no unnecessary things or bloat, and stay reliable. Brontodroid aims to be performant and be highly compatible as it relies on Android's WebView API. We also believe in open source, and it bringing people together to work on something they love and that would benefit them and others. 

 

 ## Why?

 Web Development is a diverse community, yet it lacks development frameworks for android. Well, how about Flutter or React Native, you might ask? While yes, people may like and prefer those, but there are people out there who would like to use Deno to build Android Apps, the Deno ecosystem as of right now isn't as diverse as Node's due to Node being around for much longer, this also aims to enrich the Deno Ecosystem. 

 

 --- 

 Thank you for reading. Please provide feedback and critique things where necessary.
