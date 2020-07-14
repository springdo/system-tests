# 👩‍🔬📋👨‍🔬 SystemTestsScaffold

This project was generated with [Angular CLI](https://github.com/angular/angular-cli) version 10.0.1.

## 🏃‍♂️Running end-to-end tests locally

Run `npm run e2e` to execute the end-to-end tests via [Protractor](http://www.protractortest.org/). You can run `npm run e2e:headless` if you don't want the browser popping up.


## 🏃‍♀️Running end-to-end tests against Selenium Grid
1. Deploy Zalenium using helm to a target namespace eg `testy-mctestface`:
```bash
helm repo add zalenium-github https://raw.githubusercontent.com/zalando/zalenium/master/charts/zalenium
helm install uj --namespace testy-mctestface zalenium-github/zalenium --set hub.openshift.route.enabled=true
```
2. Export the endpoint to be tested and run the tests pointing to your grid
```bash
export ZALENIUM_ROUTE=(oc get routes uj-zalenium -n testy-mctestface -o jsonpath='{.spec.host}')
export E2E_TEST_ROUTE=my-app.example.com
npm run e2e:ci
```

## 📰Reporting
A Cucubmber JSON report for consumption in CI is located in `./reports/` along with a HTML report supporting multiple browsers out of the box `./reports/index.html` 
