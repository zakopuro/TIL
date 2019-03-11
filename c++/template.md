# テンプレート関数
一般的な二つの変数の合計を返す関数の場合。
```cpp
int Add(int iA, int iB) {
    return iA + iB;
}
```
しかし、これではdouble型などに対応しておらず、double型の引数を利用した場合は以下のような別関数を用意する必要がある。
```cpp
double Add(double dA, double dB) {
       return dA + dB;
}
```
テンプレート関数はこのような型を入力時に決めることで対応できるものである。

例
```cpp
template<typename T_n>  // typenameはclassと記載してもよい
T_n Add(T_n tnA, T_n tnB){
    return tnA + tnB;
}
```

利用例
```cpp
int main(){
  double dValue;
  int    iValue;
  // int    iValue2;
  int    iValue3;
  
  dValue = Add(1.3,2.4);    // 戻り値引数共にdouble型となる。
  iValue = Add(1,2);        // 戻り値引数ともにint型になる
  // iValue2 = Add(2.3,1);      // 型が一つしか宣言されていないのに対し、double,int両方があるためコンパイルエラーとなる
  iValue3 = Add<int>(2.3,1);  // <int>宣言をすることにより引数がint型に変換され処理がされる。 2.3 -> 2となる
  
  printf("dValue:%f,iValue:%d,iValue3:%d",dValue,iValue,iValue3);
  return 0;
}
```
