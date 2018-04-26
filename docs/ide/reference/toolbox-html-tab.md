---
title: Boîte à outils, onglet HTML
ms.date: 06/21/2017
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- vs.toolbox.html
helpviewer_keywords:
- Toolbox, HTML tab
- HTML Designer, setting options
- HTML tab in Toolbox
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 4c47ca792c25efe6ef77f3ee3a9baad61e801624
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2018
---
# <a name="toolbox-html-tab"></a>Boîte à outils, onglet HTML

L’onglet **HTML** de la boîte à outils fournit des composants utiles sur les pages web et les formulaires web. Pour afficher cet onglet, ouvrez d’abord un document pour le modifier dans le concepteur HTML. Dans le menu **Affichage**, cliquez sur **Boîte à outils**, puis sur l’onglet **HTML** de la boîte à outils.

 Pour créer une instance d’un outil sous l’onglet **HTML**, double-cliquez sur l’outil pour l’ajouter à votre document au point d’insertion actuel, ou sélectionnez l’outil et faites-le glisser à la position souhaitée dans la surface d’édition.

## <a name="ui-elements"></a>Éléments de l'interface utilisateur

Les outils suivants sont disponibles par défaut sous l’onglet HTML.

**Pointeur**

![Pointeur HTMLpage de concepteur ASP.NET mobile](../../ide/reference/media/vxpointer.gif "vxPointer")

Cet outil est sélectionné par défaut quand un onglet de boîte à outils s’ouvre. Il ne peut pas être supprimé. Le pointeur vous permet de faire glisser des objets sur la surface en mode Design, de les redimensionner et de les repositionner sur la page ou le formulaire. Pour plus d'informations, consultez [Boîte à outils](../../ide/reference/toolbox.md).

**Input (Button)**

![Bouton de page web HTML](../../ide/reference/media/vxbutton.gif "vxButton")

Insère un élément `input` tel que `type="button"`. Pour changer le texte affiché, modifiez la propriété `name`. Par défaut, `id="Button1"` est inséré pour le premier bouton, `id="Button2"` pour le deuxième, etc.

Quand vous faites glisser **Input (Button)** sur la surface en mode Design, une balise HTML similaire à ce qui suit est insérée dans votre document :

```html
<input id="Button1" type="button" value="Button" name="Button1">
```

**Input (Reset)**

![Capture d’écran de HTMLpageResetButton](../../ide/reference/media/vxreset.gif "vxReset")

Insère un élément `input` tel que `type="reset"`. Pour changer le texte affiché, modifiez la propriété `name`. Par défaut, `id="Reset1"` est inséré pour le premier bouton de réinitialisation, `id="Reset2"` pour le deuxième, etc.

Quand vous faites glisser **Input (Reset)** sur la surface en mode Design, une balise HTML similaire à ce qui suit est insérée dans votre document :

```html
<input id="Reset1" type="reset" value="Reset" name="Reset1">
```

**Input (Submit)**

![Capture d’écran de HTMLpageToolbarSubmitButton](../../ide/reference/media/vxsubmit.gif "vxSubmit")

Insère un élément `input` tel que `type="submit"`. Pour changer le texte affiché, modifiez la propriété `name`. Par défaut, `id="Submit1"` est inséré pour le premier bouton d’envoi, `id="Submit2"` pour le deuxième, etc.

Quand vous faites glisser **Input (Submit)** sur la surface en mode Design, une balise HTML similaire à ce qui suit est insérée dans votre document :

```html
<input id="Submit1" type="submit" value="Submit" name="Submit1">
```

**Input (Text)**

![Capture d’écran de HTMLpageToolbarTextField](../../ide/reference/media/vxtextfield.gif "vxTextfield")

Insère un élément `input` tel que `type="text"` dans votre document. Pour changer le texte affiché par défaut, modifiez l’attribut `value`. Par défaut, `id="Text1"` est inséré pour le premier champ de texte, `id="Text2"` pour le deuxième, etc.

