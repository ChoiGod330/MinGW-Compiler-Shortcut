```
#include <iostream>
#include <fstream>
#include <thread>
#include <bits/stdc++.h>

using namespace std;

string check(string p) {
    p.pop_back();
    return p;
}

string path = "C:/";
string name = "";
char check1 = '\\';
char check2 = '/';
char check3 = '\"';
char check4 = '.';

int main() {
    cout << "Please ensure you have installed MinGW. This program is only a compiler shortcut. \nPlease go to https://github.com/ChoiGod330/Compile-.cpp-to-.exe for tutorial." << endl;
    cout << "\nMake sure your file do not have \"SPACE\"...";
    ::this_thread::sleep_for(::chrono::seconds(3));
    cout << "\n\n\nPaste your path here (e.g. \"C:\\path\\file.cpp\"):\n";
    cin >> path;

    char last = path.back();
    int i = 0;

    while ((last != check1) && (last != check2)) //Create a usable path and name.
    {  

        if (last != check3){
        i = i + 1;
        name = name + last;
        }

        path = check(path);
        last = path.back();

    }

    reverse(name.begin(), name.end()); //Reverse name.
    last = name.back();

    while (last != check4) //Delete extention from name.
    {

        name = check(name);
        last = name.back();
    }

    if (last == check4){
        name = check(name);
    }
  
    string quo = "\"";
    string st = "";
    st.push_back(path[0]);

    if (st == quo) //Add quotation mark if needed.
    {
        path = path + quo;
    }
    
    string CMD = quo + "cd " + path + " && " + "g++ " + name + ".cpp -o " + name + ".exe" + quo;
    cout << CMD <<endl;
    system(CMD.c_str());
    
    if (system(CMD.c_str()) == 0 ){
        cout << "The file " + name + ".exe has been created in " + path +" successfully! This program will be closed automatically in 5 seconds.";
    }
    else{
        cout << "ERROR!!! This program will be closed automatically in 5 seconds.";
    }
    ::this_thread::sleep_for(::chrono::seconds(5));

}
```
