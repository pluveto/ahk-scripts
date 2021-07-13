SetTitleMatchMode, 2

; 一些 Typora 快捷输入
#IfWinActive Typora
:*:iii::$${left 1}
:*:\vae::\varepsilon
:*:\nfa::\text{{}NFA {}} M = (Q,T,\delta,q_0,F) \text{{} where {}} Q = \{{}\{}}, T = \{{}\{}}, F =\{{}\{}}
:*:\omg::\omega
:*:\{}::\{{}\{}}{left 2}
::.sh::``````shell`n

#IfWinActive
; Ctrl + Alt + S 搜索
^!s::
OldClipboard:= Clipboard
Clipboard:= ""
Send, ^c ;copies selected text
ClipWait
Run http://www.google.com/search?q=%Clipboard%
Sleep 200
Clipboard:= OldClipboard
return

; Ctrl + Alt + F8 更新博客
^!F8::
RunWait, cmd.exe /c cd C:\doc\Projects\cv\util\ && py update.py && pause
return

; Ctrl + Alt + T 打开终端
^!t::ToggleTerminal()

ShowAndPositionTerminal()
{
    WinShow ahk_class CASCADIA_HOSTING_WINDOW_CLASS
    WinActivate ahk_class CASCADIA_HOSTING_WINDOW_CLASS

    ;SysGet, WorkArea, MonitorWorkArea
    ;TerminalWidth := A_ScreenWidth * 0.9
    ;if (A_ScreenWidth / A_ScreenHeight) > 1.5 {
    ;    TerminalWidth := A_ScreenWidth * 0.6
    ;}
    ;WinMove, ahk_class CASCADIA_HOSTING_WINDOW_CLASS,, (A_ScreenWidth - TerminalWidth) / 2, WorkAreaTop - 2, TerminalWidth, A_ScreenHeight * 0.5,
}

ToggleTerminal()
{
    WinMatcher := "ahk_class CASCADIA_HOSTING_WINDOW_CLASS"

    DetectHiddenWindows, On

    if WinExist(WinMatcher)
    ; Window Exists
    {
        DetectHiddenWindows, Off

        ; Check if its hidden
        if !WinExist(WinMatcher) || !WinActive(WinMatcher)
        {
            ShowAndPositionTerminal()
        }
        else if WinExist(WinMatcher)
        {
            ; Script sees it without detecting hidden windows, so..
            WinHide ahk_class CASCADIA_HOSTING_WINDOW_CLASS
            Send !{Esc}
        }
    }
    else
    {
        Run "%LOCALAPPDATA%\Microsoft\WindowsApps\wt.exe"
        Sleep, 1000
        ShowAndPositionTerminal()
    }
}
