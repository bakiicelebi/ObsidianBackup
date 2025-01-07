```
import { ENVIRONMENT_TYPES, envLinks } from '@/core/utils/deploy';

export const detectEnvironment = () => {

  const currentUrl = window.location.href;

  _// Development Environment Check_

  if (

    currentUrl.includes(import.meta.env.VITE_PANEU_MEASURE_ADMIN_WEB_CLIENT_DEV_URL) ||

    currentUrl.includes(import.meta.env.VITE_PANEU_MEASURE_ADMIN_WEB_CLIENT_DEV_URL2) ||

    currentUrl.includes(import.meta.env.VITE_PANEU_MEASURE_ADMIN_WEB_CLIENT_DEV_URL3)

  ) {

    return ENVIRONMENT_TYPES.DEV;

  }

  _// TMMT Test Environment Checks_

  if (currentUrl.includes(envLinks.TMMT_TEST.adminFe)) {

    return ENVIRONMENT_TYPES.TMMT_TEST;

  }

  if (currentUrl.includes(envLinks.TMMT_TEST_NODE1.adminFe)) {

    return ENVIRONMENT_TYPES.TMMT_TEST_NODE1;

  }

  if (currentUrl.includes(envLinks.TMMT_TEST_NODE2.adminFe)) {

    return ENVIRONMENT_TYPES.TMMT_TEST_NODE2;

  }

  _// TMMT Production Environment Checks_

  if (currentUrl.includes(envLinks.TMMT_PROD.adminFe)) {

    return ENVIRONMENT_TYPES.TMMT_PROD;

  }

  if (currentUrl.includes(envLinks.TMMT_PROD_NODE1.adminFe)) {

    return ENVIRONMENT_TYPES.TMMT_PROD_NODE1;

  }

  if (currentUrl.includes(envLinks.TMMT_PROD_NODE2.adminFe)) {

    return ENVIRONMENT_TYPES.TMMT_PROD_NODE2;

  }

  _// TMUK Test Environment Checks_

  if (currentUrl.includes(envLinks.TMUK_TEST.adminFe)) {

    return ENVIRONMENT_TYPES.TMUK_TEST;

  }

  if (currentUrl.includes(envLinks.TMUK_TEST_NODE1.adminFe)) {

    return ENVIRONMENT_TYPES.TMUK_TEST_NODE1;

  }

  if (currentUrl.includes(envLinks.TMUK_TEST_NODE2.adminFe)) {

    return ENVIRONMENT_TYPES.TMUK_TEST_NODE2;

  }

  _// TMUK Production Environment Checks_

  if (currentUrl.includes(envLinks.TMUK_PROD.adminFe)) {

    return ENVIRONMENT_TYPES.TMUK_PROD;

  }

  if (currentUrl.includes(envLinks.TMUK_PROD_NODE1.adminFe)) {

    return ENVIRONMENT_TYPES.TMUK_PROD_NODE1;

  }

  if (currentUrl.includes(envLinks.TMUK_PROD_NODE2.adminFe)) {

    return ENVIRONMENT_TYPES.TMUK_PROD_NODE2;

  }

  _// If no environment matches, return UNKNOWN_

  return ENVIRONMENT_TYPES.UNKNOWN;

};
````
```





