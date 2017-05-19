## State vs props

**state vs props**

Props which is passed when instantiating component is immutable. State on the other hand is mutable. State is reserved only for interactivity, that is, data that changes over time.

    const scaleNames = {
      c: 'Celsius',
      f: 'Fahrenheit'
    };

    class TemperatureInput extends React.Component {
      constructor(props) {
        super(props);
        this.handleChange = this.handleChange.bind(this);
      }

      handleChange(e) {
        this.props.onTemperatureChange(e.target.value);
      }

      render() {
        const temperature = this.props.temperature;
        const scale = this.props.scale;
        return (
          <fieldset>
            <legend>Enter temperature in {scaleNames[scale]}:</legend>
            <input value={temperature}
                   onChange={this.handleChange} />
          </fieldset>
        );
      }
    }

    class Calculator extends React.Component {
      constructor(props) {
        super(props);
        this.handleCelsiusChange = this.handleCelsiusChange.bind(this);
        this.handleFahrenheitChange = this.handleFahrenheitChange.bind(this);
        this.state = {temperature: '', scale: 'c'};
      }

      handleCelsiusChange(temperature) {
        this.setState({scale: 'c', temperature});
      }

      handleFahrenheitChange(temperature) {
        this.setState({scale: 'f', temperature});
      }

      render() {
        const scale = this.state.scale;
        const temperature = this.state.temperature;
        const celsius = scale === 'f' ? tryConvert(temperature, toCelsius) : temperature;
        const fahrenheit = scale === 'c' ? tryConvert(temperature, toFahrenheit) : temperature;

        return (
          <div>
            <TemperatureInput
              scale="c"
              temperature={celsius}
              onTemperatureChange={this.handleCelsiusChange} />
            <TemperatureInput
              scale="f"
              temperature={fahrenheit}
              onTemperatureChange={this.handleFahrenheitChange} />
            <BoilingVerdict
              celsius={parseFloat(celsius)} />
          </div>
        );
      }
    }


**state update**

State must be changed by calling `setState` otherwise React will not update DOM, which means screeen will stay the same. Changing state happens asynchronously so if new value depends on the previous one, we need to set it in a call back.

    // Correct
    this.setState((prevState, props) => ({
      counter: prevState.counter + props.increment
    }));
