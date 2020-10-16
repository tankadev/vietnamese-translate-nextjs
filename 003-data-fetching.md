###### Ngày cập nhật: 16/10/2020
# Data fetching

>Tài liệu này được viết ra cho Next.js từ phiên bản 9.3 trở lên. Nếu bạn đang sử dụng những phiên bản Next.js cũ hơn, hãy tham khảo [tài liệu này](https://nextjs.org/docs/tag/v9.2.2/basic-features/pages).

<details open>
  <summary><b>Examples</b></summary>
  <ul>
    <li><a href="https://github.com/vercel/next.js/tree/canary/examples/cms-wordpress">WordPress Example</a> (<a href="https://next-blog-wordpress.now.sh">Demo</a>)</li>
    <li><a href="https://github.com/vercel/next.js/tree/canary/examples/blog-starter">Blog Starter using markdown files</a> (<a href="https://next-blog-starter.now.sh/">Demo</a>)</li>
    <li><a href="https://github.com/vercel/next.js/tree/canary/examples/cms-datocms">DatoCMS Example</a> (<a href="https://next-blog-datocms.now.sh/">Demo</a>)</li>
    <li><a href="https://github.com/vercel/next.js/tree/canary/examples/cms-takeshape">TakeShape Example</a> (<a href="https://next-blog-takeshape.now.sh/">Demo</a>)</li>
    <li><a href="https://github.com/vercel/next.js/tree/canary/examples/cms-sanity">Sanity Example</a> (<a href="https://next-blog-sanity.now.sh/">Demo</a>)</li>
    <li><a href="https://github.com/vercel/next.js/tree/canary/examples/cms-prismic">Prismic Example</a> (<a href="https://next-blog-prismic.now.sh/">Demo</a>)</li>
    <li><a href="https://github.com/vercel/next.js/tree/canary/examples/cms-contentful">Contentful Example</a> (<a href="https://next-blog-contentful.now.sh/">Demo</a>)</li>
    <li><a href="https://github.com/vercel/next.js/tree/canary/examples/cms-strapi">Strapi Example</a> (<a href="https://next-blog-strapi.now.sh/">Demo</a>)</li>
    <li><a href="https://github.com/vercel/next.js/tree/canary/examples/cms-agilitycms">Agility CMS Example</a> (<a href="https://next-blog-agilitycms.now.sh/">Demo</a>)</li>
    <li><a href="https://github.com/vercel/next.js/tree/canary/examples/cms-cosmic">Cosmic Example</a> (<a href="https://next-blog-cosmic.now.sh/">Demo</a>)</li>
    <li><a href="https://github.com/vercel/next.js/tree/canary/examples/cms-buttercms">ButterCMS Example</a> (<a href="https://next-blog-buttercms.now.sh/">Demo</a>)</li>
    <li><a href="https://github.com/vercel/next.js/tree/canary/examples/cms-storyblok">Storyblok Example</a> (<a href="https://next-blog-storyblok.now.sh/">Demo</a>)</li>
    <li><a href="https://github.com/vercel/next.js/tree/canary/examples/cms-graphcms">GraphCMS Example</a> (<a href="https://next-blog-graphcms.now.sh/">Demo</a>)</li>
    <li><a href="https://github.com/vercel/next.js/tree/canary/examples/cms-kontent">Kontent Example</a> (<a href="https://next-blog-kontent.vercel.app/">Demo</a>)</li>
    <li><a href="https://static-tweet.now.sh/">Static Tweet Demo</a></li>
  </ul>
</details>

Trong tài liệu [Pages](https://github.com/vercel/next.js/blob/canary/docs/basic-features/pages.md), chúng tôi đã giải thích rằng Next.js có hai hình thức của pre-rendering: **Static Generation** và **Server-side Rendering**. Trong tài liệu này, chúng ta sẽ tìm hiểu sâu hơn về cách lấy dữ liệu cho mỗi trường hợp. Chúng tôi khuyên bạn nên đọc qua tài liệu [Pages](https://github.com/vercel/next.js/blob/canary/docs/basic-features/pages.md) trước nếu như bạn chưa đọc nó.

Chúng ta sẽ nói về ba Next.js function duy nhất mà bạn có thể sử dụng để lấy dữ liệu cho pre-rendering:

- [`getStaticProps`](#getstaticprops-static-generation) (Static Generation): Lấy dữ liệu tại **build time**.
- [`getStaticPaths`](#getstaticpaths-static-generation) (Static Generation): Xác định [dynamic routes](/docs/routing/dynamic-routes.md) để pre-render dựa trên dữ liệu có được.
- [`getServerSideProps`](#getserversideprops-server-side-rendering) (Server-side Rendering): Lấy dữ liệu trên **mỗi request**.
  
Ngoài ta, chúng ta sẽ nói ngắn gọn về cách lấy dữ liệu như thế nào tại client side.

## `getStaticProps` (Static Generation)

Nếu bạn export `async` function được gọi là `getStaticProps`, Next.js sẽ pre-render trang này tại build time sử dụng props được trả về bởi `getStaticProps`.

```jsx
export async function getStaticProps(context) {
  return {
    props: {}, // props sẽ được truyền tới page component
  }
}
```

Tham số `context` là một đối tượng chứa các keys sau:
- `params` chứa các tham số route của những trang sử dụng dynamic routes. Ví dụ, nếu trang có tên là [id].js, sau đó `params` sẽ như sau `{ id: ... }`. Để tìm hiểu thêm, xem qua tài liệu [Dynamic Routing](https://github.com/vercel/next.js/blob/canary/docs/routing/dynamic-routes.md). Bạn nên sử dụng cách chung với `getStaticPaths`, mà chúng tôi sẽ giải thích phía sau.
- `preview` là `true` nếu trang trong chế độ xem trước và nếu không thì là `undefined`. Xem tài liệu [Preview Mode](https://github.com/vercel/next.js/blob/canary/docs/advanced-features/preview-mode.md).
- `previewData` chứa tập dữ liệu xem trước bởi `setPreviewData`. Xem tài liệu [Preview Mode](https://github.com/vercel/next.js/blob/canary/docs/advanced-features/preview-mode.md).

`getStaticProps` sẽ trả về một đối tượng với:
- `props` - Một đối tượng **bắt buộc** với props mà sẽ được nhận bởi page component. Nó phải là [serializable object](https://en.wikipedia.org/wiki/Serialization)
- `revalidate` - Một số **tuỳ chọn** đếm bằng giây sau khi mà trang re-generation có thể xảy ra. Thông tin thêm [Incremental Static Regeneration](https://github.com/vercel/next.js/blob/canary/docs/basic-features/data-fetching.md#incremental-static-regeneration)