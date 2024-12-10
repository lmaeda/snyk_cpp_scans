# Docker Hubの コンテナ イメージ に対して スキャン
snyk container test --org=demo_high　windriver/wrdistro23:full

# Docker Hubの コンテナ イメージ に対して monitor (監視)
snyk container monitor --org=demo_high　windriver/wrdistro23:full

# Docker Hubの コンテナ イメージ に対して スキャン、結果をJSON出力
snyk container test --org=demo_high --json windriver/wrdistro23:full　| tee ./snyk_container_windriver_test_json_20241210.json

# Docker Hubの コンテナ イメージ に対して、SBOMコマンドを実行
snyk container sbom --org=demo_high --format=spdx2.3+json windriver/wrdistro23:full　| python3 -m json.tool | tee ../snyk_container_sbom_windriver.spdx.json
