#計算とその結果の表示


前節では、100+200=300 と言う式を画面に表示させましたが、
あの時は、100,200,300 と言う数値を直接並べました。
つまり 300 と言う答えの部分は、人間が先に計算していたのです。

しかし、これでは、コンピュータを使っている意味がありません。
この様な計算はコンピュータにやらせるべきでしょう。

C言語では、計算するには数式を記述するだけで済みます。
次のプログラムは、100+200 の計算をコンピュータにやらせる例です。

```
int main(void)
{
	100+200;
}

```

このプログラムの実行結果は、次の通りになります。


画面には、何の結果も表示されていません。
これは当然で、先ほどのプログラムは、100+200 を計算しろとしか書かれておらず、
計算した結果を表示しろ、とは一切書かれていないからです。
コンピュータは頑固で素直
この様に、コンピュータは頑固であり素直でもあります。
要するに、与えられた命令は全てその通りに素直に実行しますが、
それ以外のことは一切やってくれないという頑固さも持っています。
人間からすれば、計算したら結果を表示するのが当然ですが、
コンピュータにはそんな気配りは全くありません。
では、計算した結果を表示するにはどうするのでしょうか？
もちろん、画面への表示にはprintf関数を使用します。
printf関数で文字を表示したり、数値を数字に変換して表示する方法は知っています。

実は、数式を渡して、数式の計算結果を数字に変換することも可能です。
次のプログラムは、100+200 を計算させて表示する例です。

```
#include <stdio.h>

int main(void)
{
	printf("%d\n",100+200);
	return 0;
}
```

このプログラムの実行結果は、次の通りになります。

`300`

このプログラムで注意してほしいのは、printf関数に渡されるのは、
100+200 と言う式ではなく、その結果である 300 であると言う点です。
100+200 の部分は(printf関数に関係なく)勝手に計算され、300 に変換されます。
そして、その 300 が更に数字に変換され、画面に 300 と表示されたのです。


#四則演算子

前項では、加算(足し算)を行いましたが、もちろん他の計算も可能です。
C言語の基本的な演算子は、次の表の通りです。

C言語での記号
数学での記号
機能

```
+
+
]
加算(足し算)
*
×
乗算(掛け算)
/
÷
除算(割り算)
%
…
剰余算(割り算の余り)
```

この表を見ると、数学とは異なる記号を使うことがあることに気づくと思います。
一般的なコンピュータのキーボードで表現出来る記号には×や÷はないため、
C言語に限らず、多くのプログラミング言語では、別の記号が使われています。

演算子の使い方は数学と全く同じです。
次のプログラムは、ここで紹介した演算子を一通り使ってみる例です。

```
#include <stdio.h>

int main(void)
{
	printf("%d\n",10 + 3);
	printf("%d\n",10 - 3);
	printf("%d\n",10 * 3);
	printf("%d\n",10 / 3);
	printf("%d\n",10 % 3);
	return 0;
}
```

このプログラムの実行結果は、次の通りになります。

```
13
7
30
3
1
```

このプログラムで注目してほしい部分は、
10/3(10÷3)の計算結果が 3 と表示されていることです。
電卓なら、3.3333333 と表示されるのが普通ですが、
ここではどの数値も整数として計算しているので、結果も整数になります。

なお、整数計算の結果は四捨五入ではなく切り捨てとなります。
何故なら、四捨五入を行うと、商×割る数、の逆計算を行ったときに、
その結果が、元の割られる数よりも大きいという矛盾が生じるためです。
安物電卓と高級電卓
実は、この計算は、安物電卓と高級電卓を区別する手軽な方法です。
皆さんもお手持ちの電卓で 10÷3×3 と計算してみて下さい。
筆者が所持している高級電卓では、10 と表示されましたが、
100円ショップの電卓では 9.9999999 と表示されました。
高級電卓では、途中の計算を追跡して正確に表示するそうです。


#複雑な式

C言語で計算出来るのは、何も単純な式だけではありません。
もっと複雑な式であっても、問題なく計算することが出来ます。
次のプログラムは、1～100までの合計を公式で計算する例です。

```
#include <stdio.h>

int main(void)
{　　
	　　printf("%d\n",(1 + 100) * 100 / 2);
	　　return 0;
}
```

このプログラムの実行結果は、次の通りになります。

`5050`

C言語でも、数式での優先順位は、数学と同じです。
乗算や除算は、加算や減算よりも先に計算されます。
優先順位を変えたい時には、() をつけるのも、数学と全く同じです。
ただし、数学では、2重の () には {} を使いますが、C言語では違います。
C言語では、何重の () であっても、() の記号しか使いません。
