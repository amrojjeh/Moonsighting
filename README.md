# Moonsightings

Data is retreived from [Central Hilal Committee of North America](https://hilalcommittee.org).

## How Data Was Retrieved
I ran this piece of Javascript code on the [news](https://hilalcommittee.org/news) website after loading all the news:

```javascript
let news = document.getElementById("news_area");
let regex = /(((January|Jan|February|Feb|March|April|May|June|July|August|Aug|September|Sept|October|Oct|November|Nov|December|Dec)\s*\d+(st|rd|th)*,*\s*\d{4})|(\d+(st|rd|th)*\s(January|Jan|February|Feb|March|April|May|June|July|August|Aug|September|Sept|October|Oct|November|Nov|December|Dec)\s+\d{4}))/;
let sightings = [];

for (let n of news) {
	if (n.innerText.toLowerCase().includes("sighted")) {
		let sighting = {};
		let matches = n.getElementsByTagName("p")[0].innerText.match(regex);
		if (!matches) {
			console.log(n.getElementsByTagName("p")[0].innerText);
			continue;
		}
		sighting.date = matches[0];
		if (n.innerText.toLowerCase().includes("not")) {
			sighting.sighted = false;
		} else {
			sighting.sighted = true;
		}
		sightings.push(sighting);
	}
}
```

I then 
1) manually added the ones I could not automatically retrieve (if they were missing from the news page, I looked through their [twitter](https://twitter.com/CentralHilalCmt));
2) fixed dates so that they're compliant with ISO 8601;
3) added the Islamic month and year;
4) added first day of each Islamic month.

Steps two, three and four were done using automation.

Sightings after March 3rd, 2022 should be entered manually.
