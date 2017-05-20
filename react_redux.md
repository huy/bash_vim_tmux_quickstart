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

Container component is a React pattern, that separates UI into presentational and container component to encourage reuse of presentational component. A container does data fetching and then renders its corresponding sub-component. That’s it. It seems to resemble controler in MVC pattern.


**References**

* https://medium.com/@learnreact/container-components-c0e67432e005
