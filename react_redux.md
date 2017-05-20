## Container

A container is React component created by redux `connect` method

    import { connect } from 'react-redux'

    const VisibleTodoList = connect(
      mapStateToProps,
      mapDispatchToProps
    )(TodoList)

    export default VisibleTodoList
