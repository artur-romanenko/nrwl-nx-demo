# nrwl-nx-demo
Nx demo project:
- monorepos
- nx affected
- nx computation cache
- nx cloud


Apps:
angular - todos
node - api

Libs:
...

Commands:
nx serve todos

Note, re-install cypress (delete cypress cache folder first):
npx cypress install

nx e2e todos-e2e --watch

Create node API project:
nx g @nrwl/nest:app api --frontendProject=todos
Note, "--frontendProject=todos" creates proxy configuration.
nx serve api

Create a library to share code:
nx g @nrwl/workspace:lib data

Create a library of Angular components:
nx g @nrwl/angular:lib ui

Add a component to the ui library:
nx g component todos --project=ui --export

Dep Graph
nx dep-graph or npm run dep-graph

...