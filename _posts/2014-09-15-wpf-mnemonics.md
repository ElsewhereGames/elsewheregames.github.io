---
published: false
---

### Mnemonics is Hard to Type
If the content of a [Label](http://msdn.microsoft.com/en-us/library/system.windows.controls.label.aspx) is a string which contains an underscore, the label will become a mnemonic label. Specify a control (e.g. a [TextBox](http://msdn.microsoft.com/en-us/library/system.windows.controls.textbox.aspx)) using the ```Target``` property of the label, and pressing `alt` and the letter which comes after the underscore will give focus to that target control.

For example, if you put the following [XAML](http://msdn.microsoft.com/en-us/library/ms752059.aspx) into a view, and press `alt+u`, the textbox will receive focus.

```csharp
<StackPanel>
         
    <Label 
        Content     = "This is a string with an _underscore." 
        Target      = "{Binding ElementName=TestTextBox}" 
    />
        
    <TextBox Name="TestTextBox" />
        
</StackPanel>
```

### It's No Longer Turtles All the Way Down
Kind of a neat feature, but it became a problem in the code-base I am working in; There is a section of the view code which searches up the view hierarchy to find out if a an element is part of a list or not. This (legacy) code looks at the ```OriginalSource``` property of the mouse event and calls ```VisualTree.GetParent``` until it either finds a row view (indicating the item is in that list) or null. If you check the documentation for [GetParent](http://msdn.microsoft.com/en-us/library/system.windows.media.visualtreehelper.getparent.aspx), you will see that the remarks say that the dependency object you provide `can represent either a Visual or Visual3D object.` The thing is, unless it is either of those types, this operation will throw an [InvalidOperationException](http://msdn.microsoft.com/en-us/library/system.invalidoperationexception.aspx)!

When a label does *not* have mnemonic content, the ```OriginalSource``` property will be a [TextBlock](http://msdn.microsoft.com/en-us/library/system.windows.controls.textblock.aspx), a [Visual](http://msdn.microsoft.com/en-us/library/system.windows.media.visual.aspx) type. However, in the case of a mnemonic label, ```OriginalSource``` will be a [Run](http://msdn.microsoft.com/en-us/library/system.windows.documents.run.aspx), a non-visual type, and will therefore cause the exception to occur.

I don't think the original developer should have used the ```OriginalSource``` property in the first place, but what's done is done. Our solution was to wrap the label content in a TextBlock, which disables the mnemonic behavior and has the nice side effect of us not having to escape the label's contents.