# ffmpegのライセンス調査
ffmpegのソースコードにはいくつかのライセンスファイルが同梱されている。
configureオプションによりビルド結果のライセンスが変わるのだが
機械的なライセンス検出ではその全てを検出してしまい実際に使う時の
ライセンスが特定できない。

人力で調査を行った場合の結果をまとめてみる。

## ライセンスファイルによる調査
ソースコードのトップディレクトリに置かれているライセンス関連ファイル

COPYING.GPLv2
COPYING.GPLv3
COPYING.LGPLv2.1
COPYING.LGPLv3
LICENSE.md          ... どのファイル、ライブラリがGPLv2なのかが書いてある  

LICENSE.mdから抜粋
Most files in FFmpeg are under LGPL v2.1+.
Some other files have MIT/X11/BSD-style licenses. 
In combination the LGPL v2.1+ applies to FFmpeg.

Some optional parts of FFmpeg are licensed under the GPL v2+

- ffmpegはLGPL v2.1+である。
- 選択可能な部品にGPL v2+が含まれる。
- (L)GPL v3へのアップグレードが可能。
	- これは(L)GPL v3のソフトが含まれる意味ではなく、
最新のGPLに更新できる条項を用いてライセンスを変更するという意味。
- nonfreeにするとOSSではないコードを含めたバイナリコードが生成される。
	- 頒布するとライセンス違反になるため、頒布できない。

## configure option
4種類あり、ビルド結果のライセンスが変わる

-  default                  LGPL v2+
-  --enable-gpl             allow use of GPL code, the resulting libs
                           and binaries will be under GPL [no]
-  --enable-version3        upgrade (L)GPL to version 3 [no]
-  --enable-nonfree         allow use of nonfree code, the resulting libs
                           and binaries will be unredistributable [no]


gplv2の場合のみenabled filtersの数が増える
それ以外は同じソフトでライセンスを変えるだけのようだ



