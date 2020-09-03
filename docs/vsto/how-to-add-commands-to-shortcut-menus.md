---
title: 'Comment : ajouter des commandes à des menus contextuels'
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office menus, creating
- Office development in Visual Studio, context menus
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 1ad27481799718d9d2b0872d7a43837fc822ca40
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85546196"
---
# <a name="how-to-add-commands-to-shortcut-menus"></a>Comment : ajouter des commandes à des menus contextuels
  Cette rubrique montre comment ajouter des commandes à un menu contextuel dans une application Office à l’aide d’un complément VSTO.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

### <a name="to-add-commands-to-shortcut-menus-in-office"></a>Pour ajouter des commandes à des menus contextuels dans Office

1. Ajoutez un élément **Ribbon XML** à un projet au niveau du document ou de complément VSTO. Pour plus d’informations, consultez [Comment : prendre en main la personnalisation du ruban](../vsto/how-to-get-started-customizing-the-ribbon.md). Dans

2. Dans l’**Explouateur de solutions**, sélectionnez **ThisAddin.cs** ou **ThisAddin.vb**.

3. Dans la barre de menus, choisissez **Afficher**le  >  **code**.

     Le fichier de classe **ThisAddin** s’ouvre dans l’éditeur de code.

4. Ajoutez le code suivant à la classe **ThisAddin** . Ce code substitue la méthode `CreateRibbonExtensibilityObject` et retourne la classe Ribbon XML à l'application Office.

     [!code-csharp[Trin_WordAddIn_Menus#1](../vsto/codesnippet/CSharp/trin_wordaddin_menus.cs/thisaddin.cs#1)]
     [!code-vb[Trin_WordAddIn_Menus#1](../vsto/codesnippet/VisualBasic/trin_wordaddin_menus.vb/thisaddin.vb#1)]

5. Dans l’ **Explorateur de solutions**, sélectionnez le fichier XML de ruban. Par défaut, le fichier XML du ruban est nommé *Ribbon1.xml*.

6. Dans la barre de menus, choisissez **Afficher**le  >  **code**.

     Le fichier XML de ruban s’ouvre dans l’éditeur de code.

7. Dans l’éditeur de code, ajoutez le code XML qui décrit le menu contextuel et le contrôle à ajouter au menu contextuel.

     L’exemple suivant ajoute un bouton, un menu et un contrôle de galerie au menu contextuel d’un document Word. L’ID du contrôle de ce menu contextuel est ContextMenuText. Pour obtenir la liste complète des ID de contrôle de raccourci Office 2010, consultez [fichiers d’aide office 2010 : identificateurs de contrôle d’interface utilisateur Office Fluent](https://www.microsoft.com/download/details.aspx?id=6627).

    ```xml
    <?xml version="1.0" encoding="UTF-8"?>
    <customUI xmlns="http://schemas.microsoft.com/office/2009/07/customui">
      <contextMenus>
        <contextMenu idMso="ContextMenuText">
          <button id="MyButton" label="My Button" insertBeforeMso="HyperlinkInsert" onAction="GetButtonID" />
          <menu id="MySubMenu" label="My Submenu" >
            <button id="MyButton2" label="Button on submenu" />
          </menu>
          <gallery id="galleryOne" label="My Gallery">
            <item id="item1" imageMso="HappyFace" />
            <item id="item2" imageMso="HappyFace" />
            <item id="item3" imageMso="HappyFace" />
            <item id="item4" imageMso="HappyFace" />
          </gallery>
        </contextMenu>
      </contextMenus>
    </customUI>
    ```

8. Dans l’ **Explorateur de solutions**, choisissez **MyRibbon.cs** ou **MyRibbon.vb**.

9. Ajoutez une méthode de rappel à la `Ribbon1` classe pour chaque contrôle que vous souhaitez gérer.

     La méthode de rappel suivante gère le bouton **Mon bouton** . Ce code ajoute une chaîne au document actif à l’emplacement actuel du curseur.

     [!code-vb[Trin_WordAddIn_Menus#2](../vsto/codesnippet/VisualBasic/trin_wordaddin_menus.vb/ribbon1.vb#2)]
     [!code-csharp[Trin_WordAddIn_Menus#2](../vsto/codesnippet/CSharp/trin_wordaddin_menus.cs/ribbon1.cs#2)]

## <a name="see-also"></a>Voir aussi
- [Personnalisation de l’interface utilisateur Office](../vsto/office-ui-customization.md)
- [Procédure pas à pas : créer des menus contextuels pour les signets](../vsto/walkthrough-creating-shortcut-menus-for-bookmarks.md)
- [Paramètres facultatifs dans les solutions Office](../vsto/optional-parameters-in-office-solutions.md)
- [Personnaliser les menus contextuels dans Office 2010](/previous-versions/office/developer/office-2010/ee691832(v=office.14))
