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

Chúng tôi **khuyên** bạn nên sử dụng **Static Generation** trên Server-side Rendering cho những lý do về hiệu năng. Những trang tỉnh được tạo ra có thể được cache bởi CDN mà không cần phải cấu hình thêm, để tăng hiệu năng. Tuy nhiên, trong một số trường hợp, Server-side Rendering có thể là lựa chọn duy nhất.

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

#### Kịch bản 2: Đường dẫn trang của bạn phụ thuộc vào dữ liệu bên ngoài

Next.js cho phép bạn tạo ra các trang với **dynamic routes**. Ví dụ, bạn tạo một file có tên là `pages/posts/[id].js` để hiển thị một bài post dựa trên `id`. Điều này cho phép bạn hiển thị bài blog với `id: 1` khi bạn truy cập vào đường dẫn `posts/1`.

> Để tìm hiểu thêm về dynamic routing, xem thêm tài liệu [Dynamic Routing](https://github.com/vercel/next.js/blob/canary/docs/routing/dynamic-routes.md).

Tuy nhiên, `id` mà bạn muốn pre-render tại build time có thể phụ thuộc vào dữ liệu bên ngoài.

**Ví dụ**: Giả sử bạn chỉ mới thêm một bài blog (với `id: 1`) vào database. Trong trường hợp này, bạn chỉ muốn pre-render `posts/1` tại build time.

Sau đó, bạn có thể muốn thêm một bài blog thứ hai với `id: 2`. Sau đó bạn cũng muốn pre-render `posts/2`.

Vì thế những **đường dẫn** trang của bạn được pre-render sẽ phụ thuộc vào dữ liệu bên ngoài. Để xử lý vấn đề này, Next.js cho phép bạn `export` một `async` function được gọi là `getStaticPaths` từ trang động (trong trường hợp này là `pages/posts/[id].js`). Function này được gọi tại build time và cho phép bạn xác định được những đường dẫn nào mà bạn muốn pre-render.

```jsx
// Fucntion này được gọi tại build time
export async function getStaticPaths() {
  // Gọi API bên ngoài để lấy dữ liệu danh sách bài post
  const res = await fetch('https://.../posts')
  const posts = await res.json()

  // Lấy danh sách những đường dẫn chúng ta muốn pre-render dựa trên danh sách bài post
  const paths = posts.map((post) => `/posts/${post.id}`)

  // Chúng ta sẽ chỉ pre-render những đường dẫn này tại build time.
  // { fallback: false } có nghĩa là những route khác sẽ là 404 (không tìm thấy).
  return { paths, fallback: false }
}
```

Cũng trong `pages/posts/[id].js`, bạn cần export `getStaticProps` vì bạn lấy dữ liệu về bài blog với `id` của nó và sử dụng nó để pre-render trang:

```jsx
function Post({ post }) {
  // Render post...
}

export async function getStaticPaths() {
  // ...
}

// Function này cũng được gọi tại build time
export async function getStaticProps({ params }) {
  // params chứa `id` cùa bài blog.
  // Nếu đường dẫn là /posts/1, sau đó params.id sẽ là 1
  const res = await fetch(`https://.../posts/${params.id}`)
  const post = await res.json()

  // Truyền dữ liệu của bài blog vào trang thông qua props
  return { props: { post } }
}

