---
layout: default
title: Build
permalink: /javascript/angular/build/

---

# Build the application

## Environment files

The files describing each environment are stored in the directory :

```
src\environments
```

For each environment, it is necessary to create a new file with the following format `environment.XXXXX.ts`. We will find inside all the constants necessary to use Angular on the different environments such as: DB, URL of the site,...

## Configuration :

the configuration of the application is defined in **angular.json** where we will find all the definitions of the environments. For each configuration a new location must be created as in the example above with the "dev" or "pre-prod" configuration. Then it is possible to define different parameters in the configuration such as environment variables, redefine the output of the build `outputPath`, build parameters, internationalization...

```json
"configurations": {
	"dev": {
		"fileReplacements": [{
			"replace": "src/environments/environment.ts",
			"with": "src/environments/environment.dev.ts"
		}]
	},
	"pre-prod": {
		"fileReplacements": [{
			"replace": "src/environments/environment.ts",
			"with": "src/environments/environment.ppr.ts"
		}]
	}
}
```

## Builds cli :

- Build an application for production :

```bash
$ ng build --configuration=production
```

- Build an application with internationalisation options :

  [https://angular.io/guide/i18n](/https://angular.io/guide/i18n)
