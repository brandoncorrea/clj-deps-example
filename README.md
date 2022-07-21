# clj-deps-example
A Clojure deps example project to import repositories by git URL+SHA, rather than deploying as a public repository.

## Setting up the External Library (ie. this project)

For use in `deps.edn`:
- A `deps.edn` file will be needed with your paths and dependencies

For use in `project.clj`:
- A `project.clj` file will be needed with your paths and dependencies

For use in either `deps.edn` or `project.clj`:
- Both `deps.edn` and `project.clj` files will be needed.

Note: In theory, if your external library is a `deps.edn` project, you *could* get away without 
having a `project.clj` file, but you would need all your clj, cljc, and cljs code under the same `src` directory

## Importing the External Library Into Your Project

### `deps.edn`

- `:git/url`: The URL of the Git repo
- `:sha`: The full SHA of the specific commit/checkpoint you want to pull from

````clj
{:deps {brandoncorrea/clj-deps-example {:sha     "4d72c44073015b66924a560158bd4babbc0489f2"
                                        :git/url "https://github.com/brandoncorrea/clj-deps-example.git"}}
````

### `project.clj`

See [lein-git-down](https://github.com/reifyhealth/lein-git-down) about targeting specific
remote Git `:coordinates`.

> By default, the dependency's Maven group/artifact coordinates are used, 
> however, this often does not match the "owner" and "project" coordinates of a Git
> repository. This property provides the mapping.

````clj
(defproject my/app "0.1.0"
  :repositories {"public-github" {:url "git://github.com"}}
  :dependencies [[brandoncorrea/clj-deps-example "4d72c44073015b66924a560158bd4babbc0489f2"]])
````