export default Post
```

Để tìm hiểu thêm về cách `getStaticPaths` làm việc như thế nào, xem qua tài liệu [Data Fetching](https://github.com/vercel/next.js/blob/canary/docs/basic-features/data-fetching.md#getstaticpaths-static-generation) 

### Khi nào nên sử dụng Static Generation?

Chúng tôi khuyện bạn sử dụng **Static Generation** (có và không có dữ liệu) bất cứ khi nào có thể bởi vì trang của bạn có thể build một lần và được cung cấp bởi CDN, điều này làm cho trang của bạn nhanh hơn nhiều, hơn là để sever phải render trang trên mỗi request.

Bạn có thể sử dụng Static Generation cho nhiều loại trang, bao gồm:
- Những trang marketing
- Blog posts
- Danh sách sản phẩm trên trang thương mại điện tử (E-commerce)
- Hỗ trợ và tài liệu

Bạn nên tự hỏi bản thân: "Tôi có thể pre-render trang này **trước** request của người dùng không ?" Nếu câu trả lời là có, thì bạn nên lựa chọn Static Generation.

Mặt khác, Static Generation **không** phải là một ý kiến tốt nếu bạn không thể pre-render trang trước request người dùng. Có thể trang của bạn hiển thị dữ liệu được cập nhật thường xuyên, và nội dung trang thay đổi trên mỗi request.

Trong những trường hợp giống vậy, bạn có thể làm theo một trong số điều sau đây:
- Sử dụng Static Generation với **Client-side Rendering**: Bạn có thể bỏ qua pre-rendering một số phần của trang sau đó sử dụng client-side JavaScript để populate chúng. Để tìm hiểu thêm về cách tiếp cận này, xem thểm tài liệu [Data Fetching](https://github.com/vercel/next.js/blob/canary/docs/basic-features/data-fetching.md#fetching-data-on-the-client-side).
- Sử dụng **Server-Side Rendering**: Next.js pre-render trang trên mỗi request. Nó sẽ chậm hơn bởi vì trang không thể cache bằng CDN, nhưng pre-render trang sẽ luôn luôn được cập nhật. Chúng ta sẽ nói về cách tiếp cận này bên dưới.

## Server-side Rendering

> Còn được gọi là "SSR" hoặc "Dynamic Rendering".

Nếu trang sử dụng **Server-side Rendering**, thì trang HTML sẽ được tạo ra trên mỗi request.

Để sử dụng Server-side Rendering cho trang, bạn cần `export` một `async` function được gọi là `getServerSideProps`. Function này sẽ được gọi bởi server trên mỗi request.

Ví dụ, giả sử rằng trang của bạn cần pre-render để cập nhật dữ liệu thường xuyên (lấy dữ liệu từ API bên ngoài). Bạn có thể viết `getServerSideProps` để lấy dữ liệu này và truyền nó tới `Page` như bên dưới:

```jsx
function Page({ data }) {
  // Render data...
}

// Function này sẽ được gọi trên mỗi request
export async function getServerSideProps() {
  // Lấy dữ liệu từ API bên ngoài
  const res = await fetch(`https://.../data`)
  const data = await res.json()

  // Truyền dữ liệu tới page thông qua props
  return { props: { data } }
}

export default Page
```

Như bạn đã thấy, `getServerSideProps` giống với `getStaticProps`, nhưng điểm khác nhau là `getServerSideProps` thì chạy trên mỗi request thay vì tại build time.

Để tìm hiểu thêm về `getServerSideProps` làm việc như thế nào, xem thêm tài liệu [Data Fetching](https://github.com/vercel/next.js/blob/canary/docs/basic-features/data-fetching.md#getserversideprops-server-side-rendering).

## Tóm tắt
Chúng ta đã thảo luận hai hình thức pre-rendering của Next.js.
- **Static Generation** (Được đề xuất): HTML được tạo tại thời điểm build time và sẽ được sử dụng lại trên mỗi request. Để tạo một trang sử dụng Static Generation, có thể export page component hoặc export `getStaticProps` (và `getStaticPaths` nếu cần). Thật tuyệt vời cho các trang có thể hiển thị trước request của người dùng. Bạn cũng có thể sử dụng nó với Client-side Rendering để thêm dữ liệu bổ sung.
- **Server-side Rendering**: HTML được tạo ra trên **mỗi request**. Để tạo một trang sử dụng Server-side Rendering, export `getServerSideProps`. Bởi vì kết quả của Server-side Rendering có hiệu năng thấp hơn là Static Generation, vậy nên chỉ sử dụng cách này nếu thật sự cần thiết.

## Tìm hiểu thêm

Chúng tôi khuyên bạn đọc qua các phần tiếp theo:

<div class="card">
  <a href="/docs/basic-features/data-fetching.md">
    <b>Data Fetching:</b>
    <small>Tìm hiểu thêm về cách lấy dữ liệu trong Next.js.</small>
  </a>
</div>

<div class="card">
  <a href="/docs/advanced-features/preview-mode.md">
    <b>Preview Mode:</b>
    <small>Tìm hiểu thêm về chế độ xem trước trong Next.js.</small>
  </a>
</div>

<div class="card">
  <a href="/docs/routing/introduction.md">
    <b>Routing:</b>
    <small>Tìm hiểu thêm về điều hướng trong Next.js.</small>
  </a>
</div>

<div class="card">
  <a href="/docs/basic-features/typescript.md#pages">
    <b>TypeScript:</b>
    <small>Thêm Typescript vào trang của bạn.</small>
  </a>
</div>