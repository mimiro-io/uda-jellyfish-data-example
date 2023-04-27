# uda-jellyfish-data-example
Example project to expose CSV data using ObjectStorage Data Layer and Data Hub

# Installation

* Install docker and docker compose.
* Install the mimiro datahub client (mim) (https://github.com/mimiro-io/datahub-cli)

* Set the environment variable JELLYFISHHOME to the path of the project.

```
export JELLYFISHHOME=/path/to/uda-jellyfish-data-example
```

* In the compose folder run the following command to start the datahub and the data layer:

```
docker-compose up -d
```

* Connect mim to this datahub instance

```
mim login add --alias "dh1" --type=unsecured --server="http://localhost:4242"
mim login dh1
mim datasets ls
```

* Create the dataset

```
mim dataset create ocean.jellyfish
```

* In the jobs folder run the following command to load the data sync job

```
mim jobs add -f sync.json
```

* To run the job immediately run the following command:

```
mim jobs operate load-jellyfish-data -o run
```

* Check that data has been loaded into the datahub by running the following command:

```
mim dataset entities ocean.jellyfish --pretty
```

