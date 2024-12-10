# ソースコードを取得
https://sourceforge.net/projects/libpng/files/zlib/1.2.11/

# アーカイブファイル に対して スキャン
snyk test --org=demo_high --unmanaged --max-depth=20 ./downloads/zlib-1.2.11.tar.gz --print-dep-paths 

# アーカイブファイル に対して monitor (監視)
snyk monitor --org=demo_high --unmanaged --max-depth=20 ./downloads/zlib-1.2.11.tar.gz --print-dep-paths 

# アーカイブファイル に対して スキャン、結果をJSON出力
snyk test --org=demo_high --unmanaged --max-depth=20 ./downloads/zlib-1.2.11.tar.gz --print-dep-paths --json | tee ./snyk_unmanaged_zlib-1.2.11_test_json_20241210.json

# アーカイブファイル に対して スキャン、結果をDebug出力
snyk test --org=demo_high --unmanaged --max-depth=20 ./downloads/zlib-1.2.11.tar.gz --print-dep-paths -d

# アーカイブ ファイル を展開
tar -xf ../downloads/zlib-1.2.11.tar.gz

# 展開後の Directory に cd
cd zlib-1.2.11

# 展開した ソースコードに対して、SBOMコマンドを実行
snyk sbom --unmanaged --org=demo_high --format=spdx2.3+json | python3 -m json.tool | tee ../snyk_unmanaged_sbom_zlib1.2.11.spdx.json
