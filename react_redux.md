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
