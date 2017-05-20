## Container

A container is React component created by redux `connect` method

    import { connect } from 'react-redux'

    const VisibleTodoList = connect(
      mapStateToProps,
      mapDispatchToProps
    )(TodoList)

    export default VisibleTodoList


**References**

* https://medium.com/@learnreact/container-components-c0e67432e005
