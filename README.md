# How to Add json-dynamic-form library to existing angular project

 - do `npm i "https://github.com/sasivardhan518/lib/raw/main/json-dynamic-form-0.0.1.tgz"` in angular project where you want to use the library.
 - Library is having following peer dependecies:
	 - "@angular/common": "^12.2.0"
	 - "@angular/core": "^12.2.0"
	 - "@angular/material": "^12.2.11"
	 - "@angular/cdk": "^12.2.11"
	 - "lodash": "^4.17.21"
	 - "@fortawesome/fontawesome-free": "^5.15.4"
	 - "bootstrap": "^5.1.3"
 - Make sure all the above libraries are added in your projects "**package.json**" file.
 - After adding all the dependencies do `npm i or npm install` on project to download all the added dependecies.
 - Once all the dependencies are installed you are good to use the library

# How to use json-dynamic-form library in code

 - After adding the library to angular project, import the JsonDynamicFormModule in angular project modules where you want to use json-dynamic-form.
 - 	    import { NgModule } from '@angular/core';
    	import { BrowserModule } from '@angular/platform-browser';
    	import { JsonDynamicFormModule } from 'json-dynamic-form';
    	import { AppRoutingModule } from './app-routing.module';
    	import { AppComponent } from './app.component';
    	@NgModule({
    	  declarations: [
    	    AppComponent
    	  ],
    	  imports: [
    	    BrowserModule,
    	    AppRoutingModule,
    	    JsonDynamicFormModule
    	  ],
    	  providers: [],
    	  bootstrap: [AppComponent]
    	})
    	export class AppModule { }
 - Now add below lines in ***styles .scss*** file of yopur angular project
	 - @import  '~@angular/material/prebuilt-themes/indigo-pink.css';
	 - @import  '~bootstrap/dist/css/bootstrap.min.css';
	 - @import  "~@fortawesome/fontawesome-free/css/all.min.css";

		> Above imports are needed in order to render the styles of components in library  

 - Now add `<app-json-dynamic-form></app-json-dynamic-form>` in the component of your angular project.
 - `<app-json-dynamic-form  [uiConfig]="uiConfig"></app-json-dynamic-form>`
 - Sample ui config:
	 - 

