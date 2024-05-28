# Julia Buildpack

You can build locally a Cloud Native Buildpack for `julia` in 2 different ways:

- with a specific package
- without a specific package

## With a specific package

For illustration purposes, you can add the [Julia Example.jl](https://github.com/JuliaLang/Example.jl) package.

Open `julia` locally, and `dev` the `Example.jl` package or run the following from the terminal:

```bash
julia -e 'import Pkg; Pkg.develop("Example");'
```

Build the pack locally (outside the `julia-buildpack`) directory:

```bash
pack build example-app -v --path ~/.julia/dev/Example --buildpack ./julia-buildpack --builder gcr.io/buildpacks/builder:v1
```

Launch `julia`:
```bash
docker run example-app
```

Inspect the container:
```bash
docker run -it --entrypoint /bin/bash example-app
```

## Without a specific package

If you just want to containerize `julia` without including a specific package:

```bash
pack build julia-buildpack --buildpack ./julia-buildpack --builder gcr.io/buildpacks/builder:v1
```

Then, you can run the julia REPL with
```
docker run -it julia-buildpack
```