export const envLinks = {

  DEV: {

    operatorFe: import.meta.env.VITE_PANEU_MEASURE_OPERATOR_WEB_CLIENT_DEV_URL,

    operatorService: import.meta.env.VITE_PANEU_MEASURE_OPERATOR_BE_SERVICE_DEV_URL,

    adminFe: import.meta.env.VITE_PANEU_MEASURE_ADMIN_WEB_CLIENT_DEV_URL,

    adminService: import.meta.env.VITE_PANEU_MEASURE_ADMIN_BE_SERVICE_DEV_URL,

  },

  TMMT_TEST: {

    operatorFe: import.meta.env.VITE_PANEU_MEASURE_OPERATOR_WEB_CLIENT_TMMT_TEST_URL,

    operatorService: import.meta.env.VITE_PANEU_MEASURE_OPERATOR_BE_SERVICE_TMMT_TEST_URL,

    adminFe: import.meta.env.VITE_PANEU_MEASURE_ADMIN_WEB_CLIENT_TMMT_TEST_URL,

    adminService: import.meta.env.VITE_PANEU_MEASURE_ADMIN_BE_SERVICE_TMMT_TEST_URL,

  },

  TMMT_TEST_NODE1: {

    operatorFe: import.meta.env.VITE_PANEU_MEASURE_OPERATOR_WEB_CLIENT_TMMT_TEST_NODE1_URL,

    operatorService: import.meta.env.VITE_PANEU_MEASURE_OPERATOR_BE_SERVICE_TMMT_TEST_NODE1_URL,

    adminFe: import.meta.env.VITE_PANEU_MEASURE_ADMIN_WEB_CLIENT_TMMT_TEST_NODE1_URL,

    adminService: import.meta.env.VITE_PANEU_MEASURE_ADMIN_BE_SERVICE_TMMT_TEST_NODE1_URL,

  },

  TMMT_TEST_NODE2: {

    operatorFe: import.meta.env.VITE_PANEU_MEASURE_OPERATOR_WEB_CLIENT_TMMT_TEST_NODE2_URL,

    operatorService: import.meta.env.VITE_PANEU_MEASURE_OPERATOR_BE_SERVICE_TMMT_TEST_NODE2_URL,

    adminFe: import.meta.env.VITE_PANEU_MEASURE_ADMIN_WEB_CLIENT_TMMT_TEST_NODE2_URL,

    adminService: import.meta.env.VITE_PANEU_MEASURE_ADMIN_BE_SERVICE_TMMT_TEST_NODE2_URL,

  },

  TMMT_PROD: {

    operatorFe: import.meta.env.VITE_PANEU_MEASURE_OPERATOR_WEB_CLIENT_TMMT_PROD_URL,

    operatorService: import.meta.env.VITE_PANEU_MEASURE_OPERATOR_BE_SERVICE_TMMT_PROD_URL,

    adminFe: import.meta.env.VITE_PANEU_MEASURE_ADMIN_WEB_CLIENT_TMMT_PROD_URL,

    adminService: import.meta.env.VITE_PANEU_MEASURE_ADMIN_BE_SERVICE_TMMT_PROD_URL,

  },

  TMMT_PROD_NODE1: {

    operatorFe: import.meta.env.VITE_PANEU_MEASURE_OPERATOR_WEB_CLIENT_TMMT_PROD_NODE1_URL,

    operatorService: import.meta.env.VITE_PANEU_MEASURE_OPERATOR_BE_SERVICE_TMMT_PROD_NODE1_URL,

    adminFe: import.meta.env.VITE_PANEU_MEASURE_ADMIN_WEB_CLIENT_TMMT_PROD_NODE1_URL,

    adminService: import.meta.env.VITE_PANEU_MEASURE_ADMIN_BE_SERVICE_TMMT_PROD_NODE1_URL,

  },

  TMMT_PROD_NODE2: {

    operatorFe: import.meta.env.VITE_PANEU_MEASURE_OPERATOR_WEB_CLIENT_TMMT_PROD_NODE2_URL,

    operatorService: import.meta.env.VITE_PANEU_MEASURE_OPERATOR_BE_SERVICE_TMMT_PROD_NODE2_URL,

    adminFe: import.meta.env.VITE_PANEU_MEASURE_ADMIN_WEB_CLIENT_TMMT_PROD_NODE2_URL,

    adminService: import.meta.env.VITE_PANEU_MEASURE_ADMIN_BE_SERVICE_TMMT_PROD_NODE2_URL,

  },

  TMUK_TEST: {

    operatorFe: import.meta.env.VITE_PANEU_MEASURE_OPERATOR_WEB_CLIENT_TMUK_TEST_URL,

    operatorService: import.meta.env.VITE_PANEU_MEASURE_OPERATOR_BE_SERVICE_TMUK_TEST_URL,

    adminFe: import.meta.env.VITE_PANEU_MEASURE_ADMIN_WEB_CLIENT_TMUK_TEST_URL,

    adminService: import.meta.env.VITE_PANEU_MEASURE_ADMIN_BE_SERVICE_TMUK_TEST_URL,

  },

  TMUK_TEST_NODE1: {

    operatorFe: import.meta.env.VITE_PANEU_MEASURE_OPERATOR_WEB_CLIENT_TMUK_TEST_NODE1_URL,

    operatorService: import.meta.env.VITE_PANEU_MEASURE_OPERATOR_BE_SERVICE_TMUK_TEST_NODE1_URL,

    adminFe: import.meta.env.VITE_PANEU_MEASURE_ADMIN_WEB_CLIENT_TMUK_TEST_NODE1_URL,

    adminService: import.meta.env.VITE_PANEU_MEASURE_ADMIN_BE_SERVICE_TMUK_TEST_NODE1_URL,

  },

  TMUK_TEST_NODE2: {

    operatorFe: import.meta.env.VITE_PANEU_MEASURE_OPERATOR_WEB_CLIENT_TMUK_TEST_NODE2_URL,

    operatorService: import.meta.env.VITE_PANEU_MEASURE_OPERATOR_BE_SERVICE_TMUK_TEST_NODE2_URL,

    adminFe: import.meta.env.VITE_PANEU_MEASURE_ADMIN_WEB_CLIENT_TMUK_TEST_NODE2_URL,

    adminService: import.meta.env.VITE_PANEU_MEASURE_ADMIN_BE_SERVICE_TMUK_TEST_NODE2_URL,

  },

  TMUK_PROD: {

    operatorFe: import.meta.env.VITE_PANEU_MEASURE_OPERATOR_WEB_CLIENT_TMUK_PROD_URL,

    operatorService: import.meta.env.VITE_PANEU_MEASURE_OPERATOR_BE_SERVICE_TMUK_PROD_URL,

    adminFe: import.meta.env.VITE_PANEU_MEASURE_ADMIN_WEB_CLIENT_TMUK_PROD_URL,

    adminService: import.meta.env.VITE_PANEU_MEASURE_ADMIN_BE_SERVICE_TMUK_PROD_URL,

  },

  TMUK_PROD_NODE1: {

    operatorFe: import.meta.env.VITE_PANEU_MEASURE_OPERATOR_WEB_CLIENT_TMUK_PROD_NODE1_URL,

    operatorService: import.meta.env.VITE_PANEU_MEASURE_OPERATOR_BE_SERVICE_TMUK_PROD_NODE1_URL,

    adminFe: import.meta.env.VITE_PANEU_MEASURE_ADMIN_WEB_CLIENT_TMUK_PROD_NODE1_URL,

    adminService: import.meta.env.VITE_PANEU_MEASURE_ADMIN_BE_SERVICE_TMUK_PROD_NODE1_URL,

  },

  TMUK_PROD_NODE2: {

    operatorFe: import.meta.env.VITE_PANEU_MEASURE_OPERATOR_WEB_CLIENT_TMUK_PROD_NODE2_URL,

    operatorService: import.meta.env.VITE_PANEU_MEASURE_OPERATOR_BE_SERVICE_TMUK_PROD_NODE2_URL,

    adminFe: import.meta.env.VITE_PANEU_MEASURE_ADMIN_WEB_CLIENT_TMUK_PROD_NODE2_URL,

    adminService: import.meta.env.VITE_PANEU_MEASURE_ADMIN_BE_SERVICE_TMUK_PROD_NODE2_URL,

  },

  UNKNOWN: {

    operatorFe: '',

    operatorService: '',

    adminFe: '',

    adminService: '',

  },

};
```


````

envde tüm linkler bu şekilde tanımlı

VITE_REACT_APP_SERVER_ENDPOINT="api"

VITE_REACT_APP_SERVER_ACTUATOR_ENDPOINT=""

DISABLE_ESLINT_PLUGIN=true

VITE_REACT_APP_VERSION=$npm_package_version

VITE_REACT_APP_NAME=$npm_package_name

VITE_RECOMMENDED_MEAUSERE_ADMIN_VERSION="1.0.3.MEASURE-ADMIN-BR0"

VITE_PANEU_MEASURE_ADMIN_WEB_CLIENT_DEV_URL="[http://localhost:5173/"](http://localhost:5173/%22 "http://localhost:5173/%22")

VITE_PANEU_MEASURE_ADMIN_WEB_CLIENT_DEV_URL2="[http://localhost:5174/"](http://localhost:5174/%22 "http://localhost:5174/%22")

VITE_PANEU_MEASURE_ADMIN_WEB_CLIENT_DEV_URL3="[http://localhost:9010/"](http://localhost:9010/%22 "http://localhost:9010/%22")

_# Backend_

VITE_PANEU_MEASURE_ADMIN_BE_SERVICE_DEV_URL="[http://localhost:9003/paneumeasure-admin/"](http://localhost:9003/paneumeasure-admin/%22 "http://localhost:9003/paneumeasure-admin/%22")

_### Operator Development ###_

_# Frontend_

VITE_PANEU_MEASURE_OPERATOR_WEB_CLIENT_DEV_URL="[http://localhost:5173/"](http://localhost:5173/%22 "http://localhost:5173/%22")

VITE_PANEU_MEASURE_OPERATOR_WEB_CLIENT_DEV_URL2="[http://localhost:5174/"](http://localhost:5174/%22 "http://localhost:5174/%22")

VITE_PANEU_MEASURE_OPERATOR_WEB_CLIENT_DEV_URL3="[http://localhost:9010/"](http://localhost:9010/%22 "http://localhost:9010/%22")

_# Backend_

VITE_PANEU_MEASURE_OPERATOR_BE_SERVICE_DEV_URL="[http://localhost:9003/paneumeasure-operator/"](http://localhost:9003/paneumeasure-operator/%22 "http://localhost:9003/paneumeasure-operator/%22")

_# ==============================================_

_# TMMT Environment_

_# ==============================================_

_### TMMT Admin Service ###_

_## Test Environment_

_# Frontend_

VITE_PANEU_MEASURE_ADMIN_WEB_CLIENT_TMMT_TEST_URL="[http://measureadmintmmta/paneumeasure-admin-webclient"](http://measureadmintmmta/paneumeasure-admin-webclient%22 "http://measureadmintmmta/paneumeasure-admin-webclient%22")        _# Load Balancer_

VITE_PANEU_MEASURE_ADMIN_WEB_CLIENT_TMMT_TEST_NODE1_URL="[http://lxtkj2ea01:19400/paneumeasure-admin-webclient"](http://lxtkj2ea01:19400/paneumeasure-admin-webclient%22 "http://lxtkj2ea01:19400/paneumeasure-admin-webclient%22")  _# Node 1_

VITE_PANEU_MEASURE_ADMIN_WEB_CLIENT_TMMT_TEST_NODE2_URL="[http://lxtkj2ea02:19400/paneumeasure-admin-webclient"](http://lxtkj2ea02:19400/paneumeasure-admin-webclient%22 "http://lxtkj2ea02:19400/paneumeasure-admin-webclient%22")  _# Node 2_

_# Backend_

VITE_PANEU_MEASURE_ADMIN_BE_SERVICE_TMMT_TEST_URL="[http://measureadmintmmta-be/paneumeasure-admin/"](http://measureadmintmmta-be/paneumeasure-admin/%22 "http://measureadmintmmta-be/paneumeasure-admin/%22")             _# Load Balancer_

VITE_PANEU_MEASURE_ADMIN_BE_SERVICE_TMMT_TEST_NODE1_URL="[http://lxtkj2ea01:19000/paneumeasure-admin/"](http://lxtkj2ea01:19000/paneumeasure-admin/%22 "http://lxtkj2ea01:19000/paneumeasure-admin/%22")          _# Node 1_

VITE_PANEU_MEASURE_ADMIN_BE_SERVICE_TMMT_TEST_NODE2_URL="[http://lxtkj2ea02:19000/paneumeasure-admin/"](http://lxtkj2ea02:19000/paneumeasure-admin/%22 "http://lxtkj2ea02:19000/paneumeasure-admin/%22")          _# Node 2_

_## Production Environment_

_# Frontend_

VITE_PANEU_MEASURE_ADMIN_WEB_CLIENT_TMMT_PROD_URL="[http://measureadmintmmt/paneumeasure-admin-webclient"](http://measureadmintmmt/paneumeasure-admin-webclient%22 "http://measureadmintmmt/paneumeasure-admin-webclient%22")        _# Load Balancer_

VITE_PANEU_MEASURE_ADMIN_WEB_CLIENT_TMMT_PROD_NODE1_URL="[http://lxtkj2ea01:19400/paneumeasure-admin-webclient"](http://lxtkj2ea01:19400/paneumeasure-admin-webclient%22 "http://lxtkj2ea01:19400/paneumeasure-admin-webclient%22") _# Node 1_

VITE_PANEU_MEASURE_ADMIN_WEB_CLIENT_TMMT_PROD_NODE2_URL="[http://lxtkj2ea02:19400/paneumeasure-admin-webclient"](http://lxtkj2ea02:19400/paneumeasure-admin-webclient%22 "http://lxtkj2ea02:19400/paneumeasure-admin-webclient%22") _# Node 2_

_# Backend_

VITE_PANEU_MEASURE_ADMIN_BE_SERVICE_TMMT_PROD_URL="[http://measureadmintmmt-be/paneumeasure-admin/"](http://measureadmintmmt-be/paneumeasure-admin/%22 "http://measureadmintmmt-be/paneumeasure-admin/%22")             _# Load Balancer_

VITE_PANEU_MEASURE_ADMIN_BE_SERVICE_TMMT_PROD_NODE1_URL="[http://lxtkj2ea01:19000/paneumeasure-admin/"](http://lxtkj2ea01:19000/paneumeasure-admin/%22 "http://lxtkj2ea01:19000/paneumeasure-admin/%22")          _# Node 1_

VITE_PANEU_MEASURE_ADMIN_BE_SERVICE_TMMT_PROD_NODE2_URL="[http://lxtkj2ea02:19000/paneumeasure-admin/"](http://lxtkj2ea02:19000/paneumeasure-admin/%22 "http://lxtkj2ea02:19000/paneumeasure-admin/%22")          _# Node 2_

_### TMMT Operator Service ###_

_## Test Environment_

_# Frontend_

VITE_PANEU_MEASURE_OPERATOR_WEB_CLIENT_TMMT_TEST_URL="[http://measuretermtmmta/paneumeasure-operator-webclient"](http://measuretermtmmta/paneumeasure-operator-webclient%22 "http://measuretermtmmta/paneumeasure-operator-webclient%22")        _# Load Balancer_

VITE_PANEU_MEASURE_OPERATOR_WEB_CLIENT_TMMT_TEST_NODE1_URL="[http://lxtkj2ea01:19500/paneumeasure-operator-webclient"](http://lxtkj2ea01:19500/paneumeasure-operator-webclient%22 "http://lxtkj2ea01:19500/paneumeasure-operator-webclient%22") _# Node 1_

VITE_PANEU_MEASURE_OPERATOR_WEB_CLIENT_TMMT_TEST_NODE2_URL="[http://lxtkj2ea02:19500/paneumeasure-operator-webclient"](http://lxtkj2ea02:19500/paneumeasure-operator-webclient%22 "http://lxtkj2ea02:19500/paneumeasure-operator-webclient%22") _# Node 2_

_# Backend_

VITE_PANEU_MEASURE_OPERATOR_BE_SERVICE_TMMT_TEST_URL="[http://measuretermtmmta-be/paneumeasure-operator/"](http://measuretermtmmta-be/paneumeasure-operator/%22 "http://measuretermtmmta-be/paneumeasure-operator/%22")             _# Load Balancer_

VITE_PANEU_MEASURE_OPERATOR_BE_SERVICE_TMMT_TEST_NODE1_URL="[http://lxtkj2ea01:19300/paneumeasure-operator/"](http://lxtkj2ea01:19300/paneumeasure-operator/%22 "http://lxtkj2ea01:19300/paneumeasure-operator/%22")          _# Node 1_

VITE_PANEU_MEASURE_OPERATOR_BE_SERVICE_TMMT_TEST_NODE2_URL="[http://lxtkj2ea02:19300/paneumeasure-operator/"](http://lxtkj2ea02:19300/paneumeasure-operator/%22 "http://lxtkj2ea02:19300/paneumeasure-operator/%22")          _# Node 2_

_## Production Environment_

_# Frontend_

VITE_PANEU_MEASURE_OPERATOR_WEB_CLIENT_TMMT_PROD_URL="[http://measuretermtmmt/paneumeasure-operator-webclient"](http://measuretermtmmt/paneumeasure-operator-webclient%22 "http://measuretermtmmt/paneumeasure-operator-webclient%22")        _# Load Balancer_

VITE_PANEU_MEASURE_OPERATOR_WEB_CLIENT_TMMT_PROD_NODE1_URL="[http://lxtkj2ea01:19500/paneumeasure-operator-webclient"](http://lxtkj2ea01:19500/paneumeasure-operator-webclient%22 "http://lxtkj2ea01:19500/paneumeasure-operator-webclient%22") _# Node 1_

VITE_PANEU_MEASURE_OPERATOR_WEB_CLIENT_TMMT_PROD_NODE2_URL="[http://lxtkj2ea02:19500/paneumeasure-operator-webclient"](http://lxtkj2ea02:19500/paneumeasure-operator-webclient%22 "http://lxtkj2ea02:19500/paneumeasure-operator-webclient%22") _# Node 2_

_# Backend_

VITE_PANEU_MEASURE_OPERATOR_BE_SERVICE_TMMT_PROD_URL="[http://measuretermtmmt-be/paneumeasure-operator/"](http://measuretermtmmt-be/paneumeasure-operator/%22 "http://measuretermtmmt-be/paneumeasure-operator/%22")             _# Load Balancer_

VITE_PANEU_MEASURE_OPERATOR_BE_SERVICE_TMMT_PROD_NODE1_URL="[http://lxtkj2ea01:19300/paneumeasure-operator/"](http://lxtkj2ea01:19300/paneumeasure-operator/%22 "http://lxtkj2ea01:19300/paneumeasure-operator/%22")          _# Node 1_

VITE_PANEU_MEASURE_OPERATOR_BE_SERVICE_TMMT_PROD_NODE2_URL="[http://lxtkj2ea02:19300/paneumeasure-operator/"](http://lxtkj2ea02:19300/paneumeasure-operator/%22 "http://lxtkj2ea02:19300/paneumeasure-operator/%22")          _# Node 2_

_# ==============================================_

_# TMUK Environment_

_# ==============================================_

_### TMUK Admin Service ###_

_## Test Environment_

_# Frontend_

VITE_PANEU_MEASURE_ADMIN_WEB_CLIENT_TMUK_TEST_URL="[http://measureadmintmuka/paneumeasure-admin-webclient"](http://measureadmintmuka/paneumeasure-admin-webclient%22 "http://measureadmintmuka/paneumeasure-admin-webclient%22")        _# Load Balancer_

VITE_PANEU_MEASURE_ADMIN_WEB_CLIENT_TMUK_TEST_NODE1_URL="[http://lxtkj2ea01:19400/paneumeasure-admin-webclient"](http://lxtkj2ea01:19400/paneumeasure-admin-webclient%22 "http://lxtkj2ea01:19400/paneumeasure-admin-webclient%22")  _# Node 1_

VITE_PANEU_MEASURE_ADMIN_WEB_CLIENT_TMUK_TEST_NODE2_URL="[http://lxtkj2ea02:19400/paneumeasure-admin-webclient"](http://lxtkj2ea02:19400/paneumeasure-admin-webclient%22 "http://lxtkj2ea02:19400/paneumeasure-admin-webclient%22")  _# Node 2_

_# Backend_

VITE_PANEU_MEASURE_ADMIN_BE_SERVICE_TMUK_TEST_URL="[http://measureadmintmuka-be/paneumeasure-admin/"](http://measureadmintmuka-be/paneumeasure-admin/%22 "http://measureadmintmuka-be/paneumeasure-admin/%22")             _# Load Balancer_

VITE_PANEU_MEASURE_ADMIN_BE_SERVICE_TMUK_TEST_NODE1_URL="[http://lxtkj2ea01:19000/paneumeasure-admin/"](http://lxtkj2ea01:19000/paneumeasure-admin/%22 "http://lxtkj2ea01:19000/paneumeasure-admin/%22")          _# Node 1_

VITE_PANEU_MEASURE_ADMIN_BE_SERVICE_TMUK_TEST_NODE2_URL="[http://lxtkj2ea02:19000/paneumeasure-admin/"](http://lxtkj2ea02:19000/paneumeasure-admin/%22 "http://lxtkj2ea02:19000/paneumeasure-admin/%22")          _# Node 2_

_## Production Environment_

_# Frontend_

VITE_PANEU_MEASURE_ADMIN_WEB_CLIENT_TMUK_PROD_URL="[http://measureadmintmuk/paneumeasure-admin-webclient"](http://measureadmintmuk/paneumeasure-admin-webclient%22 "http://measureadmintmuk/paneumeasure-admin-webclient%22")        _# Load Balancer_

VITE_PANEU_MEASURE_ADMIN_WEB_CLIENT_TMUK_PROD_NODE1_URL="[http://lxtkj2ea01:19400/paneumeasure-admin-webclient"](http://lxtkj2ea01:19400/paneumeasure-admin-webclient%22 "http://lxtkj2ea01:19400/paneumeasure-admin-webclient%22") _# Node 1_

VITE_PANEU_MEASURE_ADMIN_WEB_CLIENT_TMUK_PROD_NODE2_URL="[http://lxtkj2ea02:19400/paneumeasure-admin-webclient"](http://lxtkj2ea02:19400/paneumeasure-admin-webclient%22 "http://lxtkj2ea02:19400/paneumeasure-admin-webclient%22") _# Node 2_

_# Backend_

VITE_PANEU_MEASURE_ADMIN_BE_SERVICE_TMUK_PROD_URL="[http://measureadmintmuk-be/paneumeasure-admin/"](http://measureadmintmuk-be/paneumeasure-admin/%22 "http://measureadmintmuk-be/paneumeasure-admin/%22")             _# Load Balancer_

VITE_PANEU_MEASURE_ADMIN_BE_SERVICE_TMUK_PROD_NODE1_URL="[http://lxtkj2ea01:19000/paneumeasure-admin/"](http://lxtkj2ea01:19000/paneumeasure-admin/%22 "http://lxtkj2ea01:19000/paneumeasure-admin/%22")          _# Node 1_

VITE_PANEU_MEASURE_ADMIN_BE_SERVICE_TMUK_PROD_NODE2_URL="[http://lxtkj2ea02:19000/paneumeasure-admin/"](http://lxtkj2ea02:19000/paneumeasure-admin/%22 "http://lxtkj2ea02:19000/paneumeasure-admin/%22")          _# Node 2_

_### TMUK Operator Service ###_

_## Test Environment_

_# Frontend_

VITE_PANEU_MEASURE_OPERATOR_WEB_CLIENT_TMUK_TEST_URL="[http://measuretermtmuka/paneumeasure-operator-webclient"](http://measuretermtmuka/paneumeasure-operator-webclient%22 "http://measuretermtmuka/paneumeasure-operator-webclient%22")        _# Load Balancer_

VITE_PANEU_MEASURE_OPERATOR_WEB_CLIENT_TMUK_TEST_NODE1_URL="[http://lxtkj2ea01:19500/paneumeasure-operator-webclient"](http://lxtkj2ea01:19500/paneumeasure-operator-webclient%22 "http://lxtkj2ea01:19500/paneumeasure-operator-webclient%22") _# Node 1_

VITE_PANEU_MEASURE_OPERATOR_WEB_CLIENT_TMUK_TEST_NODE2_URL="[http://lxtkj2ea02:19500/paneumeasure-operator-webclient"](http://lxtkj2ea02:19500/paneumeasure-operator-webclient%22 "http://lxtkj2ea02:19500/paneumeasure-operator-webclient%22") _# Node 2_

_# Backend_

VITE_PANEU_MEASURE_OPERATOR_BE_SERVICE_TMUK_TEST_URL="[http://measuretermtmuka-be/paneumeasure-operator/"](http://measuretermtmuka-be/paneumeasure-operator/%22 "http://measuretermtmuka-be/paneumeasure-operator/%22")             _# Load Balancer_

VITE_PANEU_MEASURE_OPERATOR_BE_SERVICE_TMUK_TEST_NODE1_URL="[http://lxtkj2ea01:19300/paneumeasure-operator/"](http://lxtkj2ea01:19300/paneumeasure-operator/%22 "http://lxtkj2ea01:19300/paneumeasure-operator/%22")          _# Node 1_

VITE_PANEU_MEASURE_OPERATOR_BE_SERVICE_TMUK_TEST_NODE2_URL="[http://lxtkj2ea02:19300/paneumeasure-operator/"](http://lxtkj2ea02:19300/paneumeasure-operator/%22 "http://lxtkj2ea02:19300/paneumeasure-operator/%22")          _# Node 2_

_## Production Environment_

_# Frontend_

VITE_PANEU_MEASURE_OPERATOR_WEB_CLIENT_TMUK_PROD_URL="[http://measureatermtmuk/paneumeasure-operator-webclient"](http://measureatermtmuk/paneumeasure-operator-webclient%22 "http://measureatermtmuk/paneumeasure-operator-webclient%22")        _# Load Balancer_

VITE_PANEU_MEASURE_OPERATOR_WEB_CLIENT_TMUK_PROD_NODE1_URL="[http://lxtkj2ea01:19500/paneumeasure-operator-webclient"](http://lxtkj2ea01:19500/paneumeasure-operator-webclient%22 "http://lxtkj2ea01:19500/paneumeasure-operator-webclient%22") _# Node 1_

VITE_PANEU_MEASURE_OPERATOR_WEB_CLIENT_TMUK_PROD_NODE2_URL="[http://lxtkj2ea02:19500/paneumeasure-operator-webclient"](http://lxtkj2ea02:19500/paneumeasure-operator-webclient%22 "http://lxtkj2ea02:19500/paneumeasure-operator-webclient%22") _# Node 2_

_# Backend_

VITE_PANEU_MEASURE_OPERATOR_BE_SERVICE_TMUK_PROD_URL="[http://measureatermtmuk-be/paneumeasure-operator/"](http://measureatermtmuk-be/paneumeasure-operator/%22 "http://measureatermtmuk-be/paneumeasure-operator/%22")             _# Load Balancer_

VITE_PANEU_MEASURE_OPERATOR_BE_SERVICE_TMUK_PROD_NODE1_URL="[http://lxtkj2ea01:19300/paneumeasure-operator/"](http://lxtkj2ea01:19300/paneumeasure-operator/%22 "http://lxtkj2ea01:19300/paneumeasure-operator/%22")          _# Node 1_

VITE_PANEU_MEASURE_OPERATOR_BE_SERVICE_TMUK_PROD_NODE2_URL="[http://lxtkj2ea02:19300/paneumeasure-operator/"](http://lxtkj2ea02:19300/paneumeasure-operator/%22 "http://lxtkj2ea02:19300/paneumeasure-operator/%22")          _# Node 2_

bağlam menüsü var
```