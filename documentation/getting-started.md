###### Ngày cập nhật: 13/10/2020
# Bắt đầu

Chào các bạn đến với tài liệu Next.js

Nếu bạn là một người mới làm quen với Next.js, chúng tôi khuyên bạn nên bắt đầu với [khoá học](https://nextjs.org/learn/basics/create-nextjs-app) này trước

Khoá học tương tác với các câu hỏi sẽ hướng dẫn bạn đi qua hết tất cả mọi thứ mà bạn cần, để biết cách sử dụng Next.js

Nếu bạn có bất kì câu hỏi nào liên quan đến Next.js, bạn luôn được chào đón để trao đổi với cộng đồng của chúng tôi trên [Github Discussions](https://github.com/vercel/next.js/discussions)

### Yêu cầu hệ thống
- [Node.js 10.13](https://nodejs.org/) hoặc sau đó
- MacOS, Windows (bao gồm WSL), và Linux được hỗ trợ

## Cài đặt
Chúng tôi gợi ý tạo một ứng dụng Next.js mới bằng cách sử dụng `create-next-app`, câu lệnh này sẽ cài đặt tất cả mọi thứ cho bạn một cách tự động. Để tạo project mới, chạy lệnh sau:

```
npx create-next-app
# hoặc
yarn create next-app
```

Sau khi cài đặt hoàn tất, làm theo hướng dẫn để khởi động **development server**. Hãy thử chỉnh sửa `pages/index.js` và xem kết quả trên trình duyệt của bạn.

Để biết thêm thông tin về cách sử dụng `create-next-app`, bạn có thể xem lại [tài liệu `create-next-app`](https://nextjs.org/docs/api-reference/create-next-app)

## Cài đặt thủ công
Cài đặt `next`, `react` và `react-dom` trong project của bạn:

```
npm install next react-dom
# hoặc
yarn add next react react-dom
```

Mở file `package.json` và thêm vào đoạn `script` sau:

```json
"script": {
    "dev": "next dev",
    "build": "next build",
    "start": "next start"
}
```

Các lệnh này sẽ đề cập đến những giai đoạn khác nhau của việc phát triển ứng dụng:
- `dev` - Chạy `next dev` sẽ khởi động Next.js trong chế độ development
- `build` - Chạy `next build` sẽ build ứng dụng chế độ production
- `start` - Chaỵ `next start` sẽ khởi động Next.js production server

Next.js được xây dựng dựa trên khái niệm về [pages](https://nextjs.org/docs/basic-features/pages). Page là [React Component](https://reactjs.org/docs/components-and-props.html) được export từ `.js`, `.jsx`, `.ts`, hoặc `.tsx` file trong thư mục `pages`. 

Pages được liên kết với route dựa trên tên file. Ví dụ `pages/about.js` được ánh xạ tới đường dẫn `/about`. Thậm chí bạn có thể thêm những tham số động cho route với tên file.

Tạo thư mục `pages` bên trong project.

Thêm vào `./pages/index.js` với nội dung sau:

```js
function HomePage() {
  return <div>Welcome to Next.js!</div>
}

export default HomePage
```

Để khởi động môi trường development, hãy chạy lệnh `npm run dev` hoặc `yarn dev`. Development server sẽ chạy trên đường dẫn `http://localhost:3000`.

Bạn hãy truy cập vào `http://localhost:3000` để xem ứng dụng của bạn.

Cho đến thời điểm hiện tại, chúng tôi đã có:
- Tự động compilation(biên dịch) and bundling(đóng gói) (với webpack và babel)
- [React Fast Refresh](https://nextjs.org/blog/next-9-4#fast-refresh)
- [Static generation and server-side rendering](https://nextjs.org/docs/basic-features/data-fetching) của [`./pages/`](https://nextjs.org/docs/basic-features/pages)
- [Static file serving.](https://nextjs.org/docs/basic-features/static-file-serving) `./public/` được ánh xạ tới `/`

Ngoài ra, bất kỳ ứng dụng Next,js nào cũng đã sẵn sàng cho production ngay từ đầu, đọc thêm thông tin về [tài liệu Deployment](https://nextjs.org/docs/deployment).

## Liên quan

Để biết thêm thông tin về những gì cần làm tiếp theo, chúng tôi đề xuất theo dõi những phần bên dưới:

- [Pages](https://nextjs.org/docs/basic-features/pages), tìm hiểu thêm Pages là gì trong Next.js
- [Hỗ trợ CSS](https://nextjs.org/docs/basic-features/built-in-css-support), sử dụng hỗ trợ CSS đã được tích hợp sẵn để thêm các style tuỳ chỉnh trong ứng dụng của bạn.
- [CLI](https://nextjs.org/docs/api-reference/cli), tìm hiểu thêm về Next.js CLI