>     uiConfig = {
>         "config": [
>           {
>             "property": "DEFAULT_HIERARCHY_LEVELS",
>             "displayText": "",
>             "section": "DHL",
>             "parentValidators": {
>               "maxlength": 2
>             },
>             "children": [
>               {
>                 "property": "pricing_segment",
>                 "displayText": "Pricing Segment",
>                 "uiControlType": "dropdown",
>                 "source": "list",
>                 "values": ["country_group", "product_hier3", "product_hier2", "product_hier1"],
>                 "isMultiSelect": true,
>                 "isDependentControl": true,
>                 "condition": {
>                   "REGRESSION_PARAMS.ndx": 2
>                 },
>                 "validators": {
>                   "required": true
>                 },
>                 "errorMessages": {
>                   "required": "Pricing segment is required."
>                 }
>               },
>               {
>                 "property": "L3",
>                 "displayText": "L3",
>                 "uiControlType": "text  ",
>                 "parentValidators": {
>                   "required": true,
>                   "minlength": 2,
>                   "maxlength": 3
>                 },
>                 "parentErrorMessages": {
>                   "required": "Must have atleast 2 values.",
>                   "minlength": "Must have atleast 2 values.",
>                   "maxlength": "Cannot have more than 3 values."
>                 }
>               },
>               {
>                 "property": "L2",
>                 "displayText": "L2",
>                 "source": "list",
>                 "values": ["country_group", "product_hier3", "product_hier2", "product_hier1"],
>                 "uiControlType": "dropdown"
>               },
>               {
>                 "property": "L1",
>                 "displayText": "L1",
>                 "uiControlType": "dropdown"
>               }
>             ]
>           },
>           {
>             "property": "JOIN_COL",
>             "displayText": "Join Cols",
>             "uiControlType": "dropdown"
>           },
>           {
>             "property": "USE_PUBLISH_AS_REFERENCE",
>             "displayText": "Use Publish as Reference",
>             "uiControlType": "checkbox"
>           },
>           {
>             "property": "LADDER_ACROSS_SEGMENTS_CENTER_ADJUST",
>             "displayText": "Ladder across segments center adjust",
>             "uiControlType": "checkbox"
>           },
>           {
>             "property": "MIN_BAND_WIDTH_CENTER_ADJUST",
>             "displayText": "Min band width center adjust",
>             "uiControlType": "checkbox"
>           },
>           {
>             "property": "IS_CAPPING_BAND",
>             "displayText": "Is capping band",
>             "uiControlType": "checkbox",
>             "defaultValue": true
>           },
>           {
>             "property": "REGRESSION_PARAMS",
>             "section": "Regression Params",
>             "children": [
>               {
>                 "property": "ndx",
>                 "displayText": "NDX",
>                 "uiControlType": "number",
>                 "validators": {
>                   "max": 5,
>                   "min": 2,
>                   "required": true
>                 },
>                 "errorMessages": {
>                   "max": "Cannot be greater than 5",
>                   "min": "Cannot be less than 2",
>                   "required": "ndx param is required."
>                 },
>                 "defaultValue": 2
>               },
>               {
>                 "property": "deg",
>                 "displayText": "Degree",
>                 "uiControlType": "number",
>                 "validators": {
>                   "required": true
>                 }
>               },
>               {
>                 "property": "lambda_value",
>                 "displayText": "Lambda Value",
>                 "uiControlType": "number",
>                 "validators": {
>                   "required": true
>                 }
>               },
>               {
>                 "property": "beta",
>                 "displayText": "Beta",
>                 "uiControlType": "number",
>                 "validators": {
>                   "required": true
>                 }
>               },
>               {
>                 "property": "small_value",
>                 "displayText": "Small Value",
>                 "uiControlType": "number",
>                 "validators": {
>                   "required": true
>                 }
>               },
>               {
>                 "property": "max_iterations",
>                 "displayText": "Max Iterations",
>                 "uiControlType": "number",
>                 "validators": {
>                   "required": true,
>                   "min": 0,
>                   "max": 50
>                 }
>               },
>               {
>                 "property": "kappa",
>                 "displayText": "Kappa",
>                 "uiControlType": "number",
>                 "validators": {
>                   "required": true
>                 }
>               },
>               {
>                 "property": "bound_value",
>                 "displayText": "Bound Value",
>                 "uiControlType": "number",
>                 "validators": {
>                   "required": true,
>                   "regex": "^[0-5][0-2]?$"
>                 }
>               }
>             ]
>           },
>           {
>             "property": "SPARSITY_CONFIG",
>             "section": "Sparsity Config",
>             "children": [
>               {
>                 "property": "min_num_price_points",
>                 "displayText": "Min. No. Price Points",
>                 "uiControlType": "textarea",
>                 "validators": {
>                   "required": true
>                 }
>               },
>               {
>                 "property": "min_num_segments",
>                 "displayText": "Min. No. Segments",
>                 "uiControlType": "number",
>                 "validators": {
>                   "required": true
>                 }
>               },
>               {
>                 "property": "min_num_transactions",
>                 "displayText": "Min. No. Transactions",
>                 "uiControlType": "number",
>                 "validators": {
>                   "required": true
>                 }
>               }
>             ]
>           },
>           {
>             "property": "csvData",
>             "displayText": "CSV Data",
>             "uiControlType": "csv",
>             "section": "CSV",
>             "csvConfig": {
>               "isEditable": true,
>               "fixedColumns": ["id"],
>               "columnControls": {
>                 "body": {
>                   "property": "body",
>                   "displayText": "Lw2",
>                   "uiControlType": "text",
>                   "validators": {
>                     "required": true
>                   }
>                 },
>                 "email": {
>                   "property": "email",
>                   "uiControlType": "text",
>                   "validators": {
>                     "required": true,
>                     "maxlength": 50
>                   },
>                   "errorMessages": {
>                     "maxlength": "Cannot have > 50 chars"
>                   }
>                 }
>               },
>               "paramControls": {
>                 "config": [
>                   {
>                     "property": "min_num_price_points",
>                     "displayText": "Min. No. Price Points",
>                     "uiControlType": "number",
>                     "validators": {
>                     }
>                   },
>                   {
>                     "property": "min_num_segments",
>                     "displayText": "Min. No. Segments",
>                     "uiControlType": "number",
>                     "validators": {
>                     }
>                   },
>                   {
>                     "property": "L22",
>                     "displayText": "L22",
>                     "source": "url",
>                     "valuesUrl": "https://jsonplaceholder.typicode.com/posts",
>                     "uiControlType": "dropdown",
>                     "dropdownID": "id",
>                     "dropdownLabel": "title",
>                     "valuesToAdd": [
>                       {
>                         "id": "22",
>                         "title": "Custom Value"
>                       }
>                     ]
>                   },
>                   {
>                     "property": "id",
>                     "displayText": "ID",
>                     "source": "list",
>                     "uiControlType": "dropdown",
>                     "values": [1, 2, 3, 4, 5, 1008],
>                     "validators": {
>                       "required": true
>                     }
>                   }
>                 ],
>                 "sectionsOrder": []
>               },
>               "uploadURL": "https://jsonplaceholder.typicode.com/posts/{{id}}/comments",
>               "downloadURL": "https://jsonplaceholder.typicode.com/posts/{{id}}/comments"
>             }
>           }
>         ],
>         "sectionsOrder": ["DHL", "Regression Params"],
>         "sectionsDisplayLabelMap": {
>           "DHL": "Default Hierarchy Levels"
>         }
>       };
