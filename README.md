SDL-IM-plus
====

SDL の IME 対応修正版です。  
SDL 1.2.15 に SDL-IM 1.2.8 (2005/8/28) のパッチを当てたソースを適用し、さらに何点か修正しています。  

SDL-1.2 [README](https://github.com/nanshiki/SDL-IM-plus/blob/master/README)  

## ビルド
### Windows  
Visual Studio の 2015 以降で VisualC/SDL.sln を読み込み、ビルドしてください。  

### Linux  
$ ./autogen.sh  
$ ./configure  
$ make  
$ sudo make install  

Debian 系の場合、autoconf libx11-dev libxext-dev あたりをインストールしておいてください。  
RedHat 系の場合、autoconf libXt-devel libXaw-devel あたりをインストールしておいてください。  
ライブラリの名称やヘッダファイルの格納先は SDLIM です。  
コンパイル用の環境取得スクリプトは sdlim-config です。  

### macOS  
$ ./autogen.sh  
$ ./configure  
$ make  
$ sudo make install  
Xcode, Command line tools for Xcode をインストールしておいてください。  
Homebrew で autoconf をインストールしておいて下さい。  
ライブラリの名称やヘッダファイルの格納先は SDLIM です。  
コンパイル用の環境取得スクリプトは sdlim-config です。  


## 追加関数
`char *SDL_SetIMValues(SDL_imvalue value, ...);`  
　IM の状態設定を行います。  
引数: SDL_imvalue  
　SDL_IM_ENABLE　IM の有効(1)、無効(0)  
　SDL_IM_ONOFF　IM の ON(1)、OFF(0)  
　SDL_IM_FONT_SIZE　変換中文字列のフォントサイズ(Windows のみ)  
　SDL_IM_MESSAGE_UNICODE　確定文字列をSDL_FlushIMStringで取得(0)、SDL_KEYDOWNのevent.key.keysym.unicodeで渡す(1)  
返値: エラー文字列 NULLなら正常終了  
例)
`SDL_SetIMValues(SDL_IM_ENABLE, 1, NULL);`  
　IM を有効にします。

`char *SDL_GetIMValues(SDL_imvalue value, ...);`  
　IM の状態を取得します。  
引数: SDL_imvalue  
　SDL_IM_ENABLE　IM の有効(1)、無効(0)  
　SDL_IM_ONOFF　IM の ON(1)、OFF(0)  
　SDL_IM_FONT_SIZE　変換中文字列のフォントサイズ(Windows のみ)  
　SDL_IM_MESSAGE_UNICODE　確定文字列をSDL_FlushIMStringで取得(0)、SDL_KEYDOWNのevent.key.keysym.unicodeで渡す(1)  
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
引数: buffer 文字列を格納するバッファ NULL の場合バイト数/文字数のみ取得  
返値  Shift JISの場合バイト数、UTF-16LEの場合文字数  
　文字列の末尾に 0 は付加されませんので、まずはNULLでバイト数/文字数を取得してバッファを確保してください。  
　初期状態ではShift JISで格納されますが、`SDL_EnableUNICODE(1);`を実行している場合UTF-16LEで格納されます。  
　IMEで文字列を確定するとevent.key.keysym.scancodeとevent.key.keysym.symが0のSDL_KEYDOWNが送られてきますので、SDL_FlushIMString()で確定文字列を取得してください。  
　`SDL_SetIMValues(SDL_IM_MESSAGE_UNICODE, 1, NULL);`を実行するとevent.key.keysym.unicodeに確定文字がUTF-16LEで格納されたSDL_KEYDOWNで順番に送られてきます。  

`void SDL_SetCompositionFontName(const char *name);`  
　変換中文字列で使用するフォント名を指定します。  
引数: name フォント名(Shift JIS)  
　Windows のみの対応です。  

## 環境変数
Linux 版の場合、環境変数 SDLIM_STYLE で Root, OverTheSpot, OnTheSpot の設定をする事でアプリケーションの変換表示の選択ができますが、OnTheSpot での変換文字列描画には対応していませんのであまり意味はありません。  
未設定の場合は OverTheSpot となります。  

## ライセンス
LGPL v2  

