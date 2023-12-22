---
sidebar_position: 3
---

# Đăng ký helpers

Helper là các function được sử dụng để thực hiện các tác vụ phức tạp trong template. Để sử dụng helper, bạn cần phải sử dụng `setup file` để đăng ký helpers:

Đầu tiên, chỉnh sửa template:

```bash
cat << EOF > .templates/src/services/{{name}}.service.js.hbs
const getAll{{pascalCase name}} = () => {
    return [];
};

module.exports = {
    getAll{{pascalCase name}}
};
EOF
```

Sau đó, tạo setup file:

```bash
cat << EOF > .templates/setup.js
module.exports = (plugin) => {
    plugin.registerHelper('pascalCase', (str) => {
        return str.replace(/(\w)(\w*)/g, (_, g1, g2) => g1.toUpperCase() + g2.toLowerCase());
    });
EOF
```

Cuối cùng, sử dụng setup file vừa được tạo:

```bash
fp gen .templates/setup.js -t .templates -c .templates/config.js
```