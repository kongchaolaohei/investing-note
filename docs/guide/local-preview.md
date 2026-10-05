# 本地预览

站点由 MkDocs Material 构建。本地预览步骤（macOS）：

```bash
# 1. 进入仓库目录
cd ~/Desktop/investing-note

# 2. 首次：创建虚拟环境并安装依赖
python3 -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt

# 3. 之后每次：激活环境并启动预览
source .venv/bin/activate
mkdocs serve
```

打开 <http://127.0.0.1:8000>，修改 `docs/` 下任何文件会自动刷新。

## 提交前自检

```bash
mkdocs build --strict
```

`--strict` 下任何 WARNING（死链、nav 缺页、PDF 路径错误）都会使构建失败——CI 用同样标准，本地过了再推送。

## 常见问题

- **中文文件名报错/链接断**：确认链接使用相对路径且与磁盘文件名完全一致（含大小写与全角字符）。
- **新增页面没出现在导航**：`mkdocs.yml` 的 `nav` 需手工登记，见 [conventions.md §5](conventions.md)。
