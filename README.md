SDL-IM-plus
====

SDL の IME 対応修正版です。  
SDL 1.2.15 に SDL-IM 1.2.8 (2005/8/28) のパッチを当てたソースを適用し、さらに何点か修正しています。  

SDL-1.2 [README](https://github.com/nanshiki/SDL-IM-plus/blob/master/README)  

## ビルド
### Windows  
Visual Studio Professional 2015 で VisualC/SDL.sln を読み込み、ビルドしてください。  

### Linux  
$ ./autogen.sh  
$ ./configure  
$ make  
$ sudo make install  

Debian 系の場合、apt-get で autoconf libx11-dev libxext-dev あたりをインストールしておいてください。  
RedHat 系の場合、yum で autoconf libXt-devel libXaw-devel あたりをインストールしておいてください。  
ライブラリの名称やヘッダファイルの格納先は SDLIM となりました。  
コンパイル用の環境取得スクリプトも sdlim-config となります。  

## 追加関数
`char *SDL_SetIMValues(SDL_imvalue value, ...);`  
　IM の状態設定を行います。  
引数: SDL_imvalue  
　SDL_IM_ENABLE　IM の有効無効  
　SDL_IM_ONOFF　IM の ON/OFF  
返値: エラー文字列 NULLなら正常終了  
例)
`SDL_SetIMValues(SDL_IM_ENABLE, 1, NULL);`  
　IM を有効にします。

`char *SDL_GetIMValues(SDL_imvalue value, ...);`  
　IM の状態を取得します。  
引数: SDL_imvalue  
　SDL_IM_ENABLE　IM の有効無効  
　SDL_IM_ONOFF　IM の ON/OFF  
返値: エラー文字列 NULLなら正常終了  
例)
`SDL_GetIMValues(SDL_IM_ONOFF, &stat, NULL);`  
　IM の ON/OFF 状態が stat に入ります。1 で ON 状態です。

`int SDL_SetIMPosition(int x, int y); `  
　IM の変換位置を指定します。  
引数: x  X 座標,  y  Y 座標  
返値: 0 でエラー、それ以外で成功

`int SDL_FlushIMString(void *buffer);`  
変換確定した文字列を取得します。  
引数: buffer 文字列を格納するバッファ NULL の場合文字列長のみ取得  
返値  文字列長  

## 環境変数
Linux 版の場合、環境変数 SDLIM_STYLE で Root, OverTheSpot, OnTheSpot の設定をする事でアプリケーションの変換表示の選択ができますが、OnTheSpot での変換文字列描画には対応していませんのであまり意味はありません。  
未設定の場合は OverTheSpot となります。  

## ライセンス
LGPL v2  

