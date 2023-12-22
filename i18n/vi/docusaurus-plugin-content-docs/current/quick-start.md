---
sidebar_position: 1
---

# Quick Start

## Tổng quan

`fast-project` sẽ hỗ trợ bạn 3 việc chính:
- **Khởi tạo dự án mới** với các công nghệ được tích hợp sẵn.
- **Tích hợp thêm các công nghệ** vào một dự án đang trong quá trình phát triển một cách đơn giản.
- **Tạo file dựa trên template**, giúp việc phát triển nhanh và đồng bộ hoá cấu trúc dự án giữa các thành viên.

Lưu ý: hiện tại đối với khởi tạo dự án và tích hợp công nghệ thì chúng tôi chỉ hỗ trợ cho các dự án sử dụng `nodejs`. Các nền tảng khác sẽ được hỗ trợ trong tương lai.

## Cài đặt

Trong nội dung bài này tôi sẽ cung cấp cho bạn một số hướng dẫn cơ bản để làm quen với `fp`. Để bắt đầu, bạn cần phải cài đặt công cụ này thông qua npm:

```bash
npm install -g @fast-project/cli
```

## Tạo mới dự án

Tạo thư mục và khởi tạo một dự án mới sử dụng `node generator`:

```bash
fp init node -o my-project && cd my-project
```

Sử dụng `node plugin` để tạo cấu trúc dự án NodeJS:
```bash
fp use node
```

Sử dụng `express plugin` để tích hợp express:
```bash
fp use express
```

Với các bước đơn giản trên bạn đã khởi tạo thành công một dự án nodeJs mới với express. Bây giờ, bạn có thể sử dụng lệnh `yarn dev` để tiến hành chạy dev server như một dự án bình thường.

> Quá trình khởi tạo dự án này sẽ tạo ra file `fast-project.json`, trong đó chứa thông tin cấu hình cli, generator và plugins đã được tích hợp. Nếu bạn không còn muốn sử dụng `fp` sau này, bạn có thể xóa file này khỏi dự án. Hoặc, bạn cũng có thể sử dụng file này để khởi tạo dự án khác với cấu hình tương tự với dự án hiện tại.

## Generate files

Để tạo nhanh một api, bạn có thể sử dụng lệnh `fp use` để tiến hành tạo các file liên quan thông qua plugin `express`:

**Ví dụ 1**: Tạo api `/books`

```bash
fp use express gen -c name=book
```

**Ví dụ 2**: Tạo api `/book-categories`
```bash
fp use express gen -c name=book-category
```

## Chỉnh sửa template

Các template dựng sẵn chắc chắn sẽ không phù hợp hoàn toàn đối với dự án của bạn, vậy nên trong hầu hết trường hợp, bạn cần phải chỉnh sửa các template này để phù hợp với yêu cầu của dự án. Để làm điều này, bạn có thể làm theo các bước sau:

**Bước 1**: Trích xuất template
Bạn có thể trích xuất và chỉnh sửa templates của plugin `express` bằng lệnh `fp extract`:

```bash
fp extract express gen
```

**Bước 2**: Chỉnh sửa template

Các template này sẽ được trích xuất tại thư mục `.templates/express/gen`. Bạn có thể tiến hành chính sửa các file này theo ý muốn. Bạn có thể tìm hiểu cú pháp của handlebars [tại đây](https://handlebarsjs.com/guide/).

**Bước 3**: Sử dụng template mới

Sử dụng lệnh `fp gen` để tạo các file mới dựa trên template đã chỉnh sửa:

```bash
fp gen .templates/express/gen.js -c name=city
```