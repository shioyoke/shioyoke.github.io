---
layout: post
title:  "CHEMKIN-IIの使い方，Part I: ソースコードを見つける"
categories: [Combustion, Simulation]
tags: [CHEMKIN, Usage]
---

# CHEMKIN-IIは古いが便利
　今どきのITエンジニアには信じられないかもしれないが，燃焼界隈では三十年前のレガシーなコードが業界標準として君臨しており，世界中の学生たちがそのカスタマイズを施した結果を論文で発表し続けている．それがFortran77で書かれた気相における反応動力学パッケージCHEMKIN-II<sup>1</sup>であり，燃焼の化学反応を取り扱う研究者はこの先人が築いた偉大な功績を乗り越えるために多くの時間を費やしている<sup>2, 3</sup>．実際のところ，CHEMKIIN-IIがなした功績は大きい．  
- 詳細反応機構，熱力学データ，輸送係数データのパッケージ化で，化学反応の中身をすべて理解しないでも解析ができるように
- 伝播火炎や拡散火炎などの燃焼工学で良く用いられる系の解析が容易にできる  

これらの結果，中身を全く分かっていなくても卒論のデータがなんか出来ていたり，考察１章分が増えたりと大学院生にはうれしいことばかりなのである．
# CHEMKINの種類に注意
　CHEMKIN-IIの紹介をざっとすると，アメリカのSandia Nastional Laboratoriesで開発されたFortran77のコードで，当時の燃焼界隈の有力研究者たちに配布されたらしい<sup>4</sup>．現在時点で，CHEMKINと言及するときにはいくつかの語義があるので注意が必要で，狭義のものから順に，以下のように分けられる．
- ckinterp.fとcklib.fの２つのFortran77ファイルからなる反応動力学サブルーチン集（CHEMKIN-II）
- SENKINやPREMIX，OPPDIFという名で呼ばれる特定の条件での基礎方程式を解くプログラム群（CHEMKIN-II）
- GUIが整備されたCHEMKIN-PROを含めた反応動力学解析のためのツール  

燃焼の研究のために使用する場合は２もしくは３を使用する場合が，CFDのソース項や物性値の計算には1のを使用することになると思う．ちなみに，CHEMKIN-Iは見たことがないが，CHEMKIN-IIIについては文献が公開されている<sup>5</sup>．ただしCHEMKIN-IIIではソースコードが公開されておらず，CHEMKIN-PROの機能の一つとして利用することができるのみである．

# ソースコードを見つける
書く

Sandia National LabolatryのCHEMKINのページ（今は見れない，Way Benchというサービスにアーカイブされている．）に公式ドキュメントのPDFが保管されている．ネットによく転がっている2000年代に発表されたCHEMKIIN-IIIのドキュメントだけでなく，CHEMKIN-IIのドキュメントが含まれている（商用版の機能の表記に惑わされて，不足しているコードを探してしまうことがない）．
https://web.archive.org/web/20080620010814/http://www.ca.sandia.gov/chemkin/docs.html

University of Notre Dame, Joseph M. Powers
List of source code files
https://www3.nd.edu/~powers/ame.60636/chemkin/

# 参照および備考
1. Kee, R.J., Rupley, F.M., and Miller, J.A. Fri . "Chemkin-II: A Fortran chemical kinetics package for the analysis of gas-phase chemical kinetics". United States.
2. お金のある研究室はANSYS提供の商用版CHEMKIN-PROを使うと幸せになれる．ただ，反応数が多すぎて可視化できなくなったり，中で何をやっているのか気になって，結局CHEMKIN-IIを使って解析を行ったり，ソース読み読みする羽目にはなりがちである．
3. C++で書かれたCanteraというコードもあり，PythonやMatlabでの利用が可能らしい．ただ，自分の肌感覚では論文等ででCanteraを使用したという記述はあまり目にしたことがない．それと別に，名前を忘れたがフランスあたりでFortran90のCHEMKIN-IIライクなコードが存在するのをフランス人の博士論文で目にした．入手しようと連絡を取ったが無理だった覚えがある．
4. 1で引用した報告書の末尾には配布先の人名一覧が記載されている．おそらくこのレポートと同時にソースコードが配布されたのではないかと思う．電子メールやWorld Wide Webのない時代のソースコードの展開方法と思うと感慨深い．
5. Kee, R.J., Rupley, F.M., Meeks, E., and Miller, J.A. Wed . "CHEMKIN-III: A FORTRAN chemical kinetics package for the analysis of gas-phase chemical and plasma kinetics". United States. doi:10.2172/481621. https://www.osti.gov/servlets/purl/481621.