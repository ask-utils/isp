# ASK-Utils - Utility functions for ask-sdk
[![Build Status](https://travis-ci.org/ask-utils/isp.svg?branch=master)](https://travis-ci.org/ask-utils/isp)
[![npm version](https://badge.fury.io/js/@ask-utils/isp.svg)](https://badge.fury.io/js/@ask-utils/isp)
![logo](https://raw.githubusercontent.com/ask-utils/ask-utils/master/docs/img/logo.png)

https://ask-utils.github.io/isp/

## Getting started

```
$ npm i -S @ask-utils/isp
```

## Usage

```typescript

import { getProductByName } from '@ask-utils/isp'

export default = {
  handle() {
    return true
  },
  async handler(handlerInput) {
    const { requestEnvelope, responseBuilder, serviceClientFactory } = handlerInput
    const locale = getLocale(requestEnvelope)
    if (!serviceClientFactory) {
      return responseBuilder.speak('can not call api').getResponse()
    }
    const client = serviceClientFactory.getMonetizationServiceClient()
    const { inSkillProducts } = await client.getInSkillProducts(locale)
    const product = getProductByName(inSkillProducts, 'myProduct')
    return responseBuilder
      .speak(makeParagraphText([
        product.summary,
        'Will you buy the product?'
      ]))
      .getResponse()
  }
}
```

## development

```
$ git clone git@github.com:ask-utils/isp.git
$ cd isp
$ npm i
```

### test

```
$ npm test
```

### Lint

```
$ npm run lint

or

$ npm run lint -- --fix
```

### History
-> [Release Note](https://github.com/ask-utils/isp/releases)


### Contributors

|Name|Version|
|:--|:--|
|[]()||
