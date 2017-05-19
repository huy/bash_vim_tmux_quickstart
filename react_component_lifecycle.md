## React component lifecycle


**lifecycle hooks methods**

In this component method `componentDidMount` and `componentWillUnmount` is called by `ReactDOM.render` wheever it is appropriate.

    class Clock extends React.Component {
      constructor(props) {
        super(props);
        this.state = {date: new Date()};
      }

      componentDidMount() {
        this.timerID = setInterval(
          () => this.tick(),
          1000
        );
      }

      componentWillUnmount() {
        clearInterval(this.timerID);
      }

      tick() {
        this.setState({
          date: new Date()
        });
      }

      render() {
        return (
          <div>
            <h1>Hello, world!</h1>
            <h2>It is {this.state.date.toLocaleTimeString()}.</h2>
          </div>
        );
      }
    }

    ReactDOM.render(
      <Clock />,
      document.getElementById('root')
    );

The `componentDidMount()` hook runs after the component output has been rendered to the DOM. The method `setState` asks React to update a necessary part of DOM.

**state update**

State must be changed by calling `setState` otherwise React will not update DOM, which means screeen will stay the same. Changing state happens asynchronously so if new value depends on the previous one, we need to set it in a call back.

    // Correct
    this.setState((prevState, props) => ({
      counter: prevState.counter + props.increment
    }));
