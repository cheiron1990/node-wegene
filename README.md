# node-wegene

Node.js SDK for [WeGene](https://www.wegene.com)

## Installation

    $ npm install node-wegene

## Usage

#### Set Access Token

To query data from WeGene, one need a valid OAuth2 access token authorized by
the user. Node.js Express apps can use `passport-wegene` for implementing the
OAuth2 flow.


```javascript
var wegene = require('node-wegene');
var config = wegene.configuration;
config.oAuthAccessToken = '<A Valid Access Token With Proper Scope>';
```

#### Get Basic User Info

Use `wegene.User.getUser()` to get user data

```javascript
var user = wegene.User
user.getUser(function(error, result){
  if(error){ return console.log(error) }
  console.log('User Info:\n', JSON.stringify(result));
});
```

#### Get Gene Allele Info

Use `wegene.Allele.getAllele(profile_id, callback)` to get allele data

```javascript
var allele = wegene.Allele;
allele.getAllele(profile_id, ['rs182549'], function(error, result){
  if(error){ return console.log(error) }
  console.log('Allele Data:\n', JSON.stringify(result));
});
```

#### Get Sport Advice

Use `wegene.Sport.getAdvice(profileId, sex, age, height, weight, healthTarget, callback)` to get sport advice

```javascript
var sport = wegene.Sport;
sport.getAdvice(profile_id, 'male', 26, 174, 84, 'slimming', function(error, result){
  if(error){ return console.log(error) }
  console.log('Sport Advice:\n', JSON.stringify(result));
});
```

#### Get Health Data

Use `wegene.Health.getRisk(profileId, reportId, callback)` to get health risk info

Use `wegene.Health.getDrug(profileId, reportId, callback)` to get drug response info

Use `wegene.Health.getCarrier(profileId, reportId, callback)` to get disease carrier info

```javascript
var health = wegene.Health;
health.getDrug(profile_id, 158,function(error, result){
  if(error){ return console.log(error) }
  console.log('Health Data:\n', JSON.stringify(result));
});
```

## Documentation
  - [Full WeGene API Document](https://api.wegene.com/docs/)


## Credits
  - [Eddie Wu](https://xraywu.github.io)

## Thanks
  - The SDK is modified on top of the code auto-generated using [APIMATIC](https://apimatic.io). Huge thanks to the team as this is a real life saver!!

## License

(The MIT License)

Copyright (c) 2016 Eddie Wu

Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the "Software"), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.
