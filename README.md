# Vue Segmented-Control
Segmented control for Vue.js

![Vue Segmented Control visual](https://raw.githubusercontent.com/Pandazaur/vue-segmented-control/master/exemple.png)

## Demo

[![Demo on codesandbox.io](https://codesandbox.io/static/img/play-codesandbox.svg)](https://codesandbox.io/s/n4nxjwz17j)

## Installation

```
npm install vue-segmented-control
```

## Usage

```html
<template>
    <segmented-control
        :options="options"
        label="label"
        value="value"
        color="#fff"
        active-color="#333"
        :multiple="false"
        @select="onSelect"
        :defaultSelected="{value:'val',label:'label'}"
    />
</template>
```
```javascript
import SegmentedControl from 'vue-segmented-control'

export default {
    components: {
        SegmentedControl
    },
    data () {
        return {
            options: [
                { label: 'Red', value: 'red' },
                { label: 'Blue', value: 'blue' },
                { label: 'Green', value: 'green' }
            ]
        }
    },
    methods: {
        onSelect(optionsSelected) {
            // optionSelected: [{ label: '__', value: '__', ... }]
        }
    }
}
```

## Documentation

Props:

| Property | Type | Default | Description | Required |
| ----------- | ----------- | ----------- | ----------- | ----------- |
| options | Array(Object) |  | Items selectables | true
| label   | String | 'label' | Property that define the label |  |
| value   | String | 'value' | Property that define the value (should be unique) |  |
| color   | String | '#fff' | Text color |  |
| activeColor   | String | '#000' | Background color of the selected items | |
| multiple   | Boolean | false | Set to `true` to enable multiple selection | | |
