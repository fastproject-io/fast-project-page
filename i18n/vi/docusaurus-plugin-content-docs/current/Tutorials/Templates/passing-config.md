---
sidebar_position: 2
---

# Truyền tham số

### Truyền trực tiếp

Bạn có thể truyền trực tiếp thông qua `-c` or `--config` với format `key=value`:

```bash
fp gen -t .templates -c name=book
```

### Thông qua file config

**Bước 1**: Tạo file config:

```bash
cat << EOF > .templates/src/config.js
module.exports = async () => {
    return {
        name: 'book'
    };
};
EOF
```

**Bước 2**: Sử dụng file `config.js` vừa được tạo:

```bash
fp gen -t .templates -c config.js
```

### Thông qua prompt

Cách này sẽ hữu ích khi bạn cần truyền tham số thông qua prompt để người dùng nhập vào. Bạn sẽ phải tạo file `config.js` như sau:

**Bước 1**: Cài đặt gói `inquirer`:

```bash
npm install inquirer -D
```

**Bước 2**: Tạo file config:

```bash
cat << EOF > .templates/config.js
const inquirer = require('inquirer');

module.exports = async () => {
    return await inquirer.prompt([
        {
            type: 'input',
            name: 'name',
            message: 'What is your model name?'
        }
    ]);
};
EOF
```

**Bước 3**: Sử dụng file `config.js` vừa được tạo:

```bash
fp gen -t .templates -c .templates/config.js
```