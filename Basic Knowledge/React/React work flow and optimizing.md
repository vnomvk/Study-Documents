**Online website performance monitoring and get suggestion to optimize app**

    -> https://developers.google.com/speed/pagespeed/insights/?hl=en-US&utm_source=PSI&utm_medium=incoming-link&utm_campaign=PSI
    -> https://gtmetrix.com/


**How Does React Work?**

      Each React application begins with a root component, and is composed of many components in a tree formation. 
    Components in React are “functions” that render the UI based on the data (props and state) it receives.
    
 **Where to Start Optimizing?**
 
      Measuring First - Do not start optimizing code that you feel may be slowing your app down. Instead, let React performance measuring tools guide you through the way.
      Note : one of rule from rob pike - "Measure. Don’t tune for speed until you’ve measured, and even then don’t unless one part of the code overwhelms the rest."
      
      powerful tool : react-addons-perf 
      The usage is very simple:
        Import Perf from 'react-addons-perf'
        Perf.start();
        Perf.stop();
        Perf.printWasted();
       Ex of o/p : https://uploads.toptal.io/blog/image/123160/toptal-blog-image-1495787031644-adcf932605396cf8d9f7cf3325fdadc2.jpg
 
**Should React Update The Component?**

        By default, React will run, render the virtual DOM, and compare the difference for every component in the tree for any change in its props or state. But that is obviously not reasonable.
        As your app grows, attempting to re-render and compare the entire virtual DOM at every action will eventually slow down.
        
        This gives the you a simple way of controlling the render-diff process. Whenever you need to prevent a component from being re-rendered at all, simply return false from the function. Inside the function, you can compare the current and next set of props and state to determine whether a re-render is necessary. EX: 
        
        function shouldComponentUpdate(nextProps, nextState) {
          return nextProps.id !== this.props.id;
        }
        
**Making Data Immutable**


    What if you could use a React.PureComponent but still have an efficient way of telling when any complex props or states have changed automatically? This is where immutable data structures make life easier.

    The idea behind using immutable data structures is simple. Whenever an object containing complex data changes, instead of making the changes in that object, create a copy of that object with the changes. This makes detecting changes in data as simple as comparing the reference of the two objects.

    You can use Object.assign or _.extend (from Underscore.js or Lodash):

    const newValue2 = Object.assign({}, oldValue);
    const newValue2 = _.extend({}, oldValue);
    Even better, you can use a library that provides immutable data structures:

    var map1 = Immutable.Map({a:1, b:2, c:3});
    var map2 = map1.set('b', 2);
    assert(map1.equals(map2) === true);
    var map3 = map1.set('b', 50);
    assert(map1.equals(map3) === false);
    Here, Immutable.Map is provided by the library Immutable.js.

    Every time a map is updated with its method set, a new map is returned only if the set operation changed the underlying value. Otherwise, the same map is returned.

    You can learn more about using immutable data structures here.
    -> http://facebook.github.io/immutable-js/docs/#/
    -> https://www.toptal.com/javascript/immutability-in-javascript-using-redux
    
**Reference**
    1.https://www.toptal.com/react/optimizing-react-performance
    
    
