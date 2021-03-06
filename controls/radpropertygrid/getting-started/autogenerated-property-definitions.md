---
title: Autogenerated Property Definitions
page_title: Autogenerated Property Definitions
description: Autogenerated Property Definitions
slug: radpropertygrid-getting-started-autogenerated-property-definitions
tags: autogenerated,property,definitions
published: True
position: 1
---

# Autogenerated Property Definitions



## 

Generally, RadPropertyGrid creates its property definitions automatically based on the type of the corresponding properties. Thus the proper editor controls are text fields for string properties, CheckBoxes for Boolean, ComboBoxes for enums. 

  ![](images/RadPropertyGrid_GettingStarted3.png)



However, you are free to change each of the property definitions displayed. What you need to do is to set the __AutoGeneratePropertyDefinitions__ property of RadPropertyGrid to __"True"__ and handle the __AutoGeneratingPropertyDefinition__ event. As it is cancelable, you may reject the creation of a particular property definition.  

The arguments of the __AutoGeneratingPropertyDefinition__ event are:

* __Cancel__ - gets or set a value that indicates whether the operation should be cancelled;

* __PropertyDefinition__ - gets or sets the property definition for each of the properties. You may edit the properties for each of the definitions.
          

* __Binding__ - points to the data member to display/edit in the field
  

* __Description__ - the description of a property
  

* __DisplayName__ - the displayed name
  

* __EditorTemplate__ - DataTemplate for the editor of the property. If left unset, a default editor will be generated
  

* __GroupName__ - group name used to organize properties in categories
  

* __HasNestedProperties__ - indicates whether this property definition has nested property definitions
  

* __NestedProperties__ - the collection of nested properties
  

* __OrderIndex__ - the index of the order
  

* __ParentProperty__ - the parent property of this property definition
            

The AutoGeneratingPropertyDefinition event will be fired for each property of the item, thus enabling you to customize the view on property basis.
So, for example, let us decide on defining a Description for the Background property of RadButton bound to RadPropertyGrid.

#### __[C#]Example 1: AutoGeneratingPropertyDefinition event__

	{{region radpropertygrid-getting-started-autogenerated-property-definitions_0}}
	private void PropertyGrid1_AutoGeneratingPropertyDefinition(object sender, Telerik.Windows.Controls.Data.PropertyGrid.AutoGeneratingPropertyDefinitionEventArgs e)
	  {   
		   if(e.PropertyDefinition.DisplayName == "Background")
		   {
		  	  e.PropertyDefinition.Description = "This property displays the background property of the RadButton";       
		   }
	  }
	{{endregion}}



#### __[VB.NET]Example 1: AutoGeneratingPropertyDefinition event__

	{{region radpropertygrid-getting-started-autogenerated-property-definitions_1}}
	Private Sub PropertyGrid1_AutoGeneratingPropertyDefinition(sender As Object, e As Telerik.Windows.Controls.Data.PropertyGrid.AutoGeneratingPropertyDefinitionEventArgs)
	 If e.PropertyDefinition.DisplayName = "Background" Then
	  e.PropertyDefinition.Description = "This property displays the background property of the RadButton"
	 End If
	End Sub
	{{endregion}}

![](images/RadPropertyGrid_AutogeneratedPropertyDefinitions.png)


