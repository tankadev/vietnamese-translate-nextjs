###### Ngày cập nhật: 14/10/2020
# Pages


>Tài liệu này được viết ra cho Next.js từ phiên bản 9.3 trở lên. Nếu bạn đang sử dụng những phiên bản Next.js cũ hơn, hãy tham khảo [tài liệu này](https://nextjs.org/docs/tag/v9.2.2/basic-features/pages).


Trong Next.js, **page** là một [React Component](https://reactjs.org/docs/components-and-props.html) được export từ `.js`, `.jsx`, `.ts`, hoặc `.tsx` file trong thư mục `pages`. Mỗi page được liên kết với route dựa trên tên file của nó.

**Ví dụ**: Nếu bạn tạo file `about.js` trong thư mục `pages` (`pages/about.js`) mà export từ React component giống bên dưới, nó sẽ được liên kết với đường dẫn `/about`.

```jsx
function About() {
  return <div>About</div>
}

export default About
```

## Pages với route động (dynamic routes)

Next.js hỗ trợ pages với route động. Ví dụ, nếu bạn tạo một file có tên là `pages/posts/[id].js`, thì nó sẽ được liên kết tới đường dẫn `posts/1`, `posts/2`.


>Để biết thêm về điều hướng động (dynamic routing), hãy tham khảo [tài liệu Dynamic Routing](https://nextjs.org/docs/routing/dynamic-routes).


## Pre-rendering
Mặc định, Next.js **pre-renders** tất cả mọi trang. Điều này có nghĩa là Next.js sẽ tạo ra HTML cho mỗi trang trước, thay vì tất cả được thực hiện bởi client-side JavaScript. Pre-rendering có thể mang lại kết quả với hiệu năng tốt hơn và SEO.

Mỗi HTML được tạo ra sẽ được liên kết với code JavaScript cần thiết tối thiểu cho trang đó. Khi trang được tải lên bởi trình duyệt, code Javascript của nó sẽ được chạy và tạo ra tương tác với toàn bộ trang. (Quá trình này được gọi là *hydration*).

### Hai hình thức của Pre-rendering
***
Next.js có hai hình thức của pre-rendering: **Static Generation** và **Server-side Rendering**. Điểm khác biệt là **khi** nó tạo ra thành phần HTML của trang.
- [Static Generation (Được khuyên dùng)](https://github.com/vercel/next.js/blob/canary/docs/basic-features/pages.md#static-generation-recommended): Thành phần HTML được tạo ra tại **build time** và sẽ được sử dụng lại trên mỗi request.
- [Server-side Rendering](https://github.com/vercel/next.js/blob/canary/docs/basic-features/pages.md#server-side-rendering): Thành phần HTML được tạo ra trên **mỗi request**.

Quan trọng, Next.js cho phép bạn **lựa chọn** hình thức pre-rendering nào mà bạn thích sử dụng cho mỗi trang. Bạn có thể tạo ra ứng dụng Next.js "hybrid" bằng cách sử dụng Static Generation cho hầu hết các trang và sử dụng Server-side Rendering cho những trang khác.

Chúng tôi **khuyên** bạn nên sử dụng **Static Generation** over Server-side Rendering cho những lý do về hiệu năng. Những trang tỉnh được tạo ra có thể được cache bởi CDN mà không cần phải cấu hình thêm, để tăng hiệu năng. Tuy nhiên, trong một số trường hợp, Server-side Rendering có thể là lựa chọn duy nhất.

Bạn cũng có thể sử dụng **Client-side Rendering** cùng với Static Generation hoặc Server-side Rendering. Điều này có nghĩa là một số phần của trang có thể được render toàn bộ bởi client side Javascript. Để tìm hiểu thêm, hãy xem qua tài liệu [Data Fetching](https://github.com/vercel/next.js/blob/canary/docs/basic-features/data-fetching.md#fetching-data-on-the-client-side).

## Static Generation (Được khuyên dùng)

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

Nếu trang sử dụng **Static Generation**, trang HTML được tạo ra tại **build time**. Điều này có nghĩa trong môi trường production, trang HTML được tạo ra khi bạn chạy lênh `next build`. Thành phần HTML này sau đó sẽ được tái sử dụng trên mỗi request. Nó có thể được cache bởi CDN.

Trong Next.js, bạn có thể tạo ra các trang tỉnh **với dữ liệu** hoặc **không có dự liệu**. Hãy xem xét trên mỗi trường hợp.

### Static Generation không có dữ liệu

Mặc định, Next.js pre-renders các trang sử dụng Generation Generation mà không cần phải lấy dữ liệu. Đây là ví dụ:

```jsx
function About() {
  return <div>About</div>
}

export default About
```

Chú ý rằng trang này không cần lấy bất kỳ dữ liệu bên ngoài nào để pre-rendered. Trong những trường hợp tương tự, Next.js tạo ra một file HTML cho mỗi trang trong suốt quá trình build time.

### Static Generation với dữ liệu

Một số trang yêu cầu phải lấy dữ liệu từ bên ngoài cho pre-rendering. Ở đây có hai kịch bản, và một hoặc cả hai có thể được áp dụng. Trong mỗi trường hợp, bạn có thể sử dụng những fuction riêng biệt mà Next.js cung cấp:

1. **Nội dụng** trên trang của bạn phụ thuộc vào dữ liệu bên ngoài: Sử dụng `getStaticProps`.
2. **Những đường dẫn** trên trang của bạn phụ thuộc vào dữ liệu bên ngoài: Sử dụng `getStaticPaths` (thông thường sử dụng thêm `getStaticProps`).

#### Kịch bản 1: **Nội dụng** trên trang của bạn phụ thuộc vào dữ liệu bên ngoài

**Ví dụ**: Trang blog của bạn có thể cần lấy danh sách của các bài blog từ CMS (content management system).

```jsx
// TODO: Cần lấy dữ liệu `posts` (bằng cách gọi một số API nào đó)
//      trước khi trang này có thể được pre-rendered.
function Blog({ posts }) {
  return (
    <ul>
      {posts.map((post) => (
        <li>{post.title}</li>
      ))}
    </ul>
  )
}

export default Blog
```

Để lấy dữ liệu khi pre-render, Next.js cho phép bạn `export` một `async` function được gọi là `getStaticProps` trên cùng file này. Function này được gọi tại build time và cho bạn truyền dữ liệu lấy được tới `props` của trang khi pre-render.

```jsx
function Blog({ posts }) {
  // Render posts...
}

// Function này được gọi tại build time
export async function getStaticProps() {
  // Gọi một API bên ngoài để lấy về danh sách các bài post
  const res = await fetch('https://.../posts')
  const posts = await res.json()

  // Trả về { props: posts }, the Blog component
  // sẽ nhận về `posts` như là một prop tại build time
  return {
    props: {
      posts,
    },
  }
}

export default Blog
```

Để tìm hiểu thêm về cách mà `getStaticProps` hoạt động, xem thêm tài liệu [Data Fetching](https://github.com/vercel/next.js/blob/canary/docs/basic-features/data-fetching.md#getstaticprops-static-generation)