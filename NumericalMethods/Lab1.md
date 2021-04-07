# Teoria błędów

## Obliczenie wartości wielomianu Wn(x) – rozwinięcie funkcji f(x) w szereg Taylora.
Wn(x)=f(x0)+f (1) (x0)/1! (x −x0)+f (2)( x0)/2! (x −x0)2+...+ f (n)(x0)/n! (x −x0)^n

### Dane: f (x)=ex x0=3 n=12

1. W(x) dla exp(3)= 2.71828
2. W(x) dla exp(3)= 8.15485
3. W(x) dla exp(3)= 13.5914
4. W(x) dla exp(3)= 17.2158
5. W(x) dla exp(3)= 19.028
6. W(x) dla exp(3)= 19.7528
7. W(x) dla exp(3)= 19.9945
8. W(x) dla exp(3)= 20.0635
9. W(x) dla exp(3)= 20.0808
10. W(x) dla exp(3)= 20.0846
11. W(x) dla exp(3)= 20.0854
12. W(x) dla exp(3)= 20.0855
13. W(x) dla exp(3)= 20.0855

```
#include <iostream>
#include <cmath>

using namespace std;

int silnia(int a){
  double s = 1;
  for (int i = 1; i <= a; i++){
    s = s*i;
  } 
  return s;
}

int main(){
int x0 = 1;
int x = 3;
int n = 12;
double suma = 0;
for (int i = 0; i <= n; i++){
  if (i == 0)
  suma = exp(x0);
  else
  suma = suma + ((pow(x0, i)*exp(x0)) / silnia(i))*pow((x - x0), i);
  cout <<i+1<< ". W(x) dla exp(3)= " << suma << endl;
  }
system("pause");
return 0;
}
```
## 2. Obliczenie wartości reszty Lagrange'a.
rn( x )= f (n+1)(c ) (n+1)! (x−x0)n+ 1 , gdzie x0<c<x lub x<c< x0

### a) Obliczenie wartości funkcji exp(3)

Dla kolejnych iteracji:
1. Wartosc funkcji: 8.15485 Reszta Lagrange'a: 14.7781
2. Wartosc funkcji: 13.5914 Reszta Lagrange'a: 9.85207
3. Wartosc funkcji: 17.2158 Reszta Lagrange'a: 4.92604
4. Wartosc funkcji: 19.028 Reszta Lagrange'a: 1.97041
5. Wartosc funkcji: 19.7528 Reszta Lagrange'a: 0.656805
6. Wartosc funkcji: 19.9945 Reszta Lagrange'a: 0.187659
7. Wartosc funkcji: 20.0635 Reszta Lagrange'a: 0.0469146
8. Wartosc funkcji: 20.0808 Reszta Lagrange'a: 0.0104255
9. Wartosc funkcji: 20.0846 Reszta Lagrange'a: 0.0020851
10. Wartosc funkcji: 20.0854 Reszta Lagrange'a: 0.000379108

Dla x0=1 exp(3) = 20.0855
```
#include<iostream>
#include<cmath>
using namespace std;
int silnia(int a){
  double s = 1;
  for(int i=1;i<=a;i++){
    s = s*i;
  } 
  return s;
}

int main(){
  double x = 3;
  double x0 = 1;
  double c = (x + x0) / 2;
  int n = 12;
  int i = 1;
  double suma = exp(x0);
  double e = 0.001;
  double rl;
  do{
    suma = suma + ((exp(x0) / silnia(i))*pow((x-x0),i));
    rl = ((exp(c) / silnia(i + 1))*(pow(x-x0, i+1)));
    cout <<i<< ".\t Wartosc funkcji: " << suma << "\t Reszta Lagrange'a: "<<rl<<endl;
    i++;
    }
  while (e <= rl);
  cout << "\nDla x0=1 exp(3) = " << exp(3)<<endl;
  system("pause");
  return 0;
}
```
### b) Obliczenie wartości funkcji sin45˚

Wynik = 0.768813 Reszta Lagrange'a = -0.00538492
Wynik = 0.766121 Reszta Lagrange'a = 0.000234961
sin(pi/4)= 0.766044
```
#include<iostream>
#include<cmath>
using namespace std;
int silnia(int a){
  double s = 1;
  for(int i=1;i<=a;i++){
    s = s*i;
  }
return s;
}

int main (){
  const double PI = 3.14159;
  double x = PI / 4;
  double x0 = 100 * PI / 360;
  double e = 0.001;
  double rl;  
  double suma = sqrt(2) / 2;
  int i = 1;
  do{
    suma = suma + ((pow(-1, i + 1)*(sqrt(2) / 2) / silnia(i))*(pow(x0-x, i)));
    rl = (((pow(-1, i)*(sqrt(2) / 2)) / silnia(i))*(pow(x0-x, i + 1)));
    cout << "Wynik = " << suma << "\t Reszta Lagrange'a = " << rl << endl;
    i++;
    } 
  while (abs(rl) >= e);
  system("pause");
}
```
