# go-ci

Go の CI 用イメージ。
lint とテスト結果整形ツールを同梱。

## 含まれるもの

- Go (Alpine) — バージョンは `versions.json` で管理
- golangci-lint — バージョンは `versions.json` で管理
- tparse — バージョンは `versions.json` で管理

## 使い方

### GitHub Actions

```yaml
jobs:
  ci:
    runs-on: ubuntu-latest
    container:
      image: ghcr.io/umekikazuya/go-ci:1.26
    steps:
      - uses: actions/checkout@v4
      - run: go mod download
      - run: golangci-lint run ./...
      - run: go test -json ./... | tparse -all
```

### ローカルで lint を実行

```bash
docker run --rm -v $(pwd):/app ghcr.io/umekikazuya/go-ci:1.26 \
  golangci-lint run ./...
```

### ローカルでテスト

```bash
docker run --rm -v $(pwd):/app ghcr.io/umekikazuya/go-ci:1.26 \
  sh -c "go test -json ./... | tparse -all"
```
