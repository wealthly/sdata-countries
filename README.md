# <img src="https://avatars1.githubusercontent.com/u/37033013?s=200&v=4" width="64" style="vertical-align:text-bottom"> sdata:countries
A dataset of countries and related information. The verified JSON dataset can be downloaded [here](https://raw.githubusercontent.com/Wealthly/sdata-countries/master/dist/data.json).

## Data Generation
This dataset is updated daily by an automated service which pulls data in from 2 distinct sources on the web, then consolidates and sanitizes the data. The sources include a public REST API and UN websites; each country must exist on 1 or more of the 2 sources to be included in the dataset. After the initial dataset is generated, any overrides manually defined in [src/overrides.json5](src/overrides.json5) are merged with the dataset. The final dataset is then written, as a JSON array in alphabetical order by their ISO defined two letter country code (alpha2Code), to [dist/data.json](../automated/dist/data.json) in the *automated* branch. Every day there is a commit pushed by the [devbot](https://github.com/wealthly-devbot) to the *automated* branch regardles if there are any data changes (eg. empty commits), this is to record that the automated service completed. Whenever data changes are included in the commit, the devbot will create a pull-request back to the *master* branch to be manually verified and merged, or rejected.

## Contributing and Issues
If you find incorrect data within the dataset, please create a pull-request with the corrections added to [src/overrides.json5](src/overrides.json5) or alternatively raise an [issue](../../issues/new).

## Example JSON
```javascript
[
  {
    "alpha2Code": "CA",
    "alpha3Code": "CAN",
    "numericCode": "124",
    "name": "Canada",          // "United States of America"
    "shortName": "Canada",     // "United States"
    "officialName": "Canada",  // "the United States of America"
    "topLevelDomains": ["ca"],
    "callingCodes": ["1"],
    "currencyCodes": ["CAD"],
    "languageCodes": ["en","fr"],
    "timeZones": ["-08:00","-07:00","-06:00","-05:00","-04:00","-03:30"],
    "latLong": [60.0,-95.0],
    "area": 9984670.0,         // km2
    "capital": "Ottawa",
    "region": "Americas",
    "subregion": "Northern America",
    "demonym": "Canadian",
    "population": "36155487"
  }
]
```
