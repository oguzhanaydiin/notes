## Static Generation

* export async function getStaticProps(context) {...}
Any code you write there never will be seen by clients. This is a server side rendering function. You cant also use client side codes in there like window methods.


//you should return a props key in the object returned by getStaticProps

// code iini getStaticProps can do server side things like fetch data from an API
// and return it as props
// getStaticProps runs at build time

// fs module is a server side node module
// it allows us to read files from the file system
// browser side cant access the file system
// so we need to use getStaticProps to read the file system

//--------------------------------------------------------------
// Incremental static generation
// if you have a page that has a lot of data
// you can use incremental static generation
// it will generate the page at build time
// and then generate the page again when a request comes in

// in getStaticProps, you can return a revalidate key
// revalidate is the number of seconds after which a new version of the page should be generated
// if you return revalidate: 10, then the page will be regenerated every 10 seconds

//  export async function getStaticProps() {
//    return {
//      props: {
//        products: data.products,
//      },
//     revalidate: 10,
//    }
//  }

//--------------------------------------------------------------
// getStaticPaths is required to say next js which paths should be pre rendered
// if you dont use getStaticPaths, next js will pre render all paths
// if you use getStaticPaths, next js will only pre render the paths you specify


// difference between getStaticProps and getServerSideProps
// getStaticProps is executed during the build process
// getServerSideProps is executed on every request
// getStaticProps is better for SEO
// getServerSideProps is better for dynamic content
// SEO is search engine optimization



  return {
    props: {
      //get 404 page if product is undefined
      loadedProduct: product,
    },
  }
}

//context in getStaticProps is an object
// it has a params key
// params is an object that contains all dynamic segments
// in this case, params is { pid: 'p1' }

export async function getStaticPaths() {
  const data = await getData()
  const ids = data.products.map((product: any) => product.id)
  const params = ids.map((id: any) => ({ params: { pid: id } }))


-----------------------------------------------------------------

  return {
    paths: params,
    fallback: true,
  }


// fallback is a boolean
// if fallback is false, then next js will return a 404 page if the path is not defined in getStaticPaths
// if fallback is true, then next js will try to generate the page on the fly
// if fallback is blocking, then next js will try to generate the page on the fly
// and will wait until the page is generated to return the response to the client



