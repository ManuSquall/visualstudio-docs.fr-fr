---
title: 'Procédure : Protéger des parties de documents à l’aide de contrôles de contenu'
ms.date: 02/02/2017
ms.topic: conceptual
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 87dda9c975f35ac8b48e60acd3e692f9b3a070d4
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2019
ms.locfileid: "60103512"
---
# <a name="how-to-protect-parts-of-documents-by-using-content-controls"></a>Procédure : Protéger des parties de documents à l’aide de contrôles de contenu
  Quand vous protégez une partie d'un document, vous empêchez les utilisateurs de modifier ou de supprimer le contenu dans cette partie du document. Il existe plusieurs manières de protéger des parties d'un document Microsoft Office Word à l'aide de contrôles de contenu :

- Vous pouvez protéger un contrôle de contenu.

- Vous pouvez protéger une partie d'un document qui ne se trouve pas dans un contrôle de contenu.

  [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="EditDeleteControl"></a> Protéger un contrôle de contenu
 Vous pouvez empêcher les utilisateurs de modifier ou supprimer un contrôle de contenu en définissant les propriétés du contrôle dans un projet au niveau du document au moment du design ou lors de l’exécution.

 Vous pouvez également protéger les contrôles de contenu que vous ajoutez à un document au moment de l'exécution à l'aide d'un projet de complément VSTO. Pour plus d'informations, voir [Procédure : Ajouter des contrôles de contenu à des documents Word](../vsto/how-to-add-content-controls-to-word-documents.md).

### <a name="to-protect-a-content-control-at-design-time"></a>Pour protéger un contrôle de contenu au moment du design

1. Dans le document hébergé dans le concepteur [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], sélectionnez le contrôle de contenu à protéger.

2. Dans le **propriétés** fenêtre, définissez une ou les deux des propriétés suivantes :

    - Pour empêcher les utilisateurs de modifier le contrôle, affectez **LockContents** à **True**.

    - Pour empêcher les utilisateurs de supprimer le contrôle, affectez **LockContentControl** à **True**.

3. Cliquez sur **OK**.

### <a name="to-protect-a-content-control-at-runtime"></a>Pour protéger un contrôle de contenu lors de l’exécution

1. Définir le `LockContents` propriété du contrôle de contenu à **true** pour empêcher les utilisateurs de modifier le contrôle et définir le `LockContentControl` propriété **true** pour empêcher les utilisateurs de supprimer le contrôle.

     L'exemple de code suivant illustre l'utilisation des propriétés <xref:Microsoft.Office.Tools.Word.RichTextContentControl.LockContents%2A> et <xref:Microsoft.Office.Tools.Word.RichTextContentControl.LockContentControl%2A> de deux objets <xref:Microsoft.Office.Tools.Word.RichTextContentControl> distincts dans un projet au niveau du document. Pour exécuter ce code, ajoutez-le à la classe `ThisDocument` dans votre projet, puis appelez la méthode `AddProtectedContentControls` à partir du gestionnaire d'événements `ThisDocument_Startup` .

     [!code-csharp[Trin_ContentControlHowToProtect#2](../vsto/codesnippet/CSharp/Trin_ContentControlHowToProtect/ThisDocument.cs#2)]
     [!code-vb[Trin_ContentControlHowToProtect#2](../vsto/codesnippet/VisualBasic/Trin_ContentControlHowToProtect/ThisDocument.vb#2)]

     L’exemple de code suivant illustre l’utilisation des propriétés <xref:Microsoft.Office.Tools.Word.RichTextContentControl.LockContents%2A> et <xref:Microsoft.Office.Tools.Word.RichTextContentControl.LockContentControl%2A> de deux objets <xref:Microsoft.Office.Tools.Word.RichTextContentControl> distincts dans un projet de complément VSTO. Pour exécuter ce code, ajoutez-le à la classe `ThisAddIn` dans votre projet, puis appelez la méthode `AddProtectedContentControls` à partir du gestionnaire d'événements `ThisAddIn_Startup` .

     [!code-vb[Trin_WordAddInDynamicControls#14](../vsto/codesnippet/VisualBasic/trin_wordaddindynamiccontrols/ThisAddIn.vb#14)]
     [!code-csharp[Trin_WordAddInDynamicControls#14](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControls/ThisAddIn.cs#14)]

## <a name="protect-a-part-of-a-document-that-is-not-in-a-content-control"></a>Protéger une partie d’un document qui n’est pas dans un contrôle de contenu
 Vous pouvez empêcher les utilisateurs de modifier une zone d'un document en la plaçant dans <xref:Microsoft.Office.Tools.Word.GroupContentControl>. Cela s'avère utile dans les scénarios suivant :

- Vous souhaitez protéger une zone qui ne contient pas de contrôles de contenu.

- Vous souhaitez protéger une zone qui contient déjà des contrôles de contenu, mais le texte ou les autres éléments que vous souhaitez protéger ne se trouvent pas dans les contrôles de contenu.

> [!NOTE]
>  Si vous créez un <xref:Microsoft.Office.Tools.Word.GroupContentControl> qui contient des contrôles de contenu incorporés, ces contrôles ne sont pas protégés automatiquement. Pour empêcher les utilisateurs de modifier un contrôle de contenu incorporé, utilisez la **LockContents** propriété du contrôle.

### <a name="to-protect-an-area-of-a-document-at-design-time"></a>Pour protéger une zone d'un document au moment du design

1. Dans le document hébergé dans le concepteur [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], sélectionnez la zone à protéger.

2. Dans le ruban, cliquez sur l'onglet **Développeur** .

    > [!NOTE]
    >  Si l'onglet **Développeur** n'est pas visible, vous devez tout d'abord l'afficher. Pour plus d'informations, voir [Procédure : Afficher l’onglet Développeur sur le ruban](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md).

3. Dans le **contrôles** de groupe, cliquez sur le **groupe** bouton de liste déroulante, puis cliquez sur **groupe**.

     Un <xref:Microsoft.Office.Tools.Word.GroupContentControl> qui contient la zone protégée est généré automatiquement dans la classe `ThisDocument` de votre projet. Une bordure qui représente le contrôle de groupe est visible au moment du design, mais il n’y a aucune bordure visible lors de l’exécution.

### <a name="to-protect-an-area-of-a-document-at-runtime"></a>Pour protéger une zone d’un document lors de l’exécution

1. Sélectionnez par programmation la zone à protéger, puis appelez la méthode <xref:Microsoft.Office.Tools.Word.ControlCollection.AddGroupContentControl%2A> pour créer <xref:Microsoft.Office.Tools.Word.GroupContentControl>.

     L'exemple de code suivant pour un projet au niveau du document ajoute du texte au premier paragraphe du document, sélectionne le premier paragraphe, puis instancie <xref:Microsoft.Office.Tools.Word.GroupContentControl>. Pour exécuter ce code, ajoutez-le à la classe `ThisDocument` dans votre projet, puis appelez la méthode `ProtectFirstParagraph` à partir du gestionnaire d'événements `ThisDocument_Startup` .

     [!code-csharp[Trin_ContentControlHowToProtect#1](../vsto/codesnippet/CSharp/Trin_ContentControlHowToProtect/ThisDocument.cs#1)]
     [!code-vb[Trin_ContentControlHowToProtect#1](../vsto/codesnippet/VisualBasic/Trin_ContentControlHowToProtect/ThisDocument.vb#1)]

     L'exemple de code suivant pour un projet de complément VSTO ajoute du texte au premier paragraphe du document actif, sélectionne le premier paragraphe, puis instancie <xref:Microsoft.Office.Tools.Word.GroupContentControl>. Pour exécuter ce code, ajoutez-le à la classe `ThisAddIn` dans votre projet, puis appelez la méthode `ProtectFirstParagraph` à partir du gestionnaire d'événements `ThisAddIn_Startup` .

     [!code-vb[Trin_WordAddInDynamicControls#15](../vsto/codesnippet/VisualBasic/trin_wordaddindynamiccontrols/ThisAddIn.vb#15)]
     [!code-csharp[Trin_WordAddInDynamicControls#15](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControls/ThisAddIn.cs#15)]

## <a name="see-also"></a>Voir aussi
- [Automatiser Word à l’aide d’objets étendus](../vsto/automating-word-by-using-extended-objects.md)
- [Contrôles de contenu](../vsto/content-controls.md)
- [Guide pratique pour Ajouter des contrôles de contenu à des documents Word](../vsto/how-to-add-content-controls-to-word-documents.md)
- [Éléments hôtes et la vue d’ensemble des contrôles hôtes](../vsto/host-items-and-host-controls-overview.md)
- [Limitations de programmation des éléments hôtes et contrôles hôtes](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
- [Ajouter des contrôles aux documents Office au moment de l’exécution](../vsto/adding-controls-to-office-documents-at-run-time.md)
