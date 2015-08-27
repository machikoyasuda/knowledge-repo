var React = require('react');

var Filter = React.createClass({
  render: function(){
    return (
      <form onChange={this.props.changeFilter.bind(null, changedState)} > 
        //Not sure exactly how this would work, but you get the idea.
        //stuff here
      </form>
    )
  }
});

var Product = React.createClass({
  render: function(){
    return(
      <div>
        <h1>{this.props.name}</h1>
        //other stuff
      </div>
    )
  }
})

var Container = React.createClass({
  getInitialState: function() {
    return {
      filter: {},
      products: [] 
    };
  },
  componentDidMount: function() {
    getSomeData().then(function(results){
      this.setState({
        products: results
      })
    })
  },
  changeFilter: function(newFilter){
    // AJAX request
    this.setState({
      filter: newFilter
    })
  },
  render: function(){
    var productsToRender = this.state.products.filter(function(item, index){
      //Do some stuff to filter out products here
    });
    var Products = productsToRender.map(function(item, index){
      return (
        <Product name={item.name} price={item.price} size={item.size} picture={item.picture} />
      )
    });
    return (
      <div>
        <Filter changeFilter={this.changeFilter} filter={this.state.filter} />
        {Products}
      </div>
    )
  }  
})