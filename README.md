# angular-signature-pad-v2
Angular 14+ component for [szimek/signature_pad](https://www.npmjs.com/package/signature_pad).

# Get the right version
- Angular 14/ CLI 14: angular-signature-pad-v2@^5.0.0
- Angular 15/ CLI 15: angular-signature-pad-v2@^6.0.0
- Angular 16/ CLI 16: angular-signature-pad-v2@^7.0.0
- Angular 17/ CLI 17: angular-signature-pad-v2@^8.0.0
- Angular 18/ CLI 18: angular-signature-pad-v2@^9.0.0

# Maintenance
- update only major version of angular  

## Install
`npm install angular-signature-pad-v2@9.0.0 --save`

## Reference Implementation

* [Live Demo](http://lathonez.com/angular2-signaturepad-demo/)
* [Demo Project](https://github.com/aditya-singh-07/signature-test)
* [Source](https://github.com/lathonez/angular2-signaturepad-demo)

## Usage example

API is identical to [szimek/signature_pad](https://www.npmjs.com/package/signature_pad).

Options are as per [szimek/signature_pad](https://www.npmjs.com/package/signature_pad) with the following additions:
* canvasWidth: width of the canvas (px)
* canvasHeight: height of the canvas (px)
The above options are provided to avoid accessing the DOM directly from your component to adjust the canvas size.

```typescript

// import into app module

import { SignaturePadModule } from 'angular-signature-pad-v2';

...

@NgModule({
  declarations: [ ],
  imports: [ SignaturePadModule ],
  providers: [ ],
  bootstrap: [ AppComponent ]
})

// then import for use in a component

import { Component, ViewChild } from 'angular2/core';
import { SignaturePad } from 'angular-signature-pad-v2';

@Component({
  template: '<signature-pad [options]="signaturePadOptions" (onBeginEvent)="drawStart()" (onEndEvent)="drawComplete()"></signature-pad>'
})

export class SignaturePadPage{

  @ViewChild(SignaturePad) signaturePad: SignaturePad;

  private signaturePadOptions: Object = { // passed through to szimek/signature_pad constructor
    'minWidth': 5,
    'canvasWidth': 500,
    'canvasHeight': 300
  };

  constructor() {
    // no-op
  }

  ngAfterViewInit() {
    // this.signaturePad is now available
    this.signaturePad.set('minWidth', 5); // set szimek/signature_pad options at runtime
    this.signaturePad.clear(); // invoke functions from szimek/signature_pad API
  }

  drawComplete() {
    // will be notified of szimek/signature_pad's onEnd event
    console.log(this.signaturePad.toDataURL());
  }

  drawStart() {
    // will be notified of szimek/signature_pad's onBegin event
    console.log('begin drawing');
  }
}
```
# Credit 

Special thanks to : 
- szimzk
- wulfsolte
- Aditya Singh
- Antoine Delahaye
