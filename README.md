This is a mirror of http://www.vim.org/scripts/script.php?script_id=102

This is a utility that performs a recursive diff on two directories and generate a diff "window".  Based on that window you can perform various diff operations such as opening two files in Vim's diff mode, copy the file or directory recursively to the other, or remove the directory tree from the source directory.
 
Install Details
===============
  Put this file in your ~/.vim/plugin

  Doing the following will generate a diff window.

      :DirDiff <A:Src Directory> <B:Src Directory>
  e.g.
      :DirDiff ../something/dir1 /usr/bin/somethingelse/dir2

  The following commands can be used inside the diff window:
  'Enter','o' - Diff open: open the diff file(s) where your cursor is at
  's' - Synchronize the current diff.  You can also select
        a range (through visual) and press 's' to synchronize differences
        across a range.

        - There are 6 Options you can choose when you hit 's':
          1. A -> B
             Copy A to overwrite B
             If A's file actually points to a directory, it'll copy it to B
             recursively.
          2. B -> A
             Copy B to overwrite A
             If B's file actually points to a directory, it'll copy it to A
             recursively.
          3. Always A
             For the rest of the items that you've selected,
             synchronize like (1).
          4. Always B
             For the rest of the items that you've selected,
             synchronize like (2).
          5. Skip
             Skip this diff entry.
          6. Cancel
             Quit the loop and exit.

  'u' - Diff update: update the diff window
  'x' - Sets the exclude pattern, separated by ','
  'i' - Sets the ignore pattern, separated by ','
  'a' - Sets additional arguments for diff, eg. -w to ignore white space,
        etc.
  'q' - Quit DirDiff
  
  The following comamnds can be used in the Vim diff mode
  \dg - Diff get: maps to :diffget<CR>
  \dp - Diff put: maps to :diffput<CR>
  \dj - Diff next: (think j for down)
  \dk - Diff previous: (think k for up)

  You can set the following DirDiff variables.  You can add the following
  "let" lines in your .vimrc file.

  Sets default exclude pattern:
      let g:DirDiffExcludes = "CVS,*.class,*.exe,.*.swp"

  Sets default ignore pattern:
      let g:DirDiffIgnore = "Id:,Revision:,Date:"

  If DirDiffSort is set to 1, sorts the diff lines.
      let g:DirDiffSort = 1

  Sets the diff window (bottom window) height (rows)
      let g:DirDiffWindowSize = 14

  Ignore case during diff
      let g:DirDiffIgnoreCase = 0

  Dynamically figure out the diff text.  If you are using and i18n version
  of diff, this will try to get the specific diff text during runtime.  It's
  turned off by default.  If you are always targetting a specific version of
  diff, you can turn this off and set the DirDiffText* variables
  accordingly.
      let g:DirDiffDynamicDiffText = 0

  String used for the English equivalent "Files "
      let g:DirDiffTextFiles = "Files "

  String used for the English equivalent " and "
      let g:DirDiffTextAnd = " and "

  String used for the English equivalent " differ")
      let g:DirDiffTextDiffer = " differ"

  String used for the English equivalent "Only in ")
      let g:DirDiffTextOnlyIn = "Only in "
