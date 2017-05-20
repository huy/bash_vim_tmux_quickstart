## Redux

Redux provides a way to keep/change application state in one single place - single source of true. The application state is managed in a redux `store`. It is can be changed using `reducer` which takes `action` as an argument. In reality we don't call a `reducer` explictly but create a `store` passing all `reducers` to it then we call `dispatch` method of `store`.

## Container

A container is React component created by redux `connect` method

    const Link = ({ active, children, onClick }) => {
      if (active) {
        return <span>{children}</span>
      }

      return (
        <a href="#"
           onClick={e => {
             e.preventDefault()
             onClick()
           }}
        >
          {children}
        </a>
      )
    }

    const mapStateToProps = (state, ownProps) => {
      return {
        active: ownProps.filter === state.visibilityFilter
      }
    }

    const mapDispatchToProps = (dispatch, ownProps) => {
      return {
        onClick: () => {
          dispatch(setVisibilityFilter(ownProps.filter))
        }
      }
    }

    const FilterLink = connect(
      mapStateToProps,
      mapDispatchToProps
    )(Link)

A container does data fetching, state updating and rendering its corresponding sub-component. It resembles a controler in MVC pattern.
Container component is a React pattern, that separates UI into presentational and container component to encourage reuse of presentational component.

**References**

* https://medium.com/@learnreact/container-components-c0e67432e005
