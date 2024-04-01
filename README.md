# libpackagelistparser
GNU Emacs30.0.50に含まれる`java/INSTALL`にしたがってパッチを適用したlibpackagelistparserモジュール(libselinuxの依存モジュール)のレポジトリ。

# 作成した手順
1. [Google Gitのcore](git clone https://android.googlesource.com/platform/system/core)をclone

```bash
$: git clone git clone https://android.googlesource.com/platform/system/core
```

2. `nougat-mr1-dev`ブランチから修正用ブランチ`my/nougat-mr1-dev`をcheckout

```bash
$: cd core
$: git checkout nougat-mr1-dev
$: git checkout -b my/nougat-mr1-dev
```

3. システムヘッダのincludeエラー([バグレポート](https://debbugs.gnu.org/cgi/bugreport.cgi?bug=66507#22)を参照)に対処するために独自にpatchを適用

```bash
$: patch -p1 < PATCH_FOR_PACKAGELISTPARSER.patch
```

4. 上記patch ファイルとpatch適用後ファイルをcommitして空レポジトリにpush

```bash
$: git add -A
$: git commit -m 'nanika commit messages...'
$: gh repo create my-core --public
$: git remote add mine https://github.com/JIBUN/my-core.git
$: git branch -M my/nougat-mr1-dev
$: git push -u mine my/nougat-mr1-dev
```
