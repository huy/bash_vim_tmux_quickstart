## Redux

Redux provides a way to keep/change application state in one single place - single source of true. The application state is managed in a redux `store`. It is can be changed using `reducer` which takes `action` as an argument. In reality we don't call a `reducer` explictly but create a `store` passing all `reducers` to it then we call `dispatch` method of `store`.

`redux-react` is a pattern to use redux with React. It make separation between presenational component and container component.

## Presentational Component

It is a dump React component without any logic and is responsible for visual aspect only. It takes both data and call back from `props`.

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

An invocation of the presentational component can pass additional `props` to it in additional to the one given by `store`.

    const Footer = () => (
      <p>
        Show:
        {" "}
        <FilterLink filter="SHOW_ALL">
          All
        </FilterLink>
        {", "}
        <FilterLink filter="SHOW_ACTIVE">
          Active
        </FilterLink>
        {", "}
        <FilterLink filter="SHOW_COMPLETED">
          Completed
        </FilterLink>
      </p>
    )


## Container

Container component is a React pattern, that separates UI into presentational and container component to encourage reuse of presentational component.

A container is React component created by redux `connect` method

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

There are two methods passed to `connect` the `mapStateToProps` and `mapDispatchToProps`. They in combination provide  both data and callback properties to the presentational component.  The first one selects part of application state from `store`, combines it with `props` argument in a component invocation. The second one takes dispach from `store` does similar for call back properties. 

**References**

* https://medium.com/@learnreact/container-components-c0e67432e005
