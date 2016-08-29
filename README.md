  
> *So you've developed this shiny new website but your editors and marketing guys keep complaining they need more "native embedded content" with shiny share and retweet buttons because otherwise their text will look like ...text?      
Look no further: This processwire module has you covered!*   


#TextformatterOEmbed for processwire
---


### What it does

At this point this module basically wraps the fabolous [Essence](https://github.com/felixgirault/essence) PHP library by Félix Girault and adds some processwire magic to parse your boring Textareas and make your content look more ***bling bling***  than ever before.  
Disclaimer: This Module is heavily inspired by [TextFormatterVideoEmbed](https://github.com/ryancramerdesign/TextformatterVideoEmbed) by the awesome guy who created processwire: [RyanCramer](http://www.ryancramer.com/).   

### Requirements
- php 5.4+
- curl and/or allow_fopen on

### Features

- **Supports the following 32 providers out of the box**
```html
23hq             Dipity          Official.fm     Ted
Bandcamp         Flickr          Polldaddy       Twitter
Blip.tv          FunnyOrDie      Prezi           Vhx
Cacoo            HowCast         Qik             Viddler
CanalPlus        Huffduffer      Revision3       Vimeo
Chirb.it         Hulu            Scribd          Yfrog
Clikthrough      Ifixit          Shoudio         Youtube
CollegeHumor     Imgur           Sketchfab
Dailymotion      Instagram       SlideShare
Deviantart       Mobypicture     SoundCloud
``` 
(*That's a lot of Hanna-Codes you can get rid of now, eh?*):   
- **[Add your own providers in the blink of an eye](#own)** (if you're not good at regex - like me - it will propably take you a cup of coffee and a google search) 
- **Easy styling**: Wraps embedded items with customizable [BEM-Style](http://www.integralist.co.uk/posts/maintainable-css-with-bem/) classes including modifiers for every provider and embedtype. Choose to either add CSS directly in the modules configuration or to your existing stylesheets 
- **Choose to add pre defined Fluid Video CSS for your responsive design** (*or - again - feel free to add your own*)

### Usage
- Click *check for new modules* in ProcessWire Admin Modules screen. Click *install* for the module labeled: "oEmbed for processwire".
- Install the module
- Open the modules Settings page
- Add css classes either within the "Custom CSS" field or in a seperate CSS file. Every provider is wrapped with the following markup:   
```html
<div class="pw-oembed pw-oembed--providername pw-oembed--embedtype">
	<div class="pw-oembed__inner pw-oembed__inner--providername pw-oembed--embedtype"></div>
</div>
```   
If you're not happy with the "block" class .pw-oembed you can rename it to something you like better using the modules config. Every embedded media item and it's respective inner wrapper has two modifier classes: One for the provider (i.e. youtube, twitter...) and one for the media type (one of photo, video, link or rich according to the [OEmbed specification](http://oembed.com/)). This should be enough classes to add some fancy icons, adjust widths per provider or whatever else you like to do.
- <a name="own"></a>If you're missing a provider don't hesitate to open a pull request (see [roadmap](#roadmap) first) and  I'll do my best to add it as soon as possible. In the meantime you can extend the [available providers found in lib/essence/providers.php](lib/essence/providers.php) in the modules settings using the following JSON-Format (remember that you'll have to properly escape the regex):
```json
	[{
		"23hq" : { 
			"class" : "OEmbed",
			"filter" : "#23hq\\.com/.+/photo/.+#i",
			"endpoint" :"http://www.23hq.com/23/oembed?format=json&url=%s"
		}
	}]
```



<a name="roadmap"></a>
### Roadmap

- Add *moaaar* providers: 
	- Facebook (currently not providing a "native" oEmbed API)
	- Google Plus (currently not providing a "native" oEmbed API)
	- support for more fancy integration of Instagram posts (currently there are "just" images without fancy sharing stuff that will be embedded)
- Render only one javascript (i.e. ) when there are multiple items of the same provider 
- Propably make this module more generic and add services as submodules at some point
- World domination

### Bugs, Suggestions, Contact
Feel free to file bugs using the [issue tracker](issues)

If you've got any questions regarding the module just drop me a line via  [e-mail](mailto:felix.wahner@neuwaerts.de), on [twitter](https://twitter.com/felixwahner)  or contact me in the processwire [forums](https://processwire.com/talk/user/934-felix/).


### License

- This module is licensed under the [MIT License](LICENSE.txt).
- The included Library "Essence" by Félix Girault is licensed under the [FreeBSD License](lib/essence/LICENSE.txt).


