###### Ngày cập nhật: 13/10/2020
# Pages

***
Tài liệu này được viết ra cho Next.js từ phiên bản 9.3 trở lên. Nếu bạn đang sử dụng những phiên bản Next.js cũ hơn, hãy tham khảo [tài liệu này](https://nextjs.org/docs/tag/v9.2.2/basic-features/pages).
***

Trong Next.js, **page** là một [React Component](https://reactjs.org/docs/components-and-props.html) được export từ `.js`, `.jsx`, `.ts`, hoặc `.tsx` file trong thư mục `pages`. Mỗi page được liên kết với route dựa trên tên file của nó.

**Ví dụ**: Nếu bạn tạo một một file `about.js` trong thư mục `pages` (`pages/about.js`) mà export từ React component giống bên dưới, nó sẽ được liên kết với đường dẫn `/about`.

```js
function About() {
  return <div>About</div>
}

export default About
```

## Pages với route động (dynamic routes)

Next.js hỗ trợ pages với route động. Ví dụ, nếu bạn tạo một file có tên là `pages/posts/[id].js`, thì nó sẽ được liên kết tới đường dẫn `posts/1`, `posts/2`.

***
Để biết thêm về điều hướng động (dynamic routing), hãy tham khảo [tài liệu Dynamic Routing](https://nextjs.org/docs/routing/dynamic-routes).
***

## Pre-rendering
Mặc định, Next.js **pre-renders** tất cả mọi trang. Điều này có nghĩa là Next.js sẽ tạo ra HTML cho mỗi trang trước, thay vì tất cả được thực hiện bởi client-side JavaScript. Pre-rendering có thể mang lại kết quả với hiệu năng tốt hơn và SEO.

Mỗi HTML được tạo ra sẽ được liên kết với code JavaScript cần thiết tối thiểu cho trang đó. Khi trang được tải lên bởi trình duyệt, code Javascript của nó sẽ được chạy và tạo ra tương tác với toàn bộ trang. (Quá trình này được gọi là *hydration*).

## Hai hình thức của Pre-rendering
