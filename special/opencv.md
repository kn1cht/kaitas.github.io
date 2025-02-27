---
layout: post
title: "「OpenCV 1.0 release candidate 1」(2006-08-18）"
date: 2006-01-15 20:39:15 GMT
author: aki
category: 
- special
- OpenCV
---
## 「OpenCV 1.0 release candidate 1」(2006-08-18）
情報まとめ．

## 翻訳:ライセンス条文>OpenCV/License

### OpenCVライセンス条文

----

 IMPORTANT: READ BEFORE DOWNLOADING, COPYING, INSTALLING OR USING. 
 重要：ダウンロード、コピー、インストール、使用する前にお読みください。

By downloading, copying, installing or using the software you agree to this license.
If you do not agree to this license, do not download, install, copy or use the software.

ソフトウェアをダウンロード、コピー、インストール、もしくは使用することによって、あなたはこのライセンスに同意します。
あなたがこの許可に同意しないならば、ソフトウェアをダウンロード、インストール、コピー、使用しないでください。



                       Intel License Agreement 
               For Open Source Computer Vision Library 
               オープンソースコンピュータビジョンライブラリのための
                       インテルライセンス契約

Copyright (C) 2000-2006, Intel Corporation, all rights reserved.
Third party copyrights are property of their respective owners. 

(C) 2000-2006、インテル社、全ての権利を保有しています
第三者著作権は、彼らのそれぞれの所有者の財産です。

Redistribution and use in source and binary forms, with or without modification,
are permitted provided that the following conditions are met:
以下の状況が対処されるならば、ソースとバイナリ形式の再配布と使用は、修正の有無にかかわらず、許されます：

  * Redistribution's of source code must retain the above copyright notice,
    this list of conditions and the following disclaimer.
  * ソースコードの再配布物は、上記の著作権通知（状況と以下の断り書きのこのリスト）を保持しなければなりません。

  * Redistribution's in binary form must reproduce the above copyright notice,
    this list of conditions and the following disclaimer in the documentation
    and/or other materials provided with the distribution.
  * バイナリ形式の再配布物は上記の著作権通知を複写しなければなりません。そして、この条件リストと以下の否認文書がドキュメントや他の資料が流通において提供されなければなりません。

  * The name of Intel Corporation may not be used to endorse or promote products
    derived from this software without specific prior written permission.
  * インテル社の名前は、特定の先の書面による許諾なしでこのソフトウェアに由来する製品を支持するか、販売促進するのに用いられない可能性があります。

This software is provided by the copyright holders and contributors "as is" and
any express or implied warranties, including, but not limited to, the implied
warranties of merchantability and fitness for a particular purpose are disclaimed.
In no event shall the Intel Corporation or contributors be liable for any direct,
indirect, incidental, special, exemplary, or consequential damages
(including, but not limited to, procurement of substitute goods or services;
loss of use, data, or profits; or business interruption) however caused
and on any theory of liability, whether in contract, strict liability,
or tort (including negligence or otherwise) arising in any way out of
the use of this software, even if advised of the possibility of such damage.  

このソフトウェアは著作権者によって提供されます、そして、寄稿者（contributors）は「"as is"（ありのまま）」かつ、いかなる明示もしくは暗黙の保証も、市場性における暗黙の補償（含むがこれに限らず）、特定の目的に対する適合性は否認されます。
インテル社もしくは寄稿者は、いかなる責任もなく、直接・間接的損害、付随的損害、特別損害、模範的損害、もしくは間接損害（代用品またはサービスの獲得、使用・利益・ビジネス停止のロス、を含むがこれに限らず）、を負いません。
使用、データまたは利益の損失;またはビジネス中断）どんなに引き起こされて責任のどんな理論中でもでも、契約、厳しい責任または不法行為（怠慢またはその反対を含む）においてこのソフトウェアの使用の範疇から外れたどんな使い方に対してでも起こる、たとえそのような損害の可能性について知らされているとしても。



