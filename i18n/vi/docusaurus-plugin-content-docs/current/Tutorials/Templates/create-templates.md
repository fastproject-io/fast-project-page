---
sidebar_position: 1
---

# Tạo template

## Tạo mới template

Tạo thư mục chứa templates:

```bash
mkdir -p .templates/src/services
```

Tạo template đầu tiên:

```bash
cat << EOF > .templates/src/services/{{name}}.service.js.hbs
const getAll{{name}} = () => {
    return [];
};

module.exports = {
    getAll{{name}}
};
EOF
```

## Sử dụng template

```bash
fp gen -t .templates -c name=book
```