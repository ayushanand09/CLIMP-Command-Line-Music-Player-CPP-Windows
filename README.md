# CLIMP-Command-Line-Music-Player-CPP-Windows
CLIMP - Command Line Music Player made exclusively in C++ for windows. It can play, pause and replay music files
#### Description :
This project can be used to play, pause and replay mp3 files of constant bitrate from terminal.

Uses mciSendStringA() function of Windows Multimedia API (winmm.dll) to play mp3 files.

It is restricted to 9 songs in 'Show List'. If more mp3s are present in the songs folder it will only take first 9.

Displays error messege for mp3s which could not be played.

Doesn't change song by itself. Have to select 'next' or 'previous' button.

Stores list of songs in a list.txt file in 'songs' folder.

UI is made manually instead of using libraries like ncurces etc. and mp3s are played using Windows Multimedia API instead of SFML,FMOD etc. since it was a college project 🙂.
Works as a proof of concept. Does not have much practical use.

#### Screenshots :
![image](https://user-images.githubusercontent.com/85148764/120287268-bcbc9000-c2dc-11eb-8727-b914b86e5770.png)

![image](https://user-images.githubusercontent.com/85148764/120287353-ce059c80-c2dc-11eb-99ce-61526ccf04a6.png)

![image](https://user-images.githubusercontent.com/85148764/120287398-d9f15e80-c2dc-11eb-84bf-25f16d77b4c5.png)
#### How to use :
1. Place constant bitrate mp3 files in the 'songs' folder which is in the same directory as the main.cpp file (up to 9 mp3s are supported).
Song filename must follow this convention : (artistname)-(songname)-(duration).mp3 without any whitespace.
Example - OzzyOsbourne-Dreamer-4.44.mp3
Note - Space should not be used in filenames.

2. winmm.lib (static library) must be linked to main.cpp. This could be done in different ways in different IDEs or text editors.
For Visual Studio Code Use -
![image](https://user-images.githubusercontent.com/85148764/120284654-17a0b800-c2da-11eb-822e-450bb5eaa235.png)
Note the addition of '-lwinmm' in the above line.

3. run main.cpp.

#### Working Environment :
C++ Compiler – MinGW gcc x64 (could work on others, not tested)
C++ standard 11 or newer (could work on older versions, not tested)
Operating System – Windows XP(SP1 64 bit) or newer.
Note - terminal should accept ANSI Escape Sequences for the UI to work. (Example - Windows Powershell)

#### Problem Faced :
1. MciSendStrings documentation by Microsoft was very vague and lacked crucial informations like examples to demonstrate the working of its function.
2. MciSendStrings has 2 versions for its string command parameters. One accepts ANSI encoded characters while other accepts UNICODE and there was no proper information available regarding this.
3. To use MciSendStrings we need to link a library called -lwinmm (Windows Multimedia Lib) but there was no direct way to implement this Visual Studio Code as all the development work is done of Visual Studio IDE.
4. Windows Media Library provides very limited options in regards to the attributes of media file such as it could only play mono bit rate audio files with greatly reduced sample rate and hence offering poor sound quality.

We have also implemented error handling so that is any audio file could not be played for any reason the program will automatically skip to the next music in the list.

#### Conclusion :
There are many overheads to make a fully fledged music player via C++, but with the help of above code we have demonstrated a good example of how to make this work on C++ despite of having so many compatibility issues.

#### References
CodeSpeedy - https://www.codespeedy.com/play-and-pause-an-mp3-file-in-cpp/, https://www.codespeedy.com/play-a-part-of-an-mp3-file-in-cpp/

CodeProject - https://www.codeproject.com/Articles/14709/Playing-MP3s-using-MCI

Stackoverflow - https://stackoverflow.com/questions/22253074/how-to-play-or-open-mp3-or-wav-sound-file-in-c-program

Microsoft - https://docs.microsoft.com/en-us/previous-versions/dd757161(v=vs.85), https://docs.microsoft.com/en-us/windows/win32/multimedia/mci-functions?redirectedfrom=MSDN

Domi Yan Medium - https://domiyanyue.medium.com/c-development-tutorial-4-static-and-dynamic-libraries-7b537656163e

Stackoverflow - https://stackoverflow.com/questions/22253074/how-to-play-or-open-mp3-or-wav-sound-file-in-c-program

Github - https://github.com/microsoft/vscode-cpptools/issues/6191
