+++
aliases = [ ]
authors = [ "callum"]
categories = [ "Eto" ]
description = "An overview of Eto Native Controls with the minimum code to get started."
keywords = [ "rhino", "developer", "eto", "ui", "ux" ]
languages = [ "C#", "Python" ]
sdk = "eto"
title = "Eto Native Controls"
type = "guides"

[admin]
TODO = ""
origin = ""
picky_sisters = ""
state = ""

[included_in]
platforms = [ "Windows", "Mac" ]

+++

 <!-- cs -- Tested on Win/Mac -->
 <!-- TODO : Include these samples https://developer.rhino3d.com/guides/rhinopython/eto-controls-python/ -->

## Buttons [API](http://pages.picoe.ca/docs/api/html/T_Eto_Forms_Button.htm)
Buttons offer simple click → action functionality.

{{< row >}}
{{< column >}}

<div class="codetab">
  <button class="tablinks1" onclick="openCodeTab(event, 'cs1')" id="defaultOpen1">C#</button>
  <button class="tablinks1" onclick="openCodeTab(event, 'py1')">Python</button>
</div>

<div class="tab-content">
  <div class="codetab-content1" id="cs1">

  ```cs
using Eto.Forms;
using Eto.Drawing;
using Rhino.UI;

var parent = RhinoEtoApp.MainWindowForDocument(__rhino_doc__);

var button = new Button() { Text = "I am a button" };
button.Click += (s, e) => { MessageBox.Show("You clicked me"); };

var dialog = new Dialog()
{
    Padding = 8,
    Content = button
};

dialog.ShowModal(parent);
  ```

  </div>
  <div class="codetab-content1" id="py1">

```py
import scriptcontext as sc

import Rhino
from Rhino.UI import RhinoEtoApp, EtoExtensions

import Eto.Drawing as ed
import Eto.Forms as ef


def show_message(sender, e):
  ef.MessageBox.Show("You clicked me")

parent = RhinoEtoApp.MainWindowForDocument(sc.doc)

dialog = ef.Dialog()
dialog.Padding = ed.Padding(8)

button = ef.Button()
button.Click += show_message
button.Text = "I am a button"

dialog.Content = button
dialog.ShowModal(parent)
```

  </div>
</div>

{{< /column >}}
{{< column >}}

![Eto Button](/images/eto/controls/button.png)

{{< /column >}}
{{< /row >}}

## Drop Down [API](http://pages.picoe.ca/docs/api/html/T_Eto_Forms_DropDown.htm)
Drop Downs store a collection of items and force a user to choose one, drop downs are favourable when the length of data can change or is more than 3-4 items.

{{< row >}}
{{< column >}}

<div class="codetab">
  <button class="tablinks2" onclick="openCodeTab(event, 'cs2')" id="defaultOpen2">C#</button>
  <button class="tablinks2" onclick="openCodeTab(event, 'py2')">Python</button>
</div>

<div class="tab-content">
  <div class="codetab-content2" id="cs2">

```cs
using Eto.Forms;
using Eto.Drawing;
using Rhino.UI;

var parent = RhinoEtoApp.MainWindowForDocument(__rhino_doc__);

string[] items = new [] {
    "Point", "Curve", "Brep",
};

var dropDown = new DropDown()
{
    DataStore = items,
    SelectedIndex = 0
};

var dialog = new Dialog()
{
    Padding = 8,
    Content = dropDown
};

dialog.ShowModal(parent);
```

  </div>
  <div class="codetab-content2" id="py2">

```py
import scriptcontext as sc

import Rhino
from Rhino.UI import RhinoEtoApp, EtoExtensions

import Eto.Drawing as ed
import Eto.Forms as ef

parent = RhinoEtoApp.MainWindowForDocument(sc.doc)

dialog = ef.Dialog()
dialog.Padding = ed.Padding(8)

drop_down = ef.DropDown()
drop_down.DataStore = ["Point", "Curve", "Brep" ]
drop_down.SelectedIndex = 0

dialog.Content = drop_down
dialog.ShowModal(parent)
```

  </div>
