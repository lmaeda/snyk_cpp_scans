# ソースコードを取得
https://sourceforge.net/projects/libpng/files/libpng16/1.6.37/

# アーカイブファイル に対して スキャン
snyk test --org=demo_high --unmanaged --max-depth=20 ./downloads/libpng-1.6.37.tar.gz --print-dep-paths

# アーカイブファイル に対して monitor (監視)
snyk monitor --org=demo_high --unmanaged --max-depth=20 ./downloads/libpng-1.6.37.tar.gz --print-dep-paths

# アーカイブファイル に対して スキャン、結果をJSON出力
snyk test --org=demo_high --unmanaged --max-depth=20 ./downloads/libpng-1.6.37.tar.gz --print-dep-paths --json | tee ./snyk_unmanaged_libpng1.6.37_json_test_20241210.json

# アーカイブファイル に対して スキャン、結果をDebug出力
snyk test --org=demo_high --unmanaged --max-depth=20 ./downloads/libpng-1.6.37.tar.gz --print-dep-paths

# アーカイブ ファイル を展開
tar -xf ../downloads/libpng-1.6.37.tar.gz

# 展開後の Directory に cd
cd libpng-1.6.37

# 展開した ソースコードに対して、SBOMコマンドを実行
snyk sbom --unmanaged --org=demo_high --format=spdx2.3+json | python3 -m json.tool | tee ../snyk_unmanaged_sbom_libpng1.6.37.spdx.json
