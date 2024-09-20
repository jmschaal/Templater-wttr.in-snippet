# Templater wttr.in snippet for Obsidian

This snippet inserts the current weather information from v2.wttr.in into an obsidian note using the ![Templater](https://github.com/SilentVoid13/Templater) plugin.

```ts
<%*
const params = {
    url: 'https://v2.wttr.in/?T',
    headers: { 
		 "User-Agent": 'curl',
	     Accept: 'text/html'
	}
};
const response = await requestUrl(params);
let weather = response.text;
weather = weather.replaceAll('\x0F','')
weather = weather.split('\n');
weather.splice(-7,7)
weather = weather.join('\n')
tR += weather
%>
```

The snippet requests the weather information from ![v2.wttr.in](https://github.com/chubin/wttr.in) parses the output.

It is necessary to use the User-Agent string used by curl in order for wttr.in to return plain text instead of html code.

The output of v2.wttr.in contains shift-in characters (\x0F) that are not rendered properly by obsidian which means they have to be removed. 
Additionally, the T parameter is used, which tells wttr.in to ommit the terminal color codes.

Finally the information block and socials at the bottom of the wttr.in output are removed and the result is added to the note.

Templater wttr.in snippet © 2024 by J. Schaal is licensed under CC BY-NC-SA 4.0 
