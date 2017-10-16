# WM_Command SendMessage constants for popular applications

By extracting the **menu** resources from EXE and DLL files, you can often discover the constant to automate those functions yourself in a language like [Autohotkey](www.autohotkey.com) via [SendMessage/PostMessage](https://autohotkey.com/docs/commands/PostMessage.htm). 

**.rc** files are text and resemble the following (taken from Process Monitor):


    CONTEXT_PROCESSTREE MENU
    LANGUAGE LANG_ENGLISH, SUBLANG_ENGLISH_US
    {
        POPUP "Context Menu"
            {
            MENUITEM "&Go To Event", 1058
            MENUITEM "&Add process to Include filter", 40143
            MENUITEM "Add process and &children to Include filter", 40145
            }
    }

To initiate the **&Add process to Include filter** command in Autohotkey, you might do the following:


    #Y::
        menu_constant=40143
        SendMessage, 0x111, menu_constant, 0,, A
    Return

This uses the **Windows+Y** key combination to send the command to the active window, which in this case would be Process Monitor.