Quand vous faites glisser **Input (Text)** sur la surface en mode Design, une balise HTML similaire à ce qui suit est insérée dans votre document :

```html
<input id="Text1" TYPE="text" value="Text Field" name="Text1">
```

> [!IMPORTANT]
>Il est recommandé de valider toutes les entrées d’utilisateur. Pour plus d’informations, consultez [Validation des entrées d’utilisateur sur des sites de pages web ASP.NET (Razor)](/aspnet/web-pages/overview/ui-layouts-and-themes/validating-user-input-in-aspnet-web-pages-sites).

**Input (File)**

![Champ File de page HTML](../../ide/reference/media/vxfilefield.gif "vxFilefield")

Insère un élément `input` tel que `type="file"` dans votre document. Par défaut, `id="File1"` est inséré pour le premier champ de fichier, `id="File2"` pour le deuxième, etc.

Quand vous faites glisser **Input (File)** sur la surface en mode Design, une balise HTML similaire à ce qui suit est insérée dans votre document :

```html
<input id="File1" type="file" name="File1">
```

> [!IMPORTANT]
> Il est recommandé de valider toutes les entrées d’utilisateur. Pour plus d’informations, consultez [Validation des entrées d’utilisateur sur des sites de pages web ASP.NET (Razor)](/aspnet/web-pages/overview/ui-layouts-and-themes/validating-user-input-in-aspnet-web-pages-sites).

**Input (Password)**

![Champ Password de Visual Studio](../../ide/reference/media/vxpassword.gif "vxPassword")

Insère un élément `input` tel que `type="password"`. Par défaut, `id="Password1"` est inséré pour le premier champ de mot de passe, `id="Password2"` pour le deuxième, etc.

Quand vous faites glisser **Input (Password)** sur la surface en mode Design, une balise HTML similaire à ce qui suit est insérée dans votre document :

```html
<input id="Password1" type="password" name="Password1">
```

