# react16-with-Routing-Package
# link: https://mmstarz.github.io/react16-with-Routing-Package/
# example of using 'react-router', 'react-router-dom'.
# features used:
{ BrowserRouter, Route, NavLink, Switch, Redirect }

asyncComponent for importing components only when they are needed. without loading them in bundle all the time.

import asyncComponent from '../../hoc/asyncComponent';
const AsyncNewPost = asyncComponent(() => {
    return import('../NewPost/NewPost');
});
