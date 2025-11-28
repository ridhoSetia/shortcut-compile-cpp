# Membuat Shortcut Untuk Compile c++

## 1. Cari tasks: tasks configure default build task

Klik `ctrl + shift + p`, lalu cari `tasks: tasks configure default build task`

![cari-tasks](img/cari-tasks.png)<br>
Klik `enter`


## 2. Pilih C/C++: g++ build active file

![cari-tasks](img/cari-g++.png)<br>
Klik `enter`

Akan muncul file tasks.json di dalam folder .vscode atau jika tidak ingin mengikuti langkah 1 dan 2 bisa buat manual folder .vscode dan tasks.json di dalamnya.

## 3. Ubah isi dari file tasks.json

Copy paste script di bawah ke tasks.json

### 🐧 Linux (Arch, Ubuntu, Debian, Mint, dll.)
```
{
    "tasks": [
        {
            "type": "shell",
            "label": "Compile c++",
            "command": "g++",
            "args": [
                "${file}",
                "-o",
                "${fileDirname}/${fileBasenameNoExtension}.out"
            ]
        },
        {
            "label": "Run",
            "type": "shell",
            "command": "clear && '${fileDirname}/${fileBasenameNoExtension}.out'",
            "dependsOn": ["Compile c++"],
            "group": {
                "kind": "build",
                "isDefault": true
            }
        }
    ],
    "version": "2.0.0"
}
```
<br>

### 🪟 Windows
```
{
    "tasks": [
        {
            "type": "shell",
            "label": "Compile c++",
            "command": "g++",
            "args": [
                "${file}",
                "-o",
                "${fileDirname}\\${fileBasenameNoExtension}.exe"
            ]
        },
        {
            "label": "Run",
            "type": "shell",
            "command": "cmd.exe",
            "args": [
                "/c",
                "cls && \"${fileDirname}\\${fileBasenameNoExtension}.exe\""
            ],           
            "dependsOn": ["Compile c++"],
            "group": {
                "kind": "build",
                "isDefault": true
            }
        }
    ],
    "version": "2.0.0"
}
```
Sekarang dengan klik `ctrl + shift + b` otomatis akan melakukan compile sekaligus menjalankannya.

Berikut merupakan outputnya jika digunakan pada main.cpp.

![file-compile](img/file-hasil-compile.png)

![hasil](img/hasil.png)