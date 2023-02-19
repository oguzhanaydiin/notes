## Static Generation

* export async function getStaticProps(context) {...}
Any code you write there never will be seen by clients. This is a server side rendering function. You cant also use client side codes in there like window methods.
