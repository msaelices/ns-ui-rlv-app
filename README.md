# NS-Vue with RLV

> NativeScript-Vue app which uses RadListView

## Setup

* Install ngrok from https://ngrok.com/download

* Install node dependencies

``` bash
npm install
```

* Install `json-server` globally

``` bash
npm install -g json-server
```

* Start the REST service (will listen on 3000 port)

``` bash
json-server --watch db.json
```

* Start ngrok in a new terminal

``` bash
ngrok http 3000
```

* Open the `app/constants.js` file and change `YOURHASH` with your ngrok hash


## Usage

``` bash
# Build for production
tns build <platform> --bundle

# Build, watch for changes and debug the application
tns debug <platform> --bundle

# Build, watch for changes and run the application
tns run <platform> --bundle
```