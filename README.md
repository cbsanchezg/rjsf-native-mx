# [react-json-schema-form](https://github.com/rjsf-team/react-jsonschema-form) themed for react-native

## Getting Started

```bash
yarn add @rjsf/core rjsf-native

# This package also depends on `@react-native-community/slider`
yarn add @react-native-community/slider
```

## Usage
```typescript
import ReactNativeForm from 'rjsf-native';

const App = () => {
  const form = useRef(null);
  return (
    <ReactNativeForm
      ref={form}
      onError={e => {
        console.log(e);
        Alert.alert('Please check your form');
      }}
      schema={schema}
      uiSchema={uiSchema}
      onSubmit={form => console.log(form.formData)}>
      <Button
        title="Submit"
        onPress={() => {
          form.current?.submit();
        }}
      />
    </ReactNativeForm>
  );
};
```

We also provide a Context as a form of overriding defaults and theming

```typescript
import ReactNativeForm, {defaultProps, FormContext} from 'rjsf-native';

const App = () => {
  const form = useRef(null)
  return (
    <FormContext value={{...defaultProps, requiredTitle: '*'}}>
        <ReactNativeForm .../>
    </FormContext>
  )
}
```

### Form Context Props
```typescript
{
  theme: {
    primaryColor: string; // Your main theme color. Used for e.g. buttons
    highlightColor: string; // Used for focused inputs, checked checkboxes, slider...
    borderColor: string; // Color of textinput borders
    textColor: string;
    placeholderTextColor: string;
    errorColor: string;
    [propName: string]: any;
  };
  requiredTitle: string;
  arrayAddTitle: string;
  radioLabelMapping?: (label: string) => string;
  [propName: string]: any;
}
```

## Development
1. Run ```npm start``` in root folder to run the dev server
2. ```cd example && npm run android``` to start the example app



