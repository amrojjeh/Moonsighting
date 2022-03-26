# Moonsightings

Data is retreived from [Central Hilal Committee of North America](https://hilalcommittee.org).

Hijri year and month can be calculated using the index of each sighting. The first sighting commences 1443 Muharram. The next sighting is 1433 Safar, and so forth.

Assuming index starts at 0, a formula to calculate the year is: `i // 12 + 1433`, where `//` means floor division. To calculate the month: `i % 12`, where 0 is Muharram.