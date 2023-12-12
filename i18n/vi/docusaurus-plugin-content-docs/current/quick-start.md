---
sidebar_position: 1
---

# Quick Start

**Tổng quan**

Công cụ của chúng tôi sẽ hỗ trợ bạn 3 việc chính:
- **Khởi tạo dự án mới** với các công nghệ được tích hợp sẵn.
- **Tích hợp thêm các công nghệ** vào một dự án đang trong quá trình phát triển.
- **Tạo file dựa trên template**, giúp việc phát triển nhanh và đồng bộ hoá cấu trúc dự án giữa các thành viên.

Lưu ý: hiện tại đối với khởi tạo dự án và tích hợp công nghệ thì chúng tôi chỉ hỗ trợ cho các dự án sử dụng `nodejs`. Các nền tảng khác sẽ được hỗ trợ trong tương lai.

**Cài đặt công cụ**

Trong nội dung bài này chúng tôi sẽ cung cấp cho bạn một số hướng dẫn cơ bản để làm quen với `fp`. Để bắt đầu, bạn cần phải cài đặt công cụ này thông qua npm:

```bash
npm install -g @fast-project/cli

# Kiểm tra phiên bản hiện tại, bước này cũng đảm bảo rằng fp đã được cài đặt thành công
fp --version
```

## Tạo mới dự án

Tạo  thư mục và khởi tạo một dự án mới với `fp init`:

```bash
mkdir my-api-server
fp init node -c ts=true -c pm=yarn
```

Dự án mới này sẽ chúng ta sẽ sử dụng `express` làm web server. Để tích hợp, chúng ta cần sử dụng plugin tương ứng, được cung cấp sẵn trong `fp`:

```bash
fp use plugin express -c port=3000
```

Tiếp tục, sử dụng lệnh `yarn dev` để tiến hành chạy server. 

>Quá trình khởi tạo dự án này sẽ tạo ra file `fp.yaml`, trong đó chứa thông tin về các công nghệ đã được tích hợp. Bạn không nên tự chỉnh sửa file này vì có thể dẫn đến lỗi nếu tiếp tục sử dụng `fp` trong tương lai. Ngược lại, Nếu bạn không còn muốn sử dụng `fp` sau này, bạn có thể xóa file này khỏi dự án. Hoặc, bạn cũng có thể sử dụng file này để khởi tạo dự án mới với cấu hình tương tự.

**Tích hợp typeOrm**

Sau khi dự án được khởi tạo, chúng ta sẽ tiến hành tích hợp một ORM để làm việc với database. Trong ví dụ này, chúng ta sẽ sử dụng `typeorm`. Bạn cần thay đổi các giá trị config để phù hợp với môi trường trên máy của bạn:
```bash
fp use plugin typeorm  \
    -c db=mysql \
    -c db_user=root \
    -c db_password=123456 \
    -c db_name=test
```

**Và một số công nghệ khác**

Bạn cũng có thể tiết kiệm được thời gian khi sử dụng `fp` để tích hợp thêm các công cụ khác vào dự án của mình. Ví dụ, chúng ta sẽ tích hợp `eslint` và `docker`. Công việc này đơn giản chỉ là sử dụng lệnh `fp use` với tên plugin tương ứng:

```bash
fp use plugin eslint
fp use plugin docker -c compose=true
```

Để xem danh sách các plugin có sẵn, bạn có thể sử dụng lệnh sau:
```bash 
fp plugin list
```

### Tích hợp các tính năng cơ bản

Chúng tôi cung cấp sẵn cho bạn một số module cơ bản mà hầu như mọi dự án đều cần đến như xác thực người dùng, quản lý file, quản lý nội dung, ... Bạn có thể sử dụng lệnh `use module` để tích hợp các tính năng này vào dự án của mình:

```bash
fp use module auth
```

Các module yêu cầu sử dụng một số plugin nhất định, nên bạn cần phải cài đặt các plugin này trước khi sử dụng module. Ví dụ, module `auth` yêu cầu sử dụng plugin `typeorm` và `express`, nên bạn cần phải cài đặt 2 plugin này trước khi sử dụng module `auth`.

Để xem danh sách các module có sẵn, bạn có thể sử dụng lệnh sau:
```bash
fp module list
```

### Crud generator

Hai plugin `express` và `typeorm` đều cung cấp cho bạn một số lệnh để tạo ra các file mẫu. Ví dụ, bạn có thể sử dụng lệnh để tạo ra các file controller, route và validator cho một api trong express:
```bash
fp gen --plugin express -c name=book
```

Tương tự, bạn cũng có thể sử dụng lệnh để tạo ra một model, service và repository cho một entity trong typeorm:
```bash
fp gen --plugin typeorm -c name=book
```

### Tạo file dựa trên template