> [!IMPORTANT]
> Si votre application transmet des noms d’utilisateurs et des mots de passe, vous devez configurer votre site web afin qu’il utilise SSL (Secure Sockets Layer) pour chiffrer la transmission. Pour plus d’informations, consultez la rubrique relative à la sécurisation des connexions avec SSL dans le [Guide des opérations IIS](http://go.microsoft.com/fwlink/?linkid=47856). Il est, en outre, recommandé de valider toutes les entrées d’utilisateur. Pour plus d’informations, consultez [Validation des entrées d’utilisateur sur des sites de pages web ASP.NET (Razor)](/aspnet/web-pages/overview/ui-layouts-and-themes/validating-user-input-in-aspnet-web-pages-sites).

**Input (Check box)**

![Option Checkbox de boîte à outils de page web HTML](../../ide/reference/media/vxcheckbox.gif "vxCheckbox")

Insère un élément `input` tel que `type="checkbox"`. Pour changer le texte affiché, modifiez la propriété `name`. Par défaut, `id="Checkbox1"` est inséré pour la première case à cocher, `id="Checkbox2"` pour la deuxième, etc.

Quand vous faites glisser **Input (Check box)** sur la surface en mode Design, une balise HTML similaire à ce qui suit est insérée dans votre document :

```html
<input id="Checkbox1" type="checkbox" name="Checkbox1">
```

**Input (Radio)**

![Capture d’écran de VisualStudioHTMLpageRadioButton](../../ide/reference/media/vxradio.gif "vxRadio")

Insère un élément `input` tel que `type="radio"`. Pour changer le texte affiché, modifiez la propriété `name`. Par défaut, `id="Radio1"` est inséré pour la première case d’option, `id="Radio2"` pour la deuxième, etc.

Quand vous faites glisser **Input (Radio)** sur la surface en mode Design, une balise HTML similaire à ce qui suit est insérée dans votre document :

```html
<input id="Radio1" type="radio" name="Radio1">
```

**Input (Hidden)**

![Élément Hidden de page HTML](../../ide/reference/media/vxhidden.gif "vxhidden")

Insère un élément `input` tel que `type="hidden"`. Par défaut, `id="Hidden1"` est inséré pour le premier champ masqué, `id="Hidden2"` pour le deuxième, etc.

Quand vous faites glisser **Input (Hidden)** sur la surface en mode Design, une balise HTML similaire à ce qui suit est insérée dans votre document :

```html
<input id="Hidden1" type="hidden" name="Hidden1">
```

**Textarea**

![Zone de texte de barre d’outils de page HTML](../../ide/reference/media/vxtextarea.gif "vxTextarea")

Insère un élément `textarea`. Vous pouvez redimensionner la zone de texte ou utiliser les barres de défilement pour afficher le texte qui s’étend au-delà de la zone d’affichage. Pour changer le texte affiché par défaut, modifiez l’attribut `value`. Par défaut, `id="textarea1"` est inséré pour la première zone de texte, `id=" textarea 2"` pour la deuxième, etc.

Quand vous faites glisser **Textarea** sur la surface en mode Design, une balise HTML similaire à ce qui suit est insérée dans votre document :

```html
<textarea id=" textarea 1 name=" textarea 1" rows=2 cols=20></textarea>
```

> [!IMPORTANT]
> Il est recommandé de valider toutes les entrées d’utilisateur. Pour plus d’informations, consultez [Validation des entrées d’utilisateur sur des sites de pages web ASP.NET (Razor)](/aspnet/web-pages/overview/ui-layouts-and-themes/validating-user-input-in-aspnet-web-pages-sites).

**Table**

![Capture d’écran de HTMLpageToolbarTable](../../ide/reference/media/vxtable.gif "vxTable")

Insère un élément `table`.

Quand vous faites glisser **Table** sur la surface en mode Design, une balise HTML similaire à ce qui suit est insérée dans votre document :

```html
<table cellspacing="1" width="75%" border=1> <tr><td></td></tr></table>
```

**Image**

![Élément Image de page HTML](../../ide/reference/media/vximage.gif "vxImage")

Insère un élément `img`. Modifiez cet élément pour spécifier son texte `src` et `alt`.

Quand vous faites glisser **Image** sur la surface en mode Design, une balise HTML similaire à ce qui suit est insérée dans votre document :

```html
<img alt="" src="">
```

**Select**

![Liste déroulante de boîte à outils de page HTML](../../ide/reference/media/vxdropdown.gif "vxDropdown")

Insère un élément `select` de liste déroulante (sans attribut `size`). Par défaut, `id="select1"` est inséré pour la première zone de liste, `id="select2"` pour la deuxième, etc.

Quand vous faites glisser **Select** sur la surface en mode Design, une balise HTML similaire à ce qui suit est insérée dans votre document :

```html
<select id="select1" name="select1"><option selected></option></select>
```

Vous pouvez créer un élément `select` multiligne en augmentant la valeur de la propriété size.

**Horizontal Rule**

![Élément Horizontal Rule de page HTML](../../ide/reference/media/vxhorizontal.gif "vxHorizontal")

Insère un élément `hr`. Pour augmenter l’épaisseur de la ligne, modifiez l’attribut `size`.

Quand vous faites glisser **Horizontal Rule** sur la surface en mode Design, une balise HTML similaire à ce qui suit est insérée dans votre document :

```html
<hr width="100%" size=1>
```

**Div**

![Étiquette de page HTML](../../ide/reference/media/vxlabel.gif "vxLabel")

Insère un élément `div` qui inclut un attribut `ms_positioning="FlowLayout"`. À l’exception de la largeur et de la hauteur, cet élément est identique à un panneau de mise en page fluide. Pour mettre en forme le texte contenu dans l’élément `div`, ajoutez un attribut `class="stylename"` à la balise d’ouverture.

Quand vous faites glisser **Div** sur la surface en mode Design, une balise HTML similaire à ce qui suit est insérée dans votre document :

```html
<div ms_positioning="FlowLayout" style="width: 70px; position: relative; height: 15px">Label</div>
```

## <a name="see-also"></a>Voir aussi

- [Boîte à outils](../../ide/reference/toolbox.md)
