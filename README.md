# troff-pygments
Syntax highlighting pre-processor for Heirloom Troff (written in Python language)

## Usage

    usage: troff-pygments [-h] [--style STYLE] [filename]
    
    positional arguments:
      filename
    
    optional arguments:
      -h, --help            show this help message and exit
      --style STYLE, -s STYLE
                            Select a style from Pygments
    
If no filename is provided, standard input is read.

## Troff macros
The preprocessor adds two new macros which are `.PYGMENTS1` and `.PYGMENTS2` (for enclosing a block to be highlighted). Both commands are kept by the preprocessor and they should be redefined by the user (for selecting a font for instance); however the user doesn't have to put the `.nf` and `.fi` commands wich are added by the preprocessor.

The initial macro `.PYGMENTS1' must have exactly one argument which is the name of a Lexer from the Pygments package. For instance:

    .PYGMENTS1 PythonLexer
    print "test"
    .PYGMENTS2

The list of available lexers can be found at (http://pygments.org/docs/lexers/).

If needed, the two macros may also be written with some indentation:

    .  PYGMENTS1 PythonLexer
    .  PYGMENTS2

The whole code may contain escape characters or have lines starting with a dot with no trouble.
