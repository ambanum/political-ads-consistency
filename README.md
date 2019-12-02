# Political-ads-consistency

Displays the evolution of the number of political ads on Facebook claimed to be presented in the public reports, and how many are actually available through the API for research, for all European Union member states.

> Affiche l'évolution du nombre de publicités politiques sur Facebook prétendument présentées dans les rapports publics, et combien sont effectivement disponibles via l'API, pour tous les Etats membres de l'Union européenne.

## Motivation

Facebook lauched the “[Ads Library](https://www.facebook.com/ads/library/)” in May 2018 in order to bring more transparency about the ads concerning political issues that are published on its platform.

The Facebook Ads Library can be explored online through a web interface, and queried by an [API](https://www.facebook.com/ads/library/api/). For each country, aggregated data is published in the form of “reports”: a web page containing dynamic tables and a downloadable CSV file.

We wanted to assess the legality of ads displayed in France before the 2019 European elections. We managed to create a [crowdsourcing interface](https://disinfo.quaidorsay.fr/political-ads/crowdsourcing) and find suspicious content. By doing so, we also discovered many [limitations](https://disinfo.quaidorsay.fr/en/facebook-ads-library-assessment) to the API, and to the Ads Library in general.

In order to conduct research despite these limitations, we ended up [downloading](https://desinfo.quaidorsay.fr/ads/dumps/) regularly the content of the Ads Library through its [API](https://github.com/ambanum/political-ads-scraper). Over time, we observed that ads were removed from the library, in contradiction with Facebook’s pledge:

“The Library contains data on every active and inactive ad about social issues, elections or politics that's run since March 2019. We'll keep each of these ads in the Library for seven years.”

Here is the evolution of the number of ads claimed to be presented in the public reports, and how many are actually available through the API for research, for all European Union member states.

- - -

## Development

This project is built on top of [react-boilerplate](https://github.com/react-boilerplate/react-boilerplate).

### Installation

```sh
git clone https://github.com/ambanum/political-ads-consistency.git
cd political-ads-consistency
npm install
```

### Usage

Start the server

```sh
npm start
```

## Deployment

Build the app with the command:
```sh
npm run build
```

Test the result:
```sh
npm run start:prod
```

To deploy, you can build the application and send the built files to your server.

On your server, you can simply serve the built application as a set of static files.
For example, you can do this with Nginx by adding these lines to your configuration file:

```
…
location / {
    alias /home/user/political-ads-consistency/build/;
    index index.html;
    try_files $uri $uri/ index.html =404;
}
…
```

If you want to use a specific base path, for example `/political-ads-consistency`, you have to modify the `publicPath`value in webpack production file in `webpack/webpack.prod.babel.js`:
```
…
// Utilize long-term caching by adding content hashes (not compilation hashes) to compiled assets
output: {
  filename: '[name].[chunkhash].js',
  chunkFilename: '[name].[chunkhash].chunk.js',
  publicPath: '/political-ads-consistency/',
},
…
```

For information on how we deploy this app, you can take a look at the role `political-ads-consistency` in our [disinfo.quaidorsay.fr-ops repository](https://github.com/ambanum/disinfo.quaidorsay.fr-ops.git)

- - -

## License

EUPL v1.2: akin to an AGPL, but more readable and translated and legally binding into all languages of the EU. [Recap](https://choosealicense.com/licenses/eupl-1.2/).