</div>

{{< /column >}}
{{< column >}}

![Eto Drop Down](/images/eto/controls/drop-down.png)

{{< /column >}}
{{< /row >}}

## Radio Buttons [API](http://pages.picoe.ca/docs/api/html/T_Eto_Forms_RadioButtonList.htm)
Radio Button Lists store a list of items and force a user to choose one item. Radio Buttons are not suitable for longer lists and instead a [Drop Down](#drop-down) should be preferred.

{{< row >}}
{{< column >}}

<div class="codetab">
  <button class="tablinks4" onclick="openCodeTab(event, 'cs4')" id="defaultOpen4">C#</button>
  <button class="tablinks4" onclick="openCodeTab(event, 'py4')">Python</button>
</div>

<div class="tab-content">
  <div class="codetab-content4" id="cs4">

```cs
using Eto.Forms;
using Eto.Drawing;
using Rhino.UI;

var parent = RhinoEtoApp.MainWindowForDocument(__rhino_doc__);

string[] items = new [] {
    "Earl Grey", "Rooibos", "Oolong",
};


var buttonList = new RadioButtonList()
{
    DataStore = items,
    Orientation = Orientation.Vertical,
    Spacing = new Size(4, 4)
};

var dialog = new Dialog()
{
    Padding = 8,
    Content = buttonList
};

dialog.ShowModal(parent);
```

  </div>
  <div class="codetab-content4" id="py4">

```py
import scriptcontext as sc

import Rhino
from Rhino.UI import RhinoEtoApp, EtoExtensions

import Eto.Drawing as ed
import Eto.Forms as ef

parent = RhinoEtoApp.MainWindowForDocument(sc.doc)

dialog = ef.Dialog()
dialog.Padding = ed.Padding(8)

button_list = ef.RadioButtonList()
button_list.DataStore = ["Earl Grey", "Rooibos", "Oolong"]
button_list.Orientation = ef.Orientation.Vertical
button_list.Spacing = ed.Size(4, 4)

dialog.Content = button_list
dialog.ShowModal(parent)
```

  </div>
</div>

{{< /column >}}
{{< column >}}

![Eto Combo Box](/images/eto/controls/radio-buttons.png)

{{< /column >}}
{{< /row >}}

## Check Boxes [API](http://pages.picoe.ca/docs/api/html/T_Eto_Forms_CheckBox.htm)
Check Boxes can exist individually or as a group by using the CheckBoxGroup.
Check Boxes have 3 states, checked, unchecked and indeterminate. The 3rd state can be set using Null as the Checked value is `bool?`.

{{< row >}}
{{< column >}}

<div class="codetab">
  <button class="tablinks5" onclick="openCodeTab(event, 'cs5')" id="defaultOpen5">C#</button>
  <button class="tablinks5" onclick="openCodeTab(event, 'py5')">Python</button>
</div>

<div class="tab-content">
  <div class="codetab-content5" id="cs5">

```cs
using Eto.Forms;
using Eto.Drawing;
using Rhino.UI;

var parent = RhinoEtoApp.MainWindowForDocument(__rhino_doc__);

var checkBox = new CheckBox()
{
    Text = "Check Please",
    Checked = true,
};

var dialog = new Dialog()
{
    Padding = 8,
    Content = checkBox
};

dialog.ShowModal(parent);
```

  </div>
  <div class="codetab-content5" id="py5">

```py
import scriptcontext as sc

import Rhino
from Rhino.UI import RhinoEtoApp, EtoExtensions
import Eto.Forms as ef
import Eto.Drawing as ed

parent = RhinoEtoApp.MainWindowForDocument(sc.doc)

dialog = ef.Dialog()
dialog.Padding = ed.Padding(8)

check_box = ef.CheckBox()
check_box.Checked = True
check_box.Text = "Check Please"

dialog.Content = check_box
dialog.ShowModal(parent)
```

  </div>
</div>

{{< /column >}}
{{< column >}}

![Eto Combo Box](/images/eto/controls/checkbox.png)

{{< /column >}}
{{< /row >}}


## Text Box [API](http://pages.picoe.ca/docs/api/html/T_Eto_Forms_TextBox.htm)
The Text box is meant for simple, short inputs like an email address, password, name, etc.

{{< row >}}
{{< column >}}

<div class="codetab">
  <button class="tablinks6" onclick="openCodeTab(event, 'cs6')" id="defaultOpen6">C#</button>
  <button class="tablinks6" onclick="openCodeTab(event, 'py6')">Python</button>
</div>

<div class="tab-content">
  <div class="codetab-content6" id="cs6">


```cs
using Eto.Forms;
using Eto.Drawing;
using Rhino.UI;

var parent = RhinoEtoApp.MainWindowForDocument(__rhino_doc__);

var textBox = new TextBox()
{
    TextAlignment = TextAlignment.Center,
    Width = 200,
    PlaceholderText = "example@email.com"
};

var dialog = new Dialog()
{
    Padding = 8,
    Content = textBox
};

dialog.ShowModal(parent);
```

  </div>
  <div class="codetab-content6" id="py6">

```py
import scriptcontext as sc

import Rhino
from Rhino.UI import RhinoEtoApp, EtoExtensions
import Eto.Forms as ef
import Eto.Drawing as ed

parent = RhinoEtoApp.MainWindowForDocument(sc.doc)

dialog = ef.Dialog()
dialog.Padding = ed.Padding(8)

text_box = ef.TextBox()

text_box.TextAlignment = ef.TextAlignment.Center
text_box.Width = 200
text_box.PlaceholderText = "example@email.com"

dialog.Content = text_box
dialog.ShowModal(parent)
```

  </div>
</div>

{{< /column >}}
{{< column >}}

![Eto Combo Box](/images/eto/controls/text-box.png)

{{< /column >}}
{{< /row >}}



## Text Area [API](http://pages.picoe.ca/docs/api/html/T_Eto_Forms_TextArea.htm)
The text area is for longer, multiline text values and offers more options suited to a larger text input.

{{< row >}}
{{< column >}}

<div class="codetab">
  <button class="tablinks7" onclick="openCodeTab(event, 'cs7')" id="defaultOpen7">C#</button>
  <button class="tablinks7" onclick="openCodeTab(event, 'py7')">Python</button>
</div>

<div class="tab-content">
  <div class="codetab-content7" id="cs7">

```cs
using Eto.Forms;
using Eto.Drawing;
using Rhino.UI;

var parent = RhinoEtoApp.MainWindowForDocument(__rhino_doc__);

var textArea = new TextArea()
{
    TextAlignment = TextAlignment.Left,
    AcceptsReturn = true,
    Width = 200,
    Height = 200
};

var dialog = new Dialog()
{
    Padding = 8,
    Content = textArea
};

dialog.ShowModal(parent);
```

  </div>
  <div class="codetab-content7" id="py7">

```py
import scriptcontext as sc

import Rhino
from Rhino.UI import RhinoEtoApp, EtoExtensions
import Eto.Forms as ef
import Eto.Drawing as ed

parent = RhinoEtoApp.MainWindowForDocument(sc.doc)

dialog = ef.Dialog()
dialog.Padding = ed.Padding(8)

text_area = ef.TextArea()

text_area.TextAlignment = ef.TextAlignment.Left
text_area.AcceptsReturn = True
text_area.Width = 200
text_area.Height = 200

dialog.Content = text_area
dialog.ShowModal(parent)
```

  </div>
</div>

{{< /column >}}
{{< column >}}

![Eto Combo Box](/images/eto/controls/text-area.png)

{{< /column >}}
{{< /row >}}

