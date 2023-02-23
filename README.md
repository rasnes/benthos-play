# benthos-play

## How to run

To run `./config.yaml`, which fetches a weather forecast from yr.no API, 
filters with `bloblang` processor,
and writes to `stdout` and `BigQuery`.

(Requires `benthos` to be installed, `brew install benthos`)

```bash
benthos -c ./config.yaml
```

### Unit tests

Run unit tests that tests the `processor` step using example inputs and outputs:
is the output of the `bloblang` processor (other processers are availble as well!)
as expected?

```bash
benthos test ./yr_test.yaml
```

## Note on efficiency

It took me two hours to set up this pipeline, and it's the first time
I've used `benthos`, `bloblang` and the yr.no API. It seems to a sweet
spot for abstractions, if you ask me!

## Qs

- How would I parametrise the `benthos` config file?
  - Like if the URL parameters changes with the current_date - 1 or something
  - I guess via the CLI somehow, but how to get the parameter into the container?
  - One option: pass as CLI arguments to a Cloud Run Job, that's easy at least.
  - But what about parameters from a PubSub/Eventarc message?
- The BQ schema seems poorly supported. You seem to need to manage it fully via Terraform.
