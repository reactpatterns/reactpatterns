# Container component

A container does data fetching and then renders its corresponding sub-component.

Assume that you have a component that displays comments. You didn’t know about container components. So, you put everything in one place.

```
const fetchSomeComments = cb =>
  cb([
    { author: "Bunlong VAN", body: "Nice to see you here!" },
    { author: "You", body: "Thanks!" }
  ]);

class CommentList extends React.Component {
  this.state = { comments: [] };

  componentDidMount() {
    fetchSomeComments(comments => this.setState({ comments: comments }));
  }

  render() {
    return (
      <ul>
        {this.state.comments.map(c => (
          <li>{c.body}—{c.author}</li>
        ))}
      </ul>
    );
  }
}

ReactDOM.render(
  <CommentList />,
  document.getElementById("root")
);
```

Your component is responsible for both fetching data and presenting it. There’s nothing "wrong" with this but you miss out on a few benefits of React.

CommentList can’t be reused unless under the exact same circumstances.

Lets pull out data-fetching into a container component.

```
class CommentListContainer extends React.Component {
  state = { comments: [] };

  componentDidMount() {
    fetchSomeComments(comments =>
      this.setState({ comments: comments }));
  }

  render() {
    return <CommentList comments={this.state.comments} />;
  }
}
```

Now, let’s rework CommentList to take comments as a prop.

```
const CommentList = props =>
  <ul>
    {props.comments.map(c => (
      <li>{c.body}—{c.author}</li>
    ))}
  </ul>
```

What we got:

* Separated our data-fetching and rendering concerns.

* Made our CommentList component reusable.

* Given CommentList the ability to set PropTypes.
