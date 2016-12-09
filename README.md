# react-currency-input

An es6 react component for currency.  Supports custom decimal and thousand separators as well as precision.


## Installation
```
npm install react-currency-input --save
```



## Integration
You can store the value passed in to the change handler in your state.

```javascript
import React from 'react'
import CurrencyInput from 'react-currency-input';

const MyApp = React.createClass({
    getInitialState(){
        return ({amount: "0.00"});
    },
  
    handleChange(newValue){
        this.setState({amount: newValue});
    }
    render() {
        return (
            <div>
                <CurrencyInput value={this.state.amount} onChange={this.handleChange}/>
            </div>
        );
    }
}
export default MyApp
```


You can also assign a reference then access the value using a call to getMaskedValue()

```javascript
import React from 'react'
import CurrencyInput from 'react-currency-input';

const MyApp = React.createClass({
    handleSubmit(event){
        event.preventDefault();
        console.log(this.refs.myinput.getMaskedValue())
    }
    render() {
        return (
            <form onSubmit={this.handleSubmit}>
                <CurrencyInput ref="myinput" />
            </form>
        );
    }
}
export default MyApp
```



## Separators and Precision


Specify custom decimal and thousand separators:
```javascript
    // 1.234.567,89
    <CurrencyInput decimalSeparator="," thousandSeparator="." />
```

Specify a specific precision:
```javascript
    // 123,456.789
    <CurrencyInput precision="3" />
```

```javascript
    // 123,456,789
    <CurrencyInput precision="0" />
```


## Currency

Optionally set a currency symbol as a prefix or suffix
```javascript
    // $1,234,567.89
    <CurrencyInput prefix="$" />
```

```javascript
    // 1,234,567.89 kr
    <CurrencyInput suffix=" kr" />
```



All other attributes are applied to the input element.  For example, you can integrate bootstrap styling:

```javascript
    <CurrencyInput className="form-control" />
```



## Options


| Option            | Default Value | Description          |
| -------------     | -----------   | -----------           |
| value             | 0             | The initial currency value |
| onChange          | n/a           | Callback function to handle value changes |
| precision         | 2             | Number of digits after the decimal separator |
| decimalSeparator  | '.'           | The decimal separator |
| thousandSeparator | ','           | The thousand separator |
| inputType         | "text"        | Input field tag type. You may want to use `number` or `tel` |
| allowNegative     | false         | Allows negative numbers in the input |
| prefix            | ''            | Currency prefix |
| suffix            | ''            | Currency suffix |


