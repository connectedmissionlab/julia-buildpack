# Julia Buildpack

You can build locally a Cloud Native Buildpack for `julia` in 2 different modes:

- with a specific package
- without a specific package

## With a specific package

Build the pack locally:

```bash
pack build sample-app -v --path ~/.julia/dev/SampleApp --buildpack ./julia-buildpack --builder gcr.io/buildpacks/builder:v1
```

Launch `julia`:
```bash
docker run sample-app
```

Inspect the container:
```bash
docker run -it --entrypoint /bin/bash sample-app
```

## Without a specific package

If you just want to containerize `julia` without including a sample app:
```bash
pack build julia-buildpack --buildpack ./julia-buildpack --builder gcr.io/buildpacks/builder:v1
```

Then, you can run the julia REPL with
```
docker run -it julia-buildpack
```
