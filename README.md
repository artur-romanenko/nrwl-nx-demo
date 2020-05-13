# Nx demo

- monorepos
- nx affected
- nx computation cache
- nx cloud

Steps:
1. Build a full stack application using Angular and Nest.
2. Share code between the frontend and the backend.
3. Create a UI library.
4. Demo computation cache.
5. Demo Nx dep graph capabilities to only retest and rebuild what is affected.


## Projects structure

Apps:  
	todos - Angular app  
	todos-e2e - E2E tests for the Angular app  
	api - Node app (Nest framework)  

Libs:  
	data - to share contracts  
	ui - Angular components  


## Useful commands

First, either install the nx cli globally:  
`npm install -g @nrwl/cli`  
`yarn global add @nrwl/cli`

or you can prepend every command with npm run:  
`npm run nx -- serve todos`  
`yarn nx serve todos`

Create a New Workspace  
`npx create-nx-workspace@latest`

Start Angular app  
`nx serve todos`

E2E tests - How to run  
`nx e2e todos-e2e --watch`  
`nx e2e todos-e2e --headless`

E2E tests - Note on Cypress  
`npx cypress install`  
> In case of errors, Cypress needs to be re-installed (delete Cypress cache folder first)  

Create Node API project (Nest):  
`nx g @nrwl/nest:app api --frontendProject=todos`
> Note, "--frontendProject=todos" creates proxy configuration.
`nx serve api`

Create a library to share code:  
`nx g @nrwl/workspace:lib data`

Create an Angular library of Angular components:  
`nx g @nrwl/angular:lib ui`

Add a component to the ui library:  
`nx g component todos --project=ui --export`

Dep Graph  
`nx dep-graph or npm run dep-graph`

Building Multiple Projects  
`nx run-many --target=build --projects=todos,api`

Lint app with its dependecies  
`nx lint todos --with-deps`

Affected  
`nx affected:build`  
`nx affected --target=build`  
> Note, the above are equivalent  

Affected graph 
`nx affected:dep-graph`

Test Affected Projects  
`nx affected:test`  
`npm run affected:test -- --only-failed`