---
title: 'Comment : protéger des parties de documents à l’aide de contrôles de contenu'
description: Découvrez comment vous pouvez utiliser Visual Studio pour protéger des parties d’un document Microsoft Word à l’aide de contrôles de contenu.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- restricted permissions [Office development in Visual Studio]
- partial document protection [Office development in Visual Studio]
- content controls [Office development in Visual Studio], protecting documents
- Word [Office development in Visual Studio], partial document protection
- document protection [Office development in Visual Studio]
- Word [Office development in Visual Studio], restricted permissions
- GroupContentControl
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: cc333871d4f371530db84a0c4f07ab891db2a937
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/21/2021
ms.locfileid: "107825470"
---
# <a name="how-to-protect-parts-of-documents-by-using-content-controls"></a>Comment : protéger des parties de documents à l’aide de contrôles de contenu
  Quand vous protégez une partie d'un document, vous empêchez les utilisateurs de modifier ou de supprimer le contenu dans cette partie du document. Il existe plusieurs manières de protéger des parties d'un document Microsoft Office Word à l'aide de contrôles de contenu :

- Vous pouvez protéger un contrôle de contenu.

- Vous pouvez protéger une partie d'un document qui ne se trouve pas dans un contrôle de contenu.

  [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="protect-a-content-control"></a><a name="EditDeleteControl"></a> Protéger un contrôle de contenu
 Vous pouvez empêcher les utilisateurs de modifier ou supprimer un contrôle de contenu en définissant les propriétés du contrôle dans un projet au niveau du document, au moment du design ou au moment de l'exécution.

 Vous pouvez également protéger les contrôles de contenu que vous ajoutez à un document au moment de l'exécution à l'aide d'un projet de complément VSTO. Pour plus d’informations, consultez [Comment : ajouter des contrôles de contenu à des documents Word](../vsto/how-to-add-content-controls-to-word-documents.md).

### <a name="to-protect-a-content-control-at-design-time"></a>Pour protéger un contrôle de contenu au moment du design

1. Dans le document hébergé dans le concepteur [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], sélectionnez le contrôle de contenu à protéger.

2. Dans la fenêtre **Propriétés** , définissez l’une des propriétés suivantes, ou les deux :

    - Pour empêcher les utilisateurs de modifier le contrôle, affectez la valeur **true** à **LockContents** .

    - Pour empêcher les utilisateurs de supprimer le contrôle, affectez à **LockContentControl** la **valeur true**.

3. Cliquez sur **OK**.

### <a name="to-protect-a-content-control-at-run-time"></a>Pour protéger un contrôle de contenu au moment de l'exécution

1. Affectez la valeur `LockContents` **true** à la propriété du contrôle de contenu pour empêcher les utilisateurs de modifier le contrôle, puis affectez la valeur `LockContentControl` **true** à la propriété pour empêcher les utilisateurs de supprimer le contrôle.

     L'exemple de code suivant illustre l'utilisation des propriétés <xref:Microsoft.Office.Tools.Word.RichTextContentControl.LockContents%2A> et <xref:Microsoft.Office.Tools.Word.RichTextContentControl.LockContentControl%2A> de deux objets <xref:Microsoft.Office.Tools.Word.RichTextContentControl> distincts dans un projet au niveau du document. Pour exécuter ce code, ajoutez-le à la classe `ThisDocument` dans votre projet, puis appelez la méthode `AddProtectedContentControls` à partir du gestionnaire d'événements `ThisDocument_Startup` .

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_ContentControlHowToProtect/ThisDocument.cs" id="Snippet2":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_ContentControlHowToProtect/ThisDocument.vb" id="Snippet2":::

     L’exemple de code suivant illustre l’utilisation des propriétés <xref:Microsoft.Office.Tools.Word.RichTextContentControl.LockContents%2A> et <xref:Microsoft.Office.Tools.Word.RichTextContentControl.LockContentControl%2A> de deux objets <xref:Microsoft.Office.Tools.Word.RichTextContentControl> distincts dans un projet de complément VSTO. Pour exécuter ce code, ajoutez-le à la classe `ThisAddIn` dans votre projet, puis appelez la méthode `AddProtectedContentControls` à partir du gestionnaire d'événements `ThisAddIn_Startup` .

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_wordaddindynamiccontrols/ThisAddIn.vb" id="Snippet14":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControls/ThisAddIn.cs" id="Snippet14":::

## <a name="protect-a-part-of-a-document-that-is-not-in-a-content-control"></a>Protéger une partie d’un document qui ne se trouve pas dans un contrôle de contenu
 Vous pouvez empêcher les utilisateurs de modifier une zone d'un document en la plaçant dans <xref:Microsoft.Office.Tools.Word.GroupContentControl>. Cela s'avère utile dans les scénarios suivant :

- Vous souhaitez protéger une zone qui ne contient pas de contrôles de contenu.

- Vous souhaitez protéger une zone qui contient déjà des contrôles de contenu, mais le texte ou les autres éléments que vous souhaitez protéger ne se trouvent pas dans les contrôles de contenu.

> [!NOTE]
> Si vous créez un <xref:Microsoft.Office.Tools.Word.GroupContentControl> qui contient des contrôles de contenu incorporés, ces contrôles ne sont pas protégés automatiquement. Pour empêcher les utilisateurs de modifier un contrôle de contenu incorporé, utilisez la propriété **LockContents** du contrôle.

### <a name="to-protect-an-area-of-a-document-at-design-time"></a>Pour protéger une zone d'un document au moment du design

1. Dans le document hébergé dans le concepteur [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], sélectionnez la zone à protéger.

2. Dans le ruban, cliquez sur l'onglet **Développeur** .

    > [!NOTE]
    > Si l'onglet **Développeur** n'est pas visible, vous devez tout d'abord l'afficher. Pour plus d’informations, consultez [Comment : afficher l’onglet Développeur sur le ruban](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md).

3. Dans le groupe **contrôles** , cliquez sur le bouton déroulant de **Groupe** , puis sur **groupe**.

     Un <xref:Microsoft.Office.Tools.Word.GroupContentControl> qui contient la zone protégée est généré automatiquement dans la classe `ThisDocument` de votre projet. Une bordure qui représente le contrôle de groupe est visible au moment du design. Toutefois, aucune bordure n'est visible au moment de l'exécution.

### <a name="to-protect-an-area-of-a-document-at-run-time"></a>Pour protéger une zone d'un document au moment de l'exécution

1. Sélectionnez par programmation la zone à protéger, puis appelez la méthode <xref:Microsoft.Office.Tools.Word.ControlCollection.AddGroupContentControl%2A> pour créer <xref:Microsoft.Office.Tools.Word.GroupContentControl>.

     L'exemple de code suivant pour un projet au niveau du document ajoute du texte au premier paragraphe du document, sélectionne le premier paragraphe, puis instancie <xref:Microsoft.Office.Tools.Word.GroupContentControl>. Pour exécuter ce code, ajoutez-le à la classe `ThisDocument` dans votre projet, puis appelez la méthode `ProtectFirstParagraph` à partir du gestionnaire d'événements `ThisDocument_Startup` .

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_ContentControlHowToProtect/ThisDocument.cs" id="Snippet1":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_ContentControlHowToProtect/ThisDocument.vb" id="Snippet1":::

     L'exemple de code suivant pour un projet de complément VSTO ajoute du texte au premier paragraphe du document actif, sélectionne le premier paragraphe, puis instancie <xref:Microsoft.Office.Tools.Word.GroupContentControl>. Pour exécuter ce code, ajoutez-le à la classe `ThisAddIn` dans votre projet, puis appelez la méthode `ProtectFirstParagraph` à partir du gestionnaire d'événements `ThisAddIn_Startup` .

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_wordaddindynamiccontrols/ThisAddIn.vb" id="Snippet15":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControls/ThisAddIn.cs" id="Snippet15":::

## <a name="see-also"></a>Voir aussi
- [Automatiser Word à l’aide d’objets étendus](../vsto/automating-word-by-using-extended-objects.md)
- [Contrôles de contenu](../vsto/content-controls.md)
- [Comment : ajouter des contrôles de contenu à des documents Word](../vsto/how-to-add-content-controls-to-word-documents.md)
- [Vue d’ensemble des éléments hôtes et des contrôles hôtes](../vsto/host-items-and-host-controls-overview.md)
- [Limitations de programmation des éléments hôtes et des contrôles hôtes](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
- [Ajouter des contrôles aux documents Office au moment de l’exécution](../vsto/adding-controls-to-office-documents-at-run-time.md)
