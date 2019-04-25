---
title: Boîte à outils, onglet HTML | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- vs.toolbox.html
helpviewer_keywords:
- Toolbox, HTML tab
- HTML Designer, setting options
- HTML tab in Toolbox
ms.assetid: 9bfdd3b8-f5ac-4a5f-bdbf-c2b4e97641d8
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: d688e737593ab4eaaeddfe0edcae57c99be4f8ad
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 04/17/2019
ms.locfileid: "59663727"
---
# <a name="toolbox-html-tab"></a>Boîte à outils, onglet HTML
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

L’onglet **HTML** de la boîte à outils fournit des composants utiles sur les pages web et les formulaires web. Pour afficher cet onglet, ouvrez d’abord un document pour le modifier dans le concepteur HTML. Dans le menu **Affichage**, cliquez sur **Boîte à outils**, puis sur l’onglet **HTML** de la boîte à outils.  
  
 Pour créer une instance d’un outil sous l’onglet **HTML**, double-cliquez sur l’outil pour l’ajouter à votre document au point d’insertion actuel, ou sélectionnez l’outil et faites-le glisser à la position souhaitée dans la surface d’édition.  
  
## <a name="tasks"></a>Tâches  
  
-   [Comment : gérer la fenêtre Boîte à outils](http://msdn.microsoft.com/a022c3fe-298c-4a59-a48f-b050da90ebc2)  
  
-   [Comment : manipuler des onglets de boîte à outils](http://msdn.microsoft.com/21285050-cadd-455a-b1f5-a2289a89c4db)  
  
## <a name="ui-elements"></a>Éléments de l'interface utilisateur  
 Les outils suivants sont disponibles par défaut sous l’onglet HTML.  
  
 **Pointeur**  
 ![Pointeur HTMLpage de concepteur ASP.NET mobile](../../ide/reference/media/vxpointer.gif "vxPointer")  
  
 Cet outil est sélectionné par défaut quand un onglet de boîte à outils s’ouvre. Il ne peut pas être supprimé. Le pointeur vous permet de faire glisser des objets sur la surface en mode Design, de les redimensionner et de les repositionner sur la page ou le formulaire. Pour plus d’informations, consultez [Comment : gérer la fenêtre Boîte à outils](http://msdn.microsoft.com/a022c3fe-298c-4a59-a48f-b050da90ebc2) et [Comment : manipuler des onglets de boîte à outils](http://msdn.microsoft.com/21285050-cadd-455a-b1f5-a2289a89c4db).  
  
 **Input (Button)**  
 ![Bouton de page web HTML](../../ide/reference/media/vxbutton.gif "vxButton")  
  
 Insère un élément `input` tel que `type="button"`. Pour changer le texte affiché, modifiez la propriété `name`. Par défaut, `id="Button1"` est inséré pour le premier bouton, `id="Button2"` pour le deuxième, etc.  
  
 Quand vous faites glisser **Input (Button)** sur la surface en mode Design, une balise HTML similaire à ce qui suit est insérée dans votre document :  
  
```  
<input id="Button1" type="button" value="Button" name="Button1">  
```  
  
 Pour plus d’informations, voir [Contrôles de saisie HTML](http://msdn.microsoft.com/library/2ba82c6b-dff7-4b73-b1c2-9e76a48a69de), [Syntaxe déclarative du contrôle serveur HtmlInputButton](http://msdn.microsoft.com/99ccf7fb-7e2a-4ba1-bcd9-981b619a16aa), [NIB : Guide pratique pour créer des scripts et modifier des gestionnaires d’événements](http://msdn.microsoft.com/69d71d13-c68b-4ecd-869b-a42edf6d1f6d), [Représentation du contenu des contrôles serveur web de type bouton](http://msdn.microsoft.com/library/66b3ce28-3b93-4f0a-951f-42fb5bb5fddf), <xref:System.Web.UI.HtmlControls.HtmlInputButton>, <xref:System.Web.UI.HtmlControls.HtmlButton> et <xref:System.Web.UI.WebControls.Button>.  
  
 **Input (Reset)**  
 ![Capture d’écran de HTMLpageResetButton](../../ide/reference/media/vxreset.gif "vxReset")  
  
 Insère un élément `input` tel que `type="reset"`. Pour changer le texte affiché, modifiez la propriété `name`. Par défaut, `id="Reset1"` est inséré pour le premier bouton de réinitialisation, `id="Reset2"` pour le deuxième, etc.  
  
 Quand vous faites glisser **Input (Reset)** sur la surface en mode Design, une balise HTML similaire à ce qui suit est insérée dans votre document :  
  
```  
<input id="Reset1" type="reset" value="Reset" name="Reset1">  
```  
  
 Pour plus d’informations, voir [Contrôles de saisie HTML](http://msdn.microsoft.com/library/2ba82c6b-dff7-4b73-b1c2-9e76a48a69de), [Syntaxe déclarative du contrôle serveur HtmlInputReset](http://msdn.microsoft.com/cfc1f1fb-d33a-464d-9bb5-204e66174979), <xref:System.Web.UI.HtmlControls.HtmlInputButton> et <xref:System.Web.UI.WebControls.Button>.  
  
 **Input (Submit)**  
 ![Capture d’écran de HTMLpageToolbarSubmitButton](../../ide/reference/media/vxsubmit.gif "vxSubmit")  
  
 Insère un élément `input` tel que `type="submit"`. Pour changer le texte affiché, modifiez la propriété `name`. Par défaut, `id="Submit1"` est inséré pour le premier bouton d’envoi, `id="Submit2"` pour le deuxième, etc.  
  
 Quand vous faites glisser **Input (Submit)** sur la surface en mode Design, une balise HTML similaire à ce qui suit est insérée dans votre document :  
  
```  
<input id="Submit1" type="submit" value="Submit" name="Submit1">  
```  
  
 Pour plus d’informations, voir [Contrôles de saisie HTML](http://msdn.microsoft.com/library/2ba82c6b-dff7-4b73-b1c2-9e76a48a69de), [Syntaxe déclarative du contrôle serveur HtmlInputSubmit](http://msdn.microsoft.com/eef2a157-f184-4ce9-b256-d1eacc7930f2), <xref:System.Web.UI.HtmlControls.HtmlInputButton> et <xref:System.Web.UI.WebControls.Button>.  
  
 **Input (Text)**  
 ![Capture d’écran de HTMLpageToolbarTextField](../../ide/reference/media/vxtextfield.gif "vxTextfield")  
  
 Insère un élément `input` tel que `type="text"` dans votre document. Pour changer le texte affiché par défaut, modifiez l’attribut `value`. Par défaut, `id="Text1"` est inséré pour le premier champ de texte, `id="Text2"` pour le deuxième, etc.  
  
 Quand vous faites glisser **Input (Text)** sur la surface en mode Design, une balise HTML similaire à ce qui suit est insérée dans votre document :  
  
```  
<input id="Text1" TYPE="text" value="Text Field" name="Text1">  
```  
  
 Pour plus d’informations, voir [Contrôles de saisie HTML](http://msdn.microsoft.com/library/2ba82c6b-dff7-4b73-b1c2-9e76a48a69de), [Syntaxe déclarative du contrôle serveur HtmlInputText](http://msdn.microsoft.com/87060d90-a11c-434d-9fc9-b03a8487041e), [Vue d’ensemble du contrôle serveur web TextBox](http://msdn.microsoft.com/library/ab354bc1-f23a-48fc-93d8-d4d7c1b7396f), <xref:System.Web.UI.HtmlControls.HtmlInputText> et <xref:System.Web.UI.WebControls.TextBox>.  
  
> [!IMPORTANT]
>  Il est recommandé de valider toutes les entrées d’utilisateur. Pour plus d’informations, consultez [Validation des entrées d’utilisateur dans des pages Web ASP.NET](http://msdn.microsoft.com/library/4ad3dacb-89e0-4cee-89ac-40a3f2a85461).  
  
 **Input (File)**  
 ![Champ File de page HTML](../../ide/reference/media/vxfilefield.gif "vxFilefield")  
  
 Insère un élément `input` tel que `type="file"` dans votre document. Par défaut, `id="File1"` est inséré pour le premier champ de fichier, `id="File2"` pour le deuxième, etc.  
  
 Quand vous faites glisser **Input (File)** sur la surface en mode Design, une balise HTML similaire à ce qui suit est insérée dans votre document :  
  
```  
<input id="File1" type="file" name="File1">  
```  
  
 Pour plus d’informations, voir [Contrôles de saisie HTML](http://msdn.microsoft.com/library/2ba82c6b-dff7-4b73-b1c2-9e76a48a69de), [Syntaxe déclarative du contrôle serveur HtmlInputFile](http://msdn.microsoft.com/a817b4a0-056f-4c17-a696-b9fdcde43db6) et <xref:System.Web.UI.HtmlControls.HtmlInputFile>.  
  
> [!IMPORTANT]
>  Il est recommandé de valider toutes les entrées d’utilisateur. Pour plus d’informations, consultez [Validation des entrées d’utilisateur dans des pages Web ASP.NET](http://msdn.microsoft.com/library/4ad3dacb-89e0-4cee-89ac-40a3f2a85461).  
  
 **Input (Password)**  
 ![Champ Password de Visual Studio](../../ide/reference/media/vxpassword.gif "vxPassword")  
  
 Insère un élément `input` tel que `type="password"`. Par défaut, `id="Password1"` est inséré pour le premier champ de mot de passe, `id="Password2"` pour le deuxième, etc.  
  
 Quand vous faites glisser **Input (Password)** sur la surface en mode Design, une balise HTML similaire à ce qui suit est insérée dans votre document :  
  
```  
<input id="Password1" type="password" name="Password1">  
```  
  
 Pour plus d’informations, consultez [Contrôles Input HTML](http://msdn.microsoft.com/library/2ba82c6b-dff7-4b73-b1c2-9e76a48a69de), [Syntaxe déclarative des contrôles serveur HtmlInputPassword](http://msdn.microsoft.com/df703dd0-1624-4e5a-a547-c97f2f331b9f), [Comment : définir un contrôle serveur Web TextBox pour l’entrée de mots de passe](http://msdn.microsoft.com/library/5b5069f3-64a1-435a-aee6-da263f4e6310) et [Procédure pas à pas : validation des entrées d’utilisateur dans une page Web Forms](http://msdn.microsoft.com/library/7141d6ba-34f3-410b-b5cd-2102a24cb436).  
  
> [!IMPORTANT]
>  Si votre application transmet des noms d’utilisateurs et des mots de passe, vous devez configurer votre site web afin qu’il utilise SSL (Secure Sockets Layer) pour chiffrer la transmission. Pour plus d’informations, consultez la rubrique relative à la sécurisation des connexions avec SSL dans le [Guide des opérations IIS](http://go.microsoft.com/fwlink/?linkid=47856). Il est, en outre, recommandé de valider toutes les entrées d’utilisateur. Pour plus d’informations, consultez [Validation des entrées d’utilisateur dans des pages Web ASP.NET](http://msdn.microsoft.com/library/4ad3dacb-89e0-4cee-89ac-40a3f2a85461).  
  
 **Input (Check box)**  
 ![Option Checkbox de boîte à outils de page web HTML](../../ide/reference/media/vxcheckbox.gif "vxCheckbox")  
  
 Insère un élément `input` tel que `type="checkbox"`. Pour changer le texte affiché, modifiez la propriété `name`. Par défaut, `id="Checkbox1"` est inséré pour la première case à cocher, `id="Checkbox2"` pour la deuxième, etc.  
  
 Quand vous faites glisser **Input (Check box)** sur la surface en mode Design, une balise HTML similaire à ce qui suit est insérée dans votre document :  
  
```  
<input id="Checkbox1" type="checkbox" name="Checkbox1">   
```  
  
 Pour plus d’informations, voir [Contrôles de saisie HTML](http://msdn.microsoft.com/library/2ba82c6b-dff7-4b73-b1c2-9e76a48a69de), [Syntaxe déclarative du contrôle serveur HtmlInputCheckBox](http://msdn.microsoft.com/4a509586-89d8-4ccf-a0b8-b9160ce6e4a6), [Vue d’ensemble des contrôles serveur web CheckBox et CheckBoxList](http://msdn.microsoft.com/library/3028dfd3-e2c5-451d-9150-d02c8ffb92bf), <xref:System.Web.UI.HtmlControls.HtmlInputCheckBox> et <xref:System.Web.UI.WebControls.CheckBox>.  
  
 **Input (Radio)**  
 ![Capture d’écran de VisualStudioHTMLpageRadioButton](../../ide/reference/media/vxradio.gif "vxRadio")  
  
 Insère un élément `input` tel que `type="radio"`. Pour changer le texte affiché, modifiez la propriété `name`. Par défaut, `id="Radio1"` est inséré pour la première case d’option, `id="Radio2"` pour la deuxième, etc.  
  
 Quand vous faites glisser **Input (Radio)** sur la surface en mode Design, une balise HTML similaire à ce qui suit est insérée dans votre document :  
  
```  
<input id="Radio1" type="radio" name="Radio1">  
```  
  
 Pour plus d’informations, voir [Contrôles de saisie HTML](http://msdn.microsoft.com/library/2ba82c6b-dff7-4b73-b1c2-9e76a48a69de), [Syntaxe déclarative du contrôle serveur HtmlInputRadioButton](http://msdn.microsoft.com/6e60ff63-cc57-46ef-bf96-e829e204ba33), [Vue d’ensemble des contrôles serveur web RadioButton et RadioButtonList](http://msdn.microsoft.com/library/20eb383c-4b59-432b-bba3-e9d785107747), <xref:System.Web.UI.HtmlControls.HtmlInputRadioButton> et <xref:System.Web.UI.WebControls.RadioButton>.  
  
 **Input (Hidden)**  
 ![Élément Hidden de page HTML](../../ide/reference/media/vxhidden.gif "vxhidden")  
  
 Insère un élément `input` tel que `type="hidden"`. Par défaut, `id="Hidden1"` est inséré pour le premier champ masqué, `id="Hidden2"` pour le deuxième, etc.  
  
 Quand vous faites glisser **Input (Hidden)** sur la surface en mode Design, une balise HTML similaire à ce qui suit est insérée dans votre document :  
  
```  
<input id="Hidden1" type="hidden" name="Hidden1">   
```  
  
 Pour plus d’informations, voir [Contrôles de saisie HTML](http://msdn.microsoft.com/library/2ba82c6b-dff7-4b73-b1c2-9e76a48a69de), [Syntaxe déclarative du contrôle serveur HtmlInputHidden](http://msdn.microsoft.com/4194e44d-1d74-4bfc-9cc7-743a2e1ea5f9) et <xref:System.Web.UI.HtmlControls.HtmlInputHidden>.  
  
 **Textarea**  
 ![Zone de texte de barre d’outils de page HTML](../../ide/reference/media/vxtextarea.gif "vxTextarea")  
  
 Insère un élément `textarea`. Vous pouvez redimensionner la zone de texte ou utiliser les barres de défilement pour afficher le texte qui s’étend au-delà de la zone d’affichage. Pour changer le texte affiché par défaut, modifiez l’attribut `value`. Par défaut, `id="textarea1"` est inséré pour la première zone de texte, `id=" textarea 2"` pour la deuxième, etc.  
  
 Quand vous faites glisser **Textarea** sur la surface en mode Design, une balise HTML similaire à ce qui suit est insérée dans votre document :  
  
```  
<textarea id=" textarea 1 name=" textarea 1" rows=2 cols=20></textarea>   
```  
  
 Pour plus d’informations, voir [Syntaxe déclarative du contrôle serveur HtmlTextArea](http://msdn.microsoft.com/5a103ffa-235b-4452-ba2b-a4fb8ba8cb87), <xref:System.Web.UI.HtmlControls.HtmlTextArea> et <xref:System.Web.UI.WebControls.TextBox>.  
  
> [!IMPORTANT]
>  Il est recommandé de valider toutes les entrées d’utilisateur. Pour plus d’informations, consultez [Validation des entrées d’utilisateur dans des pages Web ASP.NET](http://msdn.microsoft.com/library/4ad3dacb-89e0-4cee-89ac-40a3f2a85461).  
  
 **Table**  
 ![Capture d’écran de HTMLpageToolbarTable](../../ide/reference/media/vxtable.gif "vxTable")  
  
 Insère un élément `table`.  
  
 Quand vous faites glisser **Table** sur la surface en mode Design, une balise HTML similaire à ce qui suit est insérée dans votre document :  
  
```  
<table cellspacing="1" width="75%" border=1> <tr><td></td></tr></table>   
```  
  
 Pour plus d’informations, voir [Syntaxe déclarative du contrôle serveur HtmlTable](http://msdn.microsoft.com/625b06d8-0f69-4112-a1d4-8ef2a9fbcda9), [Vue d’ensemble des contrôles serveur web Table, TableRow et TableCell](http://msdn.microsoft.com/library/2fbd0582-cf69-4c8d-9e35-21f35e2cee1a), <xref:System.Web.UI.HtmlControls.HtmlTable> et <xref:System.Web.UI.WebControls.Table>.  
  
 **Image**  
 ![Élément Image de page HTML](../../ide/reference/media/vximage.gif "vxImage")  
  
 Insère un élément `img`. Modifiez cet élément pour spécifier son texte `src` et `alt`.  
  
 Quand vous faites glisser **Image** sur la surface en mode Design, une balise HTML similaire à ce qui suit est insérée dans votre document :  
  
```  
<img alt="" src="">  
```  
  
 Pour plus d’informations, voir [Syntaxe déclarative du contrôle serveur HtmlImage](http://msdn.microsoft.com/528430e8-ced1-47d1-8db2-942e734a61f6), [Vue d’ensemble du contrôle serveur web Image](http://msdn.microsoft.com/library/096a8d8d-58ee-4ee8-ab82-6594a0f3a0a9), <xref:System.Web.UI.HtmlControls.HtmlImage>, <xref:System.Web.UI.HtmlControls.HtmlInputImage> et <xref:System.Web.UI.WebControls.Image>.  
  
 **Select**  
 ![Liste déroulante de boîte à outils de page HTML](../../ide/reference/media/vxdropdown.gif "vxDropdown")  
  
 Insère un élément `select` de liste déroulante (sans attribut `size`). Par défaut, `id="select1"` est inséré pour la première zone de liste, `id="select2"` pour la deuxième, etc.  
  
 Quand vous faites glisser **Select** sur la surface en mode Design, une balise HTML similaire à ce qui suit est insérée dans votre document :  
  
```  
<select id="select1" name="select1"><option selected></option></select>  
```  
  
 Vous pouvez créer un élément `select` multiligne en augmentant la valeur de la propriété size.  
  
 Pour plus d’informations, voir [Syntaxe déclarative du contrôle serveur HtmlSelect](http://msdn.microsoft.com/ee93bdec-b343-441a-a8ff-56ffcafe9ae5), [NIB : Guide pratique pour créer des scripts et modifier des gestionnaires d’événements](http://msdn.microsoft.com/69d71d13-c68b-4ecd-869b-a42edf6d1f6d), [Vue d’ensemble du contrôle serveur web DropDownList](http://msdn.microsoft.com/library/517dd1a4-8df3-4c9f-8c89-1549a1aee608), [Vue d’ensemble du contrôle serveur web ListBox](http://msdn.microsoft.com/library/c08ee025-787a-408d-858e-a4a5fdb61d97), <xref:System.Web.UI.HtmlControls.HtmlSelect> et <xref:System.Web.UI.WebControls.DropDownList>.  
  
 **Horizontal Rule**  
 ![Élément Horizontal Rule de page HTML](../../ide/reference/media/vxhorizontal.gif "vxHorizontal")  
  
 Insère un élément `hr`. Pour augmenter l’épaisseur de la ligne, modifiez l’attribut `size`.  
  
 Quand vous faites glisser **Horizontal Rule** sur la surface en mode Design, une balise HTML similaire à ce qui suit est insérée dans votre document :  
  
```  
<hr width="100%" size=1>   
```  
  
 Pour plus d’informations, consultez [Horizontal Rule, contrôle HTML](http://msdn.microsoft.com/library/bf6df0a8-9844-404d-8a9a-3455b0180f2f).  
  
 **Div**  
 ![Étiquette de page HTML](../../ide/reference/media/vxlabel.gif "vxLabel")  
  
 Insère un élément `div` qui inclut un attribut `ms_positioning="FlowLayout"`. À l’exception de la largeur et de la hauteur, cet élément est identique à un panneau de mise en page fluide. Pour mettre en forme le texte contenu dans l’élément `div`, ajoutez un attribut `class="stylename"` à la balise d’ouverture.  
  
 Quand vous faites glisser **Div** sur la surface en mode Design, une balise HTML similaire à ce qui suit est insérée dans votre document :  
  
```  
<div ms_positioning="FlowLayout" style="width: 70px; position: relative; height: 15px">Label</div>  
```  
  
 Pour plus d’informations, voir [Contrôle Div HTML](http://msdn.microsoft.com/library/585fa702-4408-4af1-a92b-68d77ee5e995), [Vue d’ensemble du contrôle serveur web Label](http://msdn.microsoft.com/library/990558d1-4b22-4f28-b100-78a434b3c5ac) et <xref:System.Web.UI.WebControls.Label>.  
  
## <a name="see-also"></a>Voir aussi  
 [Boîte à outils](../../ide/reference/toolbox.md)   
 [Standard, onglet de la boîte à outils](http://msdn.microsoft.com/library/35e9320d-fcbd-474b-8b8f-55705e9a1870)   
 [Contrôles HTML](http://msdn.microsoft.com/library/83bc6f7e-a2b5-4fe9-9a34-eb34aef673be)
