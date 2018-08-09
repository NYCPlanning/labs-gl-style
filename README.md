# labs-gl-style
A generic MapboxGL openstreetmap style for use in NYC Planning Labs mapping projects

## About
This repo contains a `style.json` based on positron that will be used as a generic osm/openmaptiles-based basemap for NYC Planning Labs projects.

It also contains a simple mapboxGL map that consumes the `style.json`, so you can test the style locally or [view it on github pages](https://nycplanning.github.io/labs-gl-style/).

## Files
`data/v3.json` - tileJSON describing the vector tiles hosted at `tiles.planninglabs.nyc`

`data/style.json` - a custom mapboxGL style (based on [positron](https://github.com/openmaptiles/positron-gl-style))

## Local Development
- Clone this repo `git clone https://github.com/NYCPlanning/labs-gl-style.git`
- Run a local webserver `cd labs-gl-style && python -m SimpleHTTPServer 8000`
- Use [maputnik-dev-server](https://github.com/NYCPlanning/labs-maputnik-dev-server) to edit the style, copy and paste new layer configs into `data/style.json`

## openmaptiles Server
Run with `sudo docker run -d -v $(pwd):/data -p 8080:80 klokantech/openmaptiles-server` (removes --it and --rm flags that are used in the example, so that the container's filesystem can persist.

## Sprites
Use [spritezero-cli](https://github.com/mapbox/spritezero-cli) to create `.png` and `.json` files in `data/`.
- Install the command-line interface: `npm install -g @mapbox/spritezero-cli`
- Add/edit/delete SVG files in `svg/`
- Run the commands to generate the sprites at each resolution:
  - `spritezero data/sprite svg/`
  - `spritezero data/sprite@2x svg/ --ratio=2`

To test sprites locally:
- Temporarily change the `"sprite"` value to `"http://localhost:8000/data/sprite",`
- Enable CORS by running the local server with `python simple-cors-http-server.py`
