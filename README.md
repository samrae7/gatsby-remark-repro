Reprodcction of this issue:  https://github.com/gatsbyjs/gatsby/issues/18312

1. Clone this repo and

    ```shell
    cd gatsby-remark-repro/
    npm install
    gatsby develop
    ```

2.  Go to  _`http://localhost:8000/___graphql`and send the following gql request:


```
query searchDataQuery {
  allMarkdownRemark {
    edges {
      node {
        id
        excerpt(pruneLength: 60, format: MARKDOWN)
      }
    }
  }
}
```

Notice that the excerpt for the md file without the exerpt seperator is returns as empty string. Seeing as the pruneLength works when there is no exerpt seperator option, it seems reasonable that there should to should fall back to the pruneLength.
