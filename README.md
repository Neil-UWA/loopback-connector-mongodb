## loopback-connector-mongodb

MongoDB connector for loopback-datasource-juggler.

Please see the full documentation at [docs.strongloop.com](http://docs.strongloop.com/display/LB/MongoDB+connector).

## Customizing MongoDB configuration for tests/examples

By default, examples and tests from this module assume there is a MongoDB server
instance running on localhost at port 27017.

To customize the settings, you can drop in a `.loopbackrc` file to the root directory
of the project or the home folder.

**Note**: Tests and examples in this project configure the data source using the deprecated '.loopbackrc' file method, 
which is not suppored in general.
For information on configuring the connector in a LoopBack application, please refer to [LoopBack documentation](http://docs.strongloop.com/display/LB/MongoDB+connector).

The .loopbackrc file is in JSON format, for example:

    {
        "dev": {
            "mongodb": {
                "host": "127.0.0.1",
                "database": "test",
                "username": "youruser",
                "password": "yourpass",
                "port": 27017
            }
        },
        "test": {
            "mongodb": {
                "host": "127.0.0.1",
                "database": "test",
                "username": "youruser",
                "password": "yourpass",
                "port": 27017
            }
        }
    }

**Note**: username/password is only required if the MongoDB server has
authentication enabled.

## Running tests

The tests in this repository are mainly integration tests, meaning you will need
to run them using our preconfigured test server.

1. Ask a core developer for instructions on how to set up test server
   credentials on your machine
2. `npm test`

## Leak detection

Tests run for 100 iterations by default, but can be increased by setting the
env var `ITERATIONS`.

```
make leak-detection # run 100 iterations (default)
```

or

```
ITERATIONS=1000 make leak-detection # run 1000 iterations
```

## Release notes

  * 1.1.7 - Do not return MongoDB-specific _id to client API, except if specifically specified in the model definition
