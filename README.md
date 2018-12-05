# NS-Vue with RLV

> NativeScript-Vue app which uses RadListView

## Setup

``` bash
# Install dependencies
npm install

# Install json-server globally
npm install -g json-server

# Start the REST service
json-server --watch db.json
```

## Usage

``` bash
# Build for production
tns build <platform> --bundle

# Build, watch for changes and debug the application
tns debug <platform> --bundle

# Build, watch for changes and run the application
tns run <platform> --bundle
```