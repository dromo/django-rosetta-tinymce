Objective: to handle specific edge cases where translations require HTML as input.

Requirements:

* TinyMCE (http://www.tinymce.com/)
* TinyMCE configuration file (see below for example) 

Required variables in settings.py:

ROSETTA_TINYMCE_ENABLED = True    
ROSETTA_TINYMCE_JS_URL = '/static/js/tiny_mce/tiny_mce.js'    
ROSETTA_TINYMCE_CONFIG_URL = '/static/js/rosetta_tinymce_config.js'  

ROSETTA_TINYMCE_ENABLED = <True OR False>
ROSETTA_TINYMCE_JS_URL = <URL of TinyMCE tiny_mce.js>
ROSETTA_TINYMCE_CONFIG_URL = <URL of TinyMCE configuration> 

[simple TinyMCE configuration - refer to http://www.tinymce.com/wiki.php for more details]
***
tinyMCE.init({                                                                                                                                     mode : "textareas",                                                                                                                        width : "350",                                                                                                                                 height : "150",                                                                                                                                theme_advanced_toolbar_location : "top",                                                                                                       plugins : 'preview, searchreplace, paste, table, insertdatetime, media',                                                                       theme_advanced_buttons1 :  'cut,copy,paste,pastetext,bullist,numlist,blockquote,link,unlink,anchor,image,cleanup,help,code',               theme_advanced_buttons2 :  'bold,italic,underline,strikethrough,fontselect,fontsizeselect'                                                     }); 
***
The example above will enable Rich Text Editor (RTE) across all "textarea" HTML elements on the page. 
If you need to handle specific field in TinyMCE you need to add additional event handling as add/remove TinyMCE per request. Again look at TinyMCE docs for this - something along these lines:

tinyMCE.execCommand('mceAddControl', false, 'the_textareas_id_here');
tinyMCE.execCommand('mceFocus', false, 'the_textareas_id_here');                    
tinyMCE.execCommand('mceRemoveControl', false, 'the_textareas_id_here');

Enjoy,
