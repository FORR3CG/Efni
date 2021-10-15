# Efni fyrir FORR3CG

## Þróunarumhverfi

### Linux

Mismunandi eftir dreifingum en fyrir t.d. Ubuntu, keyra eftirfarandi í terminal:

```sudo apt install build-essential gdb```

### macOC

Opna terminal og keyra eftirfarandi skipun:

```xcode-select --install```

### Windows

Byrja á að setja upp Ubuntu í Windows Subsystem for Linux, sjá leiðbeiningar [hér](./WSL.md).

Þegar því er lokið (muna að uppfæra Ubuntu), þarf að keyra eftirfarandi línu í Ubuntu terminal:

```sudo apt install build-essential gdb```

#### Tengja VSCode við Ubuntu í Windows

Við viljum keyra VSCode í Windows en þýða (e. compile) og keyra forritin með Ubuntu vélinni. Við þurfum því að segja VSCode hvernig það á að nálgast Ubuntu vélina.

Til að þetta sé hægt þarf að setja inn viðbótina *Remote - WSL* í VSCode.

![Remote - WSL Extension](Myndir/VSCode_RemoteWSL_Extension.png)

### VSCode - öll stýrikerfi

Sækja og setja upp Visual Studio Code ef það er ekki þegar sett upp á vélinni.

Búa sér til eina möppu sem kemur til með að innihalda öll forritin sem þið skrifið í áfanganum.

Dæmi:

- Linux: ```/home/nafn/Documents/Skóli/FORR3CG```
- macOS: ```/Users/nafn/Documents/Skóli/FORR3CG```
- Windows: ```C:\Users\nafn\Documents\Skóli\FORR3CG```

**ATH.** Öll forrit sem við skrifum í áfanganum þurfa að eiga sér sína eigin möppu. Þær möppur þurfa að vera í FORR3CG möppunni.

Í þeirri möppu (t.d. FORR3CG) þarf að búa til aðra möppu sem á að heita ```.vscode``` (ath. punkturinn er hluti af nafninu).

Í ```.vscode``` möppunni þarf svo að búa til skránna ```tasks.json``` og í þá skrá þarf að afrita eftirfarandi:

```json
{
    // See https://go.microsoft.com/fwlink/?LinkId=733558
    // for the documentation about the tasks.json format
    "version": "2.0.0",
    "tasks": [
      {
        "label": "build",
        "type": "shell",
        "command": "g++ -g -Wall \"${fileDirname}/\"*.cpp -o ${workspaceFolderBasename} && ./${workspaceFolderBasename}",
        "problemMatcher": []
      }
    ]
  }
```

Næst þarf að setja inn C++ viðbótina (e. extension) í VSCode með því að fara í Extensions (Ctrl+Shift+x / Cmd+Shift+x) og leita að C++. Setja svo inn viðbótina frá Microsoft.

![VSCode c++ extension](./Myndir/VSCode_CPP_Extension.png)
