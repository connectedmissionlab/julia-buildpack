# Julia Buildpack

Build the pack locally:

```bash
pack build sample-app --path ~/.julia/dev/SampleApp --buildpack ./julia-buildpack --builder gcr.io/buildpacks/builder:v1
```

Launch `julia`:
```bash
docker run -it --entrypoint julia sample-app
```

Inspect the container:
```bash
docker run -it --entrypoint /bin/bash sample-app
```

If you just want to containerize `julia` without including a sample app:
```bash
pack build julia-buildpack --buildpack ./julia-buildpack --builder gcr.io/buildpacks/builder:v1
```

Hint: enable verbose with `-v`.

Then, you can run the julia REPL with
```
docker run -it julia-buildpack
```
