bootstrapduallistbox
====================

Dual List Box using Bootstrap 3

This is NOT my work, the original work is at
http://www.virtuosoft.eu/code/bootstrap-duallistbox/

The functionality of dual list box works fine however I was not able to use the final selected listbox values in form POST. Hence I modified little piece of code and uploaded here.

Files to include:
<code>
<script src="js/duallistbox/jquery.bootstrap-duallistbox.js"></script>
<link rel="stylesheet" type="text/css" href="js/duallistbox/bootstrap-duallistbox.css">
</code>

Form Element:

<code>

<select id="element" name="myselect" multiple style="height:200px">
<option value="1">Element 1</option>
<option value="2">Element 2</option>
<option value="3">Element 3</option>
</select>
</code>

Javascript:
Comment/Uncomment whatever you need.

<code>
$(function () { 
        $('#element')
                .bootstrapDualListbox({
                    bootstrap2Compatible: false,
                   // moveAllLabel: 'MOVE ALL',
                  //  removeAllLabel: 'REMOVE ALL',
                   // moveSelectedLabel: 'MOVE SELECTED',
                  //  removeSelectedLabel: 'REMOVE SELECTED',
                    //filterPlaceHolder: 'FILTER',
                    //filterSelected: '2',
                   // filterNonSelected: '1',
                    moveOnSelect: false,
                    preserveSelectionOnMove: 'all',
                    helperSelectNamePostfix: '_myhelper',
                    selectedListLabel: 'Assigned Members',
                    nonSelectedListLabel: 'All Members'
                })
               // .bootstrapDualListbox('setMoveAllLabel', 'Move all teh elementz!!!')
               // .bootstrapDualListbox('setRemoveAllLabel', 'Remove them all!')
                //.bootstrapDualListbox('setSelectedFilter', undefined)
                //.bootstrapDualListbox('setNonSelectedFilter', undefined)
               // .append('<option>added element</option>')
                //.bootstrapDualListbox('refresh')
    });
</code>
I had to write this so that all elements are selected before form is submitted and it gets passed to $_POST or $_GET method.

<code>
$('#bootstrap-duallistbox-selected-list_myselect option').each(function(i) {
  $(this).attr("selected", "selected");
 });
</code>

PHP Code:

The final listbox will have name = Original Select Name _ "myhelper2".In this example, it will be myselect_myhelper2[].

    foreach ($_POST['myselect_myhelper2'] as $v)
      {
	// $v contains values of selected items in listbox
      }

Contact me for any queries at anandatheerthan@gmail.com