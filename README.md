# Golang Project Structure


## Example Serverless Layout

| Path      | Content                                    | Go?       | Notes                                                         |
|-----------|--------------------------------------------|-----------|---------------------------------------------------------------|
| /         | README.md, Makefile, go.mod, no Go code    | No        |                                                               |
| /assets   | Email templates, images etc                | No        |                                                               |
| /configs  | Configuration files                        | No        |                                                               |
| /cmd      | Applications (main files, lambdas)         | Yes       |                                                               |
| /db       | Database schemas and migrations            | No        | Already have schema, probably fine as is                      |
| /deploy   | Deployment configuration (cloud formation) | No        | Probably not worth moving from root given complexity involved |
| /docs     | Design and user documentation              | No        |                                                               |
| /internal | Private application and library code       | Yes       | Enforced by compiler                                          |
| /pkg      | Library code that is safe to share         | Debatable |                                                               |
| /testdata | Test fixtures                              | No        | Convention of standard library                                |
| /tools    | Supporting tools, e.g. CLI                 | Yes       |                                                               |
| /vendor   | Application dependencies                   | No        | Not in .git, managed by go mod                                |


## Example Library Layout

| Path      | Content                          | Go?       | Notes                |
|-----------|----------------------------------|-----------|----------------------|
| /         | README.md, go.mod, not much else | Maybe     |                      |
| /internal | Private library code             | Yes       | Enforced by compiler |
| /pkg      | Public API                       | Debatable |                      |


### References

- https://github.com/golang-standards/project-layout
- https://travisjeffery.com/b/2019/11/i-ll-take-pkg-over-internal/
- https://www.wolfe.id.au/2020/03/10/how-do-i-structure-my-go-project/
- https://medium.com/golang-learn/go-project-layout-e5213cdcfaa2


## Files and Packages

- Package names should be short, be singular, contain no underscores and avoid stutter
- Packages should be organised by feature not type (e.g. `profile.User` vs `model.User`)
- File names can have underscores for readability ([examples](https://golang.org/src/html/template/) in standard library)
- Libraries should only have a single purpose, and therefore tend to be small


### References

- https://rakyll.org/style-packages/
- https://golang.org/doc/effective_go#names
- https://www.ardanlabs.com/blog/2017/02/design-philosophy-on-packaging.html
