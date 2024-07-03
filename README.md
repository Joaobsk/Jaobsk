#include<iostream>
#include<string>
#include<map>
#include<vector>
using namespace std;

const string PALAVRA = "MELANCIA";
map<char, bool> chutou;
vector<char> chuteserrados;

bool letraexiste(char chute){
        for (char letra : PALAVRA){
        if(chute == letra){ 
               return true;
        }
    }
     return false;
}

bool errou(){
    for(char letra : PALAVRA){
        if(!chutou [letra]){
            return true;
        }
    }
    return false;
}
bool acertou(){
    return chuteserrados.size() < 5;
}
void imprieme_cabecalho(){
    cout << "**********************"<< endl;
    cout << "***bem vindo a Forca***"<< endl;
    cout << "***********************"<< endl;
    cout << endl;
}
void imprime_erros(){
          cout << "Chutes errados: " ;
        for(char letra : chuteserrados){
            cout << letra << " ";
        }
cout << endl;
}

void imprime_palavra(){
     for(char letra : PALAVRA){
            if (chutou [letra]){
                cout << letra << " ";
            }
            else{
                cout << "_ ";
            }
        }
        cout << endl;
}

void chuta(){
      cout<< "Seu Chute:";
        char chute;
        cin >> chute;

        chutou [chute] = true;

        if (letraexiste(chute)){
            cout <<" Voce acertou! Seu chute esta na PALAVRA. "<< endl;
        }
        else{
            cout << "Voce errou! Seu chute nao esta na PALAVRA. " << endl;
            chuteserrados.push_back(chute);
        }
        cout << endl;
}

int main(){             

imprieme_cabecalho();

    cout << PALAVRA << endl;

       while(errou() && acertou()){

        imprime_erros(); 

        imprime_palavra();

        chuta();

   }

   cout <<"Fim de jogo" << endl;
   if(errou()){
    cout << "Voce perdeu! tente novamente" << endl;
   }
   else{ 
    cout<<"VOCE GANHOOOU! Parabens."<< endl;
   }
   }
