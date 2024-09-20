# PICKSTYLE

Pick the correct style for source files.

## GNU Emacs integration.

Add the following to your `~/.emacs.d/init.el`:

    (defun pickstyle ()
      (replace-regexp-in-string
       "\n\\'" ""
       (let ((default-directory "~/"))
         (shell-command-to-string
          (concat "sh -c "
                  "\""
                  "pickstyle -D " buffer-file-name " 2>/dev/null || echo 'k&r'"
                  "\"")))))
    
    (defun pickstyle-show ()
      (interactive)
      (message (pickstyle)))
    
    (defun pickstyle-set ()
      (interactive)
      (c-set-style (pickstyle)))
    
    (add-hook 'c-mode-common-hook 'pickstyle-set)

## Help

descstyle

    Usage: descstyle {-l | -udtc STYLE }
    
    Get programming style information from "share/styles/STYLE" which
    follow the following format.
    
      url: URL
      desc: Awesome style.
      text: This project follows the Awesome style.
      check: check-awesome-style %f
    
    Use this program for placing references to the style in the README.

pickstyle

    Usage: pickstyle {-l | -c | [-D] [FILE] }
    
    This program returns the indentation style to use with files. The
    configuration file format is as follows:
    
        FILE_REGEX     STYLE
    
    The configuration files are read in order: $PICKSTYLE_FILE,
    ~/.pickstyle, ~/.local/etc/pickstyle/* and  /etc/pickstyle/*.
    
    The program maintains a cache in ~/.cache/pickstyle, it can be
    refreshed with "-c". With "-l" you can view the list.
    
    If upwards a "./pkg/STYLE" file exists the style is read from it.
    When "-D" is specified the default style in "/etc/cstyle" is checked
    out too, and without any options inferred from the system.

## Collaborating

For making bug reports, feature requests and donations visit
one of the following links:

1. [gemini://harkadev.com/oss/](gemini://harkadev.com/oss/)
2. [https://harkadev.com/oss/](https://harkadev.com/oss/)
