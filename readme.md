<center><img src="https://raw.githubusercontent.com/JuliaLang/julia-logo-graphics/master/images/julia-logo-color.svg" height="50px"></center>
<center><img src="https://buildpacks.io/images/buildpacks-logo.svg" height="50px"></center>

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
pack build example-app -v \
           --path ~/.julia/dev/Example \
           --buildpack ./julia-buildpack \
           --builder gcr.io/buildpacks/builder:v1
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
pack build julia-buildpack \
           --buildpack ./julia-buildpack \
           --builder gcr.io/buildpacks/builder:v1
```

Then, you can run the julia REPL with
```
docker run -it julia-buildpack
```

> Copyright 2024 Connected Mission Lab
>
>   Licensed under the Apache License, Version 2.0 (the "License");
>   you may not use this file except in compliance with the License.
>   You may obtain a copy of the License at
>
>       http://www.apache.org/licenses/LICENSE-2.0
>
>   Unless required by applicable law or agreed to in writing, software
>   distributed under the License is distributed on an "AS IS" BASIS,
>   WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
>   See the License for the specific language governing permissions and
>   limitations under the License.
