## Element vs Component

In React an elemnent is created by a JSX expression

    const element = <h1>Hello, world!</h1>;
    
JSX is kind of template, which can be rendered into a DOM tree element by `ReactDOM.render`

    function formatName(user) {
      return user.firstName + ' ' + user.lastName;
    }

    const user = {
      firstName: 'Harper',
      lastName: 'Perez'
    };

    const element = (
      <h1>
        Hello, {formatName(user)}!
      </h1>
    );

    ReactDOM.render(
      element,
      document.getElementById('root')
    );
    
A component is javascript function that take one argument called `props` and return a React element

    function Welcome(props) {
      return <h1>Hello, {props.name}</h1>;
    }

A component can be created by extending `React.Component`, which offers fine grain way to customize a component

    class Welcome extends React.Component {
      render() {
        return <h1>Hello, {this.props.name}</h1>;
      }
    }
    
A element can refer to components making a recursive structure

    const element = <Welcome name="Sara" />;
    ReactDOM.render(
      element,
      document.getElementById('root')
    );

A component must be pure function, no modification of `props` is allowed.
