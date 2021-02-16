# CPI Node API's


## Custom Object

In the CPI Node, addons can intercept actions like 'rebuilding' of a custom object, and change the custom objects properties.

``` typescript
const context: DataViewContext = { 
    Name: 'ActivityForm', 
    Object: { 
        Resource: 'activities', 
        Name: 'new activity' 
    }
};
pepperi.customObjects.onRebuild(context, async (customObject: CustomObject) => { 
    for (const field of customObject.Fields) {
        if (field.FieldID === 'TSASomething') {
            // this doesn't set the value in the data object
            // just changes the value the user will see
            field.Value = 'override value'
        }
    }
});
```