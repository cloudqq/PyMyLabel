# PyMyLabel
A minimal example of using SIP to create a Python wrapper for a C++ Qt5 library.

## Prerequisites
This example was written and tested with the following configuration:
 - Python 3.4
 - Qt5.4
 - SIP 4.16.8
 - PyQt5.4.2

## Configuring and Compiling
The first step is run the following command:

    $ python configure.py

This will use SIP to generate the necessary C/C++ wrapper code and will create Makefile's for the library itself and the wrapper.

Now you can build and install the library:

    $ make
    $ make install

## Usage Example

    from PyQt5.QtCore import *
    from PyQt5.QtGui import *
    from PyQt5.QtWidgets import *
    from PyMyLabel import MyLabel
    
    class Widget(QWidget):
        def __init__(self, parent=None, **kwargs):
            super().__init__(parent, **kwargs)
            
            l=QVBoxLayout(self)
            self._myLabel=MyLabel(self)
            l.addWidget(self._myLabel)
            
    if __name__=="__main__":
        from sys import argv, exit
        
        a=QApplication(argv)
        w=Widget()
        w.show()
        w.raise_()
        exit(a.exec_())
