# react16-with-Routing-Package

# link: https://mmstarz.github.io/react16-with-Routing-Package/

# example of using 'react-router', 'react-router-dom'.

# features used:
  { BrowserRouter, Route, NavLink, Switch, Redirect }
  
 # <BrowserRouter >        
 #    <div className="App">
 #       <Blog />
 #    </div>
 # </BrowserRouter>
   ...
  
  <li>
    <NavLink to="/posts/" exact
      activeClassName="my-active"
      activeStyle={{
       color: '#fa923f',
       textDecoration: 'underline',
       }}>Posts</NavLink>
  </li>
      
  <li><NavLink to={{
    pathname: '/new-post',
    hash: '#submit',
    search: '?quick-submit=true',
    }}>New-Post</NavLink>
  </li>
  ...
  
  <div>                
     <section className="Posts">
       {posts}
     </section>
     <Route path={this.props.match.url + '/:id'} exact component={FullPost} />
  </div>
  ...
  
  {/* exact checks path and tells react to render jsx if URL path is true or false 
      <Route path="/" exact render={() => <h1>Home</h1>} />
      without exact Route will force react to render jsx for every URL that starts with '/'
      <Route path="/" render={() => <h1>Home 2</h1>} /> 
      component is a reference to a class have to render 
      <Route path="/" exact component={Posts} /> */}
  {/* Switch tells to react ot render only the first matched path Route */}                
  <Switch>
        {/* one way of using guard redirection */}                  
        {this.state.authenticated ? <Route path="/new-post" component={AsyncNewPost} /> : null}
        <Route path="/posts" component={Posts} />                    
        {/* Redirect not rendering jsx it only changes the url */}                    
        <Redirect from="/" to="/posts" />
        {/* catch all unknown routs and return jsx */}
        <Route render={() => <h1 style={{textAlign: 'center'}}>404 error handler</h1>}/>
        {/*<Route path="/" component={Posts} />*/}                    
  </Switch>
  ...
  
  asyncComponent for importing components only when they are needed.
  without loading them in bundle all the time.
  
     import asyncComponent from '../../hoc/asyncComponent';
     const AsyncNewPost = asyncComponent(() => {
        return import('../NewPost/NewPost');
     });
