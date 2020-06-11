# Vocabulary List を LaTex で作った．
## 動機
　講義の提出物で，Vocabulary "LIST" を（Excelでなく） PDF で提出することになり，あとで，語の順番を入れ替えたり，語を制限したりしやすくするために，LaTex を用いた Vocabulary List を作成した．

## 構造
　語を wordsheet.sty という style ファイルに集約し，その中で，単語一つずつに \newcommand で command を割り当てていく．こうすることで，style ファイルを擬似的なデータベースとし，そこから，コマンドで語の情報を取得するという形をとった．この時，語のコマンドを語の spell にすることで，Excel などでソートし易くすることができる．それをそのまま貼り付けるだけで良いため，語の情報の制限がしやすくなるようにした．

　wordsheet 内では，それぞれの語のコマンドが一つの単語カードのように考えている．それぞれのカードは，以下の構造になっている．

 % :: コマンド名を"\C単語"とすることで，衝突回避とソートの容易さを実現している．  
\newcommand{\Cstreamline}{  
\begin{wordcard}  
　\label{n:streamwise}  
　\begin{wordEN}  
　　strealine　% :: 英単語を入力  
　\end{wordEN}  
　\begin{wordJP}  
　　流線　　　% :: 日本語訳を入力  
　\end{wordJP}  
　\begin{ExSentence}  
　　% :: 例文を入力（省略可）  
　　A streamline is defined as a continuous line within the fluid of which the tangent at any point is in the direction of the velocity at that point.\\  
　　流線は，すべての点での流体の速度の接線方向を連続的につなぎ合わせた線として定義される．  
　\end{ExSentence}  
　\begin{wordOr}  
　　% :: 語源を入力（省略可）  
　　stream ← Old English , Old High German : stroum , Greek :   \textgreek{reuma}  
　\end{wordOr}  
　\begin{wordNote}  
　　% :: 備考を入力（省略可）  
　　例文は，"D. J. TRITTON, Physical Fluid Dynamics Second Edition, OXFORD SCIENCE PUBLICATIONS, 1988, p. 73" より  
　\end{wordNote}  
\end{wordcard}  
}  
なお，単語の長さが長い時は，  
\begin{WordEP} ... \end{WordEP} , \begin{WordJP} ... \end{WordJP}  
の組み合わせ，もしくは，より長い，  
\begin{WORDEP} ... \end{WORDEP} , \begin{WORDJP} ... \end{WORDJP}  
を用いる．それぞれ英単語の幅が，

となっている．

## コンパイル
　筆者は，pLaTex → dvipdfmx でコンパイルしている．

## Vocabulary List 
　出力されたものは，それぞれ，index\_normal.pdf と index\_dictionary.pdf が例として出力されている．（一回の操作では，両方出力されない点に注意されたい．）