## memo
2006年9月現在の最新バージョンは「OpenCV 1.0 release candidate 1」(2006-08-18）。
機械学習関係のライブラリが入ったらしいぞ。

## Linux install
### 必要なパッケージ
- libgtk2.0-dev
- libpng, zlib, libjpeg and libtiff with development files (*-devを入れてください)
- libavcodec from ffmpeg 0.4.9-pre1 or later + headers 
- libavcodecは別のライブラリでしかもLGPLなので同梱できない。以下のようにして
ffmpeg(http://ffmpeg.sourceforge.net)から入手してシェアードライブラリで使うこと（今回試しませんでした）。
        ./configure --enable-shared
        make
        make install
        you will have got: /usr/local/lib/libavcodec.so.*
                           /usr/local/lib/libavformat.so.*
                           /usr/local/include/ffmpeg/*.h

- その他
-- ''SWIG_Python_SetConstant''というエラーが出たので、Python2.4-sip4-devを入れてみたら解決しました。
-- automakeも必要。パッケージからautomake-1.9を入れ、環境変数を指定。
 export AUTOMAKE=/usr/binautomake-1.9
-- 最後に環境を確認。
 configure --enable-maintainer-mode
これで環境が見れます。


### インストール
　RPMをサポートしているLinuxだと多少方法が違いますがこれでいいでしょう。
      ./configure
      make
      sudo make install
      sudo ldconfig

　デフォルトのインストールパスは
 /usr/local/lib
 /usr/local/include/opencv
　…なので''/etc/ld.so.conf''に''/usr/local/lib''を追加してldconfigを後ほど実行する必要があります。もしくは、環境変数LD_LIBRARY_PATHに''/usr/local/lib''を足してもよいかも。
 export LD_LIBRARY_PATH=/usr/local/lib

他にも開発者は以下のパッケージがあるといいとのこと。
     autoconf-2.59 (including autoheader-2.59)
      automake-1.9* (including aclocal-1.9*)
      libtool-1.5 (including libtoolize-1.5)
      swig (version 1.3.24 is best)
で、これらのツールをインストールしたら、パッケージのトップディレクトリで、
 ./configure --enable-maintainer-mode
 autoconf
 make
 sudo make install
 sudo ldconfig
と繰り返せばいいのではないかと思う(冗長かも、環境設定はautoconfだけでいいのかも)。

### テストする
　automakeの伝統的なチェック目的プロジェクトを使ったコンパイルテストができます。
        make check
　で、以下のプログラムが手に入ると思います。
        tests/cv/src/cvtest
        tests/cxcore/src/cxcoretest
-補足：これだと関数テストしか見れないので見た目つまんないとおもいます。
　もしくは、単純なCの例をコンパイルして実行してみましょう。以下にあります。
     /usr/local/share/opencv/samples, e.g.:
     g++ `pkg-config --cflags opencv` -o morphology morphology.c `pkg-config --libs opencv`
 純gccは動きません。C++特有のシンボルが未解決なので(たぶんhighguiにある？)。

-補足：この説明もよくわかりませんし、指定されているディレクトリはrootでないとコンパイルできないと思います。なので以下の手順ではどうでしょう？
 mkdir opencv-0.9.9/tests/c
 cd opencv-0.9.9/tests/c
 cp /usr/local/share/opencv/samples/c/morphology.c ./
 g++ `pkg-config --cflags opencv` -o morphology morphology.c `pkg-config --libs opencv`
 cp /usr/local/share/opencv/samples/c/*.jpg ./
 ./morphology airplane.jpg

　これで、こんな感じのX-Windowsアプリが起動するはずです。めでたしめでたし。

![OpenCV_morph.jpg](/assets/2006/OpenCV_morph.jpg)


### OpenCVをIPPを使ってmakeする
-IPPをインストールする
     Let's assume, it installs to /opt/intel/ipp/5.1/ia32.
-インストールパス
   + add <install_path>/bin and <install_path>/bin/linux32
     (for example, /opt/intel/ipp/5.1/ia32/bin and /opt/intel/ipp/5.1/ia32/bin/linux32)
     to LD_LIBRARY_PATH in your initialization script (.bashrc or similar):
 LD_LIBRARY_PATH=/opt/intel/ipp/5.1/ia32/bin:/opt/intel/ipp/5.1/ia32/bin/linux32:$LD_LIBRARY_PATH
     export LD_LIBRARY_PATH

     or add these two directories, one per line, to /etc/ld.so.conf and run
     ldconfig as root.

   + that's it. Now OpenCV should be able to locate IPP shared libraries and make use of them.


### MacOSX
　これに関するドキュメントはINSTALLには書かれていません。OpenCV Wikiを読んでください、とのこと。


### Reading...

　NAIST千原研のwikiがグッジョブ。なので、ここを中心に読んでいこうと思います…(注)プレッシャーをかけているわけではありません。

　わたし自身は __GPUVision__ との比較のためにOpenCVを眺めているというスタンスです。


- [動画ファイル（aviファイル）の読み込み](http://chihara.naist.jp/people/2004/kenta-t/OpenCV/pukiwiki/index.php?%C6%B0%B2%E8%A5%D5%A5%A1%A5%A4%A5%EB%A1%CAavi%A5%D5%A5%A1%A5%A4%A5%EB%A1%CB%A4%CE%C6%C9%A4%DF%B9%FE%A4%DF)

　OpenCVのWindows版は DirectShow をラッピングしている%%ようなのでカメラの代わりにメディアファイルを読み込めるのは当然といえば当然。ところで実験用にこの手の動画ファイルを使うときは、ファイルタイプに注意です。MPEGやAVIは色空間の変換などしたときにブロックノイズが激しく出て困ることがあります(目に見えづらい色空間を圧縮しているため)。しかしAVIにすると、メモリを喰いすぎたり、ディスクアクセスが激しすぎてメインのプログラムの挙動に問題が出たりしますね。

- dandelionくんによる補足
「DirectShowをラッピングしているようなので」という記述は微妙に違っていて，wikiで公開しているプログラムは，Video for Windows(VFW)をラップしたOpenCVの関数を使っています．DirectShowによるキャプチャを行うにはCVCAMを用いるとよいです．

CVCAMに関しては，
C:\Program Files\OpenCV\otherlibs\cvcam\sample
にサンプルプログラムが入っているので参考になると思います．


- [キャプチャ＆動画ファイル出力](http://chihara.naist.jp/people/2004/kenta-t/OpenCV/pukiwiki/index.php?%A5%AD%A5%E3%A5%D7%A5%C1%A5%E3%A1%F5%C6%B0%B2%E8%A5%D5%A5%A1%A5%A4%A5%EB%BD%D0%CE%CF)

- [膨張・収縮処理](http://chihara.naist.jp/people/2004/kenta-t/OpenCV/pukiwiki/index.php?%CB%C4%C4%A5%A1%A6%BC%FD%BD%CC%BD%E8%CD%FD)
　この関数はGPU化するのは楽そうだな…。

- [色情報による領域抽出](http://chihara.naist.jp/people/2004/kenta-t/OpenCV/pukiwiki/index.php?%BF%A7%BE%F0%CA%F3%A4%CB%A4%E8%A4%EB%CE%CE%B0%E8%C3%EA%BD%D0)
　これもGPU化するのは可能。パラメータはテキストファイル(HLSL)や画像のピクセル値(RGB)で渡したりするのでコンパイル不要。

- [行列計算](http://chihara.naist.jp/people/2004/kenta-t/OpenCV/pukiwiki/index.php?%B9%D4%CE%F3%B7%D7%BB%BB)
　行列演算オペレータ関数があるのはいいね、まあC++ならオペレータ宣言してもいいような気がするけど。

- 以下、未読・未解説
 -マウス入力
 -文字の描画
 -ピクセル単位の色の操作 -> RGBTRIPLE
 -行列の出力
 -高度なGUI
 -基本形
 -カメラ利用の基本形
 -カメラキャリブレーション
 -主成分分析
 -Tach-Mouse(手動作認識)
 -FAGE
 -ボールトラッキング



### Links
- [OpenCV](http://www.intel.com/technology/computing/opencv/index.htm) Official
- [Latest Source](http://sourceforge.net/projects/opencvlibrary/)
- [STL like Template based coding with MMX/SSE extension](https://secure.codeproject.com/useritems/STL_like_coding_with_MMX.asp)  By Hirotaka Niitsuma  
- [OpenCVコミュ@mixi](http://mixi.jp/view_community.pl?id=426809)
- [画像処理 (プログラミング)コミュ@mixi](http://mixi.jp/view_bbs.pl?id=2973204&comm_id=41490&page=all)

### 日本語情報メモ
順不同．他にもあれば追加します．

- [OpenCV@Chihara-Lab.](http://chihara.naist.jp/people/2004/kenta-t/OpenCV/pukiwiki/) NAIST千原研

- [ユダの呟き](http://judas.exblog.jp/3789742/) OpenCVって別にビルドせんでも、インストールできるやんかーーー！！！…という叫び．
- [OpenCV覚書き](http://hawaii.aist-nara.ac.jp/~takash-b/pukiwiki/index.php?OpenCV) NAIST坂東さん，よくまとまってます．Windows+Cygwin環境．関数リストなど充実．
- [OpenCVマニュアル日本語訳](http://robotics.elec.nara-k.ac.jp/opencv/reference.html) 奈良工業高専
- [OpenCV による画像処理](http://www-cv.mech.eng.osaka-u.ac.jp/~hamada/openCV/) 阪大．実行結果のサンプル画像が充実．
- [(tips)](http://www.er.ams.eng.osaka-u.ac.jp/yamamoto/opencv.html) 大阪大学大学院 工学研究科 知能・機能創成工学専攻 先導的融合工学講座 山本さん
- [OpenCVをVisual Studio .NETで使う](http://luvtechno.net/h/?OpenCV) luvtechno.net，概要など．
- [CygwinでOpenCV メモ](http://prog.usamimi.info/blog/108.html) koba news
- [Linux + OpenCV + 1394カメラ HOWTO](http://limu.is.kyushu-u.ac.jp/~yosimoto/work/opencv-howto/) 九州大学YOSHIMOTOさん
- [OpenCVに関する覚え書き](https://www.design.t.u-tokyo.ac.jp/~nakano/opencv.html) せっかくまとまっているのにサイトが消えてしまっています


----

Blog Entries
-[[OpenCVで顔画像認識（2006年10月11日）>http://akihiko.shirai.as/modules/bwiki/index.php?Blog%2F2006-10-11#v4c9a77f]]


<!--

//http://216.239.59.104/search?q=cache:JLUN8ljIGrcJ:www.design.t.u-tokyo.ac.jp/~nakano/opencv.html+OpenCV&hl=ja&gl=jp&ct=clnk&cd=1&lr=lang_ja&client=firefox
//OpenCVに関する覚え書き
//
//画像処理をするために使用．導入方法とか使ったことのある関数などのメモ
//使い方とかのメモ．つまり自分用のメモ.役に立てば幸いです．
//
//インストールと設定
//
//自作プログラムの作成とコンパイル
//
//Microsoft Visual Studio .NET 2003を使ってプログラムを作る
//
//構造体
//
//    * IplImage
//    * CvSize
//    * CvPoint
//    * CvScalar
//    * CvCapture
//    * CvTermCriteria
//    * CvSeq
//    * CvMemStorage
//
//マクロ
//
//関数
//
//    * cvCreateImage
//    * cvCaptureFromCAM
//    * cvNamedWindow
//    * cvMoveWindow
//    * cvQueryFrame
//    * cvShowImage
//    * cvReleaseCapture
//    * cvDestroyWindow
//    * cvLoadImage
//    * cvReleaseMemStorage
//    * cvReleaseImage
//    * cvGetImageRawData
//    * cvWaitKey
//    * cvPoint
//    * cvSize
//    * cvCopy
//    * cvGetAt
//    * cvGet2D
//    * cvSetAt
//    * cvSet2D
//    * cvSet
//    * cvFlip
//    * cvCvtPixToPlane
//    * cvCvtPlaneToPix
//    * cvConvertScaleAbs
//    * cvCvtColor
//    * cvLine
//    * cvRectangle
//    * cvFindContours
//    * cvDrawContours
//    * cvCanny
//    * cvSnakeImage
//    * cvLaplace
//    * cvSmooth
//
//
//
//インストールと設定
//
//googleでOpenCVと検索してくれれば，参考になるページは色々見つかると思います． Libraryはここからダウンロードできます．私はWindows版を使ってます．
//以下の設定は，Windows版のOpenCVをCygwinから使うための設定です．
//Visual Studio .NETのIDEなんかを使うなら，特に環境変数の設定もいらないかも知れません．
//ちなみに，IPLに関してはOpenCVに含まれているみたいで，改めてインストールする必要はありません．
//インストール
//
//ダウンロードしてきたら，適当なフォルダにインストール．ダウンロードしたファイルを実行すれば自動的にインストールできます．
//環境変数の設定
//
//インストールが出来たら，環境変数PATHの設定．＼OpenCV＼bin＼にパスを通します．
//これで，作成したプログラムを実行する際に必要なcxcore096.dll,cv096.dll,highgui096.dllの 3つのファイルを見てくれます．
//
//Cygwinのための設定．
//.bashrcなんかに以下のPATHを追加します．
//
//# nmakeとcl(コンパイラ)とmspdb71.dllのためのパス
//<Install Folder>/Microsoft Visual Studio .NET 2003/Vc7/bin
//<Install Folder>/Microsoft Visual Studio .NET 2003/Common7/IDE"
//<Install Folder>/OpenCV/bin
//
//bashrcにexportで以下のパスを設定しても，VCのコンパイラが/記号でのパスをうまく読んでくれず，失敗．
//bashrcだと＼の扱いかたが分からなかったので，bashrcに追加は断念．
//というわけで，Windowsのユーザ環境変数のINCLUDEとLIBに，以下のパスを追加する．
//これを追加しないと，nmakeでライブラリのコンパイルが出来ない．IDEを使うと設定しなくてもコンパイルできたけど・・・
//
//INCLUDEパス
//C:＼Program Files＼Microsoft Visual Studio .NET 2003＼Vc7＼include;
//C:＼Program Files＼Microsoft Visual Studio .NET 2003＼SDK＼v1.1＼include;
//C:＼Program Files＼Microsoft Visual Studio .NET 2003＼Vc7＼PlatformSDK＼Include
//
//LIBパス
//C:＼Program Files＼Microsoft Visual Studio .NET 2003＼Vc7＼lib;
//C:＼Program Files＼Microsoft Visual Studio .NET 2003＼Vc7＼PlatformSDK＼Lib
//
//
//OpenCVライブラリのコンパイル
//
//以上の設定がすんだら，OpenCV/_makeのディレクトリに行って，
//$ nmake -f makefile.vc
//を実行．これでライブラリのコンパイルが出来るはず．
//環境変数の設定をすっ飛ばして，_makeディレクトリにあるopencv.slnというソリューションファイルを開いてソリューションのビルドを行ってもうまくいくはず．
//
//△top
//
//
//
//
//自作プログラムの作成とコンパイル
//
//上記の設定がすんだら，自分でプログラムを書くなり，人のサンプルプログラムを拾ってくるなりして，コンパイルしましょう．
//サンプルプログラム
//
//色んなサイトを参考にして簡単なプログラムを作成しました．
//以下のプログラムは，USBカメラを差し込んでプログラムを実行すれば，動画のキャプチャが出来ます．
//カメラの画像を取り込んで表示するだけの簡単なプログラム．
//
////---------------------------------------------------------
////Open Source Computer Vision Library
////File Name : sample.cpp
////   OS     : WindowsXP
////Library   : OpenCV for MS-Windows β4a
//// Camera   : USBcamera PMC-30
//// Auther   : NAKANO Michiki
////Time-stamp:<November 02, 2004; 22:18>
////---------------------------------------------------------
//#define WIN32	//Windows以外ではコメント
//
//#include "cv.h"
//#include "highgui.h"
//#include 
//
////グローバル変数群
//IplImage* src = NULL;	//元画像データ
//
////------
////主関数
////------
//int main(){
//  int key;	//キー入力
//  CvCapture* capture = NULL;	//カメラのデバイス
//
//  //カメラが見つからない場合
//  if(NULL==(capture = cvCaptureFromCAM(-1))){
//    printf("カメラが見つかりませんでした．");
//    return -1;
//  }
//
//  //画像表示窓の準備
//  cvNamedWindow("Capture", CV_WINDOW_AUTOSIZE);// 0を代入すると正方形
//  //窓の出現位置
//  cvMoveWindow("Capture", 50, 50);
//  //処理ループの開始
//  for(;;){
//    //キャプチャ側から画像を取り出す
//    if(NULL==(src=cvQueryFrame(capture))){
//      printf("画像の取得ができませんでした．");
//      break;
//    }
//    //画像表示
//    cvShowImage("Capture", src);
//    //キー入力
//    key = cvWaitKey(10);
//    //ESCで終了
//    if(key==0x1b)
//      break;
//  }
//  //解放
//  cvReleaseCapture(&capture);
//  cvDestroyWindow("Capture");
//
//  return 0;
//}
//
//
//makefile
//
//以下，makefileの例です．パスは各自の環境に合わせて設定してください．無駄にパスの設定をしているかもしれませんが気にしないで下さい．
//$ nmake -f makefile
//を実行すれば，コンパイルできます．
//
//##########################################################
//#Makefile for OpenCV
//#File Name : makefile
//#   OS     : WindowsXP
//#Library   : OpenCV for MS-Windows β4a and Original Lib
//# Auther   : NAKANO Michiki
//#Time-stamp:<November 08, 2004; 15:19>
//##########################################################
//
//#コンパイラ
//CC  = cl
//CFLAGS = /nologo /GX /ML /W4 /O1 /D"NDEBUG"
//CPATH = C:＼Program Files＼Microsoft Visual Studio .NET 2003＼Vc7
//CVPATH = C:＼Winapp＼OpenCV
//XINCLUDE = /I"$(CVPATH)＼cxcore＼include" /I"$(CVPATH)＼cv＼include" /I"$(CVPATH)＼otherlibs＼highgui"
//	  /I"$(CVPATH)＼otherlibs＼cvcam＼include" /I"$(CVPATH)＼cvaux＼include"
//
//#リンカ
//LINK = link
//LFLAGS1 =/NOLOGO
//LFLAGS2 = cxcore.lib cv.lib highgui.lib
//XLIB = /LIBPATH:"$(CVPATH)＼LIB" 
//
//#ターゲット
//NAME = sample
//EXE = $(NAME).exe
//OBJ = $(NAME).obj
//
//#生成ルール.サフィックスルール
//.cpp.obj:
//	$(CC) $(CFLAGS) $(XINCLUDE) /c $<
//
//$(EXE): $(OBJ)
//	$(LINK) $(XLIB) $(LFLAGS1) /out:$(EXE) $(OBJ) $(LFLAGS2)
//
//clean:
//	del *.exe *.tds *.obj *.o *.out *.ilk *.pdb
//
//△top
//
//
//
//
//Microsoft Visual Studio .NET 2003を使ってプログラムを作る
//
//Visual Studio .NETの感想は，めちゃくちゃ使い難い．
//ばりばりのWindowsプログラマなら嬉しいツールかもしれないが，UNIXとかでしかプログラミングしたことなく，初心者に毛が生えた程度の私にとっては，全く意味のわからないツール．
//ソリューションってなんだよ！プロジェクトってなんだよ！
//てなわけで，やっとのことで解明した簡単な使い方の覚え書き．
//色々設定
//
//プロジェクトの新規作成で，テンプレートにはWin32コンソールを選択．空のプロジェクトだと駄目．
//プロジェクトのプロパティの設定
//基本的にmakefileに記述したincludeパス，libバス，依存ファイルを設定すればよい．
//
//    * includeパスの設定
//      <Install folder>＼OPENCV＼CV＼INCLUDE
//      <Install folder>＼OPENCV＼CVAUX＼INCLUDE
//      <Install folder>＼OPENCV＼CXCORE＼INCLUDE
//      <Install folder>＼OPENCV＼OTHERLIBS＼HIGHGUI
//      <Install folder>＼OPENCV＼OTHERLIBS＼CVCAM＼INCLUDE
//    * libパスの設定
//    * 依存ファイルの設定
//
//△top
//
//
//構造体
//
//自分が使ったことのある構造体やマクロについてのメモ．
//
//
//IplImage
//ヘッダファイル:cxcore/include/cxtypes.h
//
//typedef struct _IplImage
//{
//    int  nSize;         /* sizeof(IplImage) */
//    int  ID;            /* version (=0)*/
//    int  nChannels;     /* Most of OpenCV functions support 1,2,3 or 4 channels */
//    int  alphaChannel;  /* ignored by OpenCV */
//    int  depth;         /* pixel depth in bits: IPL_DEPTH_8U, IPL_DEPTH_8S, IPL_DEPTH_16S,
//                           IPL_DEPTH_32S, IPL_DEPTH_32F and IPL_DEPTH_64F are supported */
//    char colorModel[4]; /* ignored by OpenCV */
//    char channelSeq[4]; /* ditto */
//    int  dataOrder;     /* 0 - interleaved color channels, 1 - separate color channels.
//                           cvCreateImage can only create interleaved images */
//    int  origin;        /* 0 - top-left origin,
//                           1 - bottom-left origin (Windows bitmaps style) */
//    int  align;         /* Alignment of image rows (4 or 8).
//                           OpenCV ignores it and uses widthStep instead */
//    int  width;         /* image width in pixels */
//    int  height;        /* image height in pixels */
//    struct _IplROI *roi;/* image ROI. if NULL, the whole image is selected */
//    struct _IplImage *maskROI; /* must be NULL */
//    void  *imageId;     /* ditto */
//    struct _IplTileInfo *tileInfo; /* ditto */
//    int  imageSize;     /* image data size in bytes
//                           (==image->height*image->widthStep
//                           in case of interleaved data)*/
//    char *imageData;  /* pointer to aligned image data */
//    int  widthStep;   /* size of aligned image row in bytes */
//    int  BorderMode[4]; /* ignored by OpenCV */
//    int  BorderConst[4]; /* ditto */
//    char *imageDataOrigin; /* pointer to very origin of image data
//                              (not necessarily aligned) -
//                              needed for correct deallocation */
//}
//IplImage;
//
//取り込んだ画像を保持するための構造体．
//
//
//
//CvSize
//ヘッダファイル:cxcore/include/cxtypes.h
//
//typedef struct CvSize
//{
//    int width;
//    int height;
//}
//CvSize;
//
//例
//CvSize sz = cvSize(width, height);
//
//
//
//CvPoint
//ヘッダファイル:cxcore/include/cxtypes.h
//
//typedef struct CvPoint
//{
//    int x;
//    int y;
//}
//CvPoint;
//
//例
//CvPoint pt = cvPoint(x, y);
//
//
//
//CvScalar
//ヘッダファイル:cxcore/include/cxtypes.h
//
//typedef struct CvScalar
//{
//    double val[4];
//}
//CvScalar;
//
//例
//・CvScalar color = CV_RGB(r,g,b); -- RGBで色の設定
//・CvScalar color = cvScalar(a,b,c,d); -- いまいちよくわかりません．
//
//
//
//CvCapture
//ヘッダファイル:otherlibs/highgui/highgui.h
//
///* "black box" capture structure */
//typedef struct CvCapture CvCapture;
//
//例
//CvCapture* capture = cvCaptureFromCAM(-1);
//
//
//
//CvTermCriteria
//ヘッダファイル:cxcore/include/cxtypes.h
//
//typedef struct CvTermCriteria
//{
//    int    type;  /* may be combination of
//                     CV_TERMCRIT_ITER
//                     CV_TERMCRIT_EPS */
//    int    max_iter;
//    double epsilon;
//}
//CvTermCriteria;
//
//例
//CvTermCriteria crit = cvTermCriteria(int type, int max_iter, double epsilon);
//
//typeにはCV_TERMCRIT_ITERやCV_TERMCRIT_EPSなどのマクロを用いるとよい．
//
//
//
//CvSeq
//ヘッダファイル:cxcore/include/cxtypes.h
//
//typedef struct CvSeq
//{
//    CV_SEQUENCE_FIELDS()
//}
//CvSeq;
//
//例
//不明．よくわかりません．
//
//
//
//CvMemStorage
//ヘッダファイル:cxcore/include/cxtypes.h
//
//typedef struct CvMemStorage
//{
//    int     signature;
//    CvMemBlock* bottom;/* first allocated block */
//    CvMemBlock* top;   /* current memory block - top of the stack */
//    struct  CvMemStorage* parent; /* borrows new blocks from */
//    size_t  block_size;  /* block size */
//    size_t  free_space;  /* free space in the current block */
//}
//CvMemStorage;
//
//例
//CvMemStorage *storage = cvCreateMemStorage(); -- いまいちよくわかりません．
//
//
//△top
//
//
//マクロ
//
//自分が使ったことのあるマクロについてのメモ．
//
//
//関数
//
//自分が使ったことのある関数についてのメモ．
//
//
//cvCreateImage
//ヘッダファイル:cxcore/include/cxcore.h
//
//IplImage* cvCreateImage( CvSize size, int depth, int channels );
//
//size - 画像サイズ
//depth - 画像のデプス．256階調なら8とか．IPL_DEPTH_8Uなどのマクロを使うと良い．
//channels - チャンネル数．1だとモノクロ．3,4だとフルカラー．
//
//ヘッダの作成とデータ領域の確保
//
//例
//IplImage* src = cvCreateImage(cvSize(width,height), IPL_DEPTH_8U, 3);
//
//
//
//cvCaptureFromCAM
//ヘッダファイル:otherlibs/highgui/highgui.h
//
//CvCapture* cvCaptureFromCAM(int index);
//
//index - カメラのインデックス
//
//カメラが1つしかなければ，インデックスの値は-1にしておけばよい．
//
//例
//CvCapture* capture = cvCaptureFromCAM(-1);
//
//
//
//cvNamedWindow
//ヘッダファイル:otherlibs/highgui/highgui.h
//
//int cvNamedWindow( const char* name, int flags );
//
//name - ウィンドウの名前
//flags - 0で正方形のウィンドウ CV_WINDOW_AUTOSIZEで自動調整
//
//例
//cvNamedWindow("Sample", CV_WINDOW_AUTOSIZE);
//
//
//
//cvMoveWindow
//ヘッダファイル:/include/.h
//
//例
//Cv = cv;
//
//
//
//cvQueryFrame
//ヘッダファイル:/include/.h
//
//例
//Cv = cv;
//
//
//
//cvShowImage
//ヘッダファイル:/include/.h
//
//例
//Cv = cv;
//
//
//
//cvReleaseCapture
//ヘッダファイル:/include/.h
//
//例
//Cv = cv;
//
//
//
//cvDestroyWindow
//ヘッダファイル:/include/.h
//
//例
//Cv = cv;
//
//
//
//cvLoadImage
//ヘッダファイル:/include/.h
//
//例
//Cv = cv;
//
//
//
//cvReleaseMemStorage
//ヘッダファイル:/include/.h
//
//例
//Cv = cv;
//
//
//
//cvReleaseImage
//ヘッダファイル:/include/.h
//
//例
//Cv = cv;
//
//
//
//cvGetImageRawData
//ヘッダファイル:/include/.h
//
//例
//Cv = cv;
//
//
//
//cvWaitKey
//ヘッダファイル:/include/.h
//
//例
//Cv = cv;
//
//
//
//cvPoint
//ヘッダファイル:/include/.h
//
//例
//Cv = cv;
//
//
//
//cvSize
//ヘッダファイル:/include/.h
//
//例
//Cv = cv;
//
//
//
//cvCopy
//ヘッダファイル:/include/.h
//
//例
//Cv = cv;
//
//
//
//cvGet2D
//ヘッダファイル:/include/.h
//
//例
//Cv = cv;
//
//
//
//cvGetAt
//ヘッダファイル:/include/.h
//
//例
//Cv = cv;
//
//
//
//cvSet2D
//ヘッダファイル:/include/.h
//
//例
//Cv = cv;
//
//
//
//cvSetAt
//ヘッダファイル:/include/.h
//
//例
//Cv = cv;
//
//
//
//cvSet
//ヘッダファイル:/include/.h
//
//例
//Cv = cv;
//
//
//
//cvFlip
//ヘッダファイル:/include/.h
//
//例
//Cv = cv;
//
//
//
//cvCvtPixToPlane
//ヘッダファイル:/include/.h
//
//例
//Cv = cv;
//
//
//
//cvCvtPlaneToPix
//ヘッダファイル:/include/.h
//
//例
//Cv = cv;
//
//
//
//cvConvertScaleAbs
//ヘッダファイル:/include/.h
//
//例
//Cv = cv;
//
//
//
//cvCvtColor
//ヘッダファイル:/include/.h
//
//例
//Cv = cv;
//
//
//
//cvLine
//ヘッダファイル:/include/.h
//
//例
//Cv = cv;
//
//
//
//cvRectangle
//ヘッダファイル:/include/.h
//
//例
//Cv = cv;
//
//
//
//cvFindContours
//ヘッダファイル:/include/.h
//
//例
//Cv = cv;
//
//
//
//cvDrawContours
//ヘッダファイル:/include/.h
//
//例
//Cv = cv;
//
//
//
//cvCanny
//ヘッダファイル:/include/.h
//
//例
//Cv = cv;
//
//
//
//cvSnakeImage
//ヘッダファイル:/include/.h
//
//例
//Cv = cv;
//
//
//
//cvLaplace
//ヘッダファイル:/include/.h
//
//例
//Cv = cv;
//
//
//
//cvSmooth
//ヘッダファイル:/include/.h
//
//例
//Cv = cv;
//
//
//
//: 定義語 | 説明文
//&color(red,black){''hoge''};
//&size(20){インライン要素};
//そういえば((注釈))
//&ref(添付ファイル名);
//&ref(ファイルのURL);
-->

このドキュメントは無保証です．~
This document has no warranty. ~
Created at 2006-01-15 12:39:41



