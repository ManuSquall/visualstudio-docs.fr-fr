---
title: Programmer des personnalisations au niveau du document
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- Sheet3
- thisWorkbook
- thisDocument
- Sheet1
- Sheet2
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ThisDocument class
- Sheet3 class
- ThisWorkbook class
- writing code for Office solutions
- programming [Office development in Visual Studio], document-level customizations
- Sheet1 class
- Office applications [Office development in Visual Studio], document-level customizations
- Sheet2 class
- document-level customizations [Office development in Visual Studio], programming
- application development [Office development in Visual Studio], document-level customizations
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 0815ccf781782a0d638fcf941a6e48edcf8ccd1f
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/21/2019
ms.locfileid: "56624683"
---
# <a name="program-document-level-customizations"></a>Programmer des personnalisations au niveau du document
  Quand vous étendez Microsoft Office Word ou Microsoft Office Excel à l’aide d’une personnalisation au niveau du document, vous pouvez effectuer les tâches suivantes :

- Automatiser l’application à l’aide de son modèle objet.

- Ajouter des contrôles à la surface du document.

- Appeler du code Visual Basic pour Applications (VBA) dans le document à partir de l’assembly de personnalisation.

- Appeler du code dans l’assembly de personnalisation à partir de VBA.

- Gérer certains aspects du document alors qu’il est sur un serveur sur lequel Microsoft Office n’est pas installé.

- Personnaliser l’interface utilisateur (IU) de l’application.

  [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

  Certains aspects de l’écriture de code dans des projets au niveau du document diffèrent des autres types de projets dans Visual Studio. Une grande partie de ces différences ont pour origine la façon dont les modèles objet Office sont exposés au code managé. Pour plus d’informations, consultez [écrire du code dans les solutions Office](../vsto/writing-code-in-office-solutions.md).

  Pour obtenir des informations générales sur les personnalisations au niveau du document et d’autres types de solutions que vous pouvez créer à l’aide des outils de développement Office dans Visual Studio, consultez [présentation du développement de solutions Office &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md).

## <a name="use-the-generated-classes-in-document-level-projects"></a>Utilisez les classes générées dans les projets au niveau du document
 Quand vous créez un projet au niveau du document, Visual Studio génère automatiquement une classe dans le projet que vous pouvez utiliser pour commencer à écrire votre code. Visual Studio génère des classes différentes pour Word et Excel :

- Dans les projets au niveau du document pour Word, la classe est appelée `ThisDocument` par défaut.

- Les projets au niveau du document pour Excel comportent plusieurs classes générées : une pour le classeur lui-même et une pour chaque feuille de calcul. Par défaut, ces classes portent les noms suivants :

  -   `ThisWorkbook`

  -   `Sheet1`

  -   `Sheet2`

  -   `Sheet3`

  La classe générée inclut des gestionnaires d’événements appelés quand le document est ouvert ou fermé. Pour exécuter du code à l’ouverture du document, ajoutez-le au gestionnaire d’événements `Startup` . Pour exécuter du code avant la fermeture du document, ajoutez-le au gestionnaire d’événements `Shutdown` . Pour plus d’informations, consultez [événements dans les projets Office](../vsto/events-in-office-projects.md).

### <a name="understand-the-design-of-the-generated-classes"></a>Comprendre la conception des classes générées
 Dans les projets qui ciblent le [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] ou le [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)], les types d’élément hôte dans le [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] sont des interfaces, donc les classes générées ne peuvent pas en dériver leur implémentation. Au lieu de cela, les classes générées dérivent la plupart de leurs membres des classes de base suivantes :

- `ThisDocument`: dérive de <xref:Microsoft.Office.Tools.Word.DocumentBase>.

- `ThisWorkbook`: dérive de <xref:Microsoft.Office.Tools.Excel.WorkbookBase>.

- `Sheet` *n*: dérive de <xref:Microsoft.Office.Tools.Excel.WorksheetBase>.

  Ces classes de base redirigent tous les appels à leurs membres vers les implémentations internes des interfaces de l’élément hôte correspondant dans le [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]. Par exemple, si vous appelez la méthode <xref:Microsoft.Office.Tools.Word.DocumentBase.Protect%2A> de la classe `ThisDocument` , la classe <xref:Microsoft.Office.Tools.Word.DocumentBase> redirige cet appel vers l’implémentation interne de l’interface <xref:Microsoft.Office.Tools.Word.Document> dans le [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)].

## <a name="access-the-object-model-of-the-host-application"></a>Accéder au modèle objet de l’application hôte
 Pour accéder au modèle objet de l’application hôte, utilisez les membres de la classe générée dans votre projet. Chacune de ces classes correspond à un objet dans le modèle objet de Microsoft Excel ou Word, et elles contiennent la plupart des mêmes propriétés, méthodes et événements. Par exemple, la classe `ThisDocument` dans un projet au niveau du document pour Word fournit plus ou moins les mêmes membres que l’objet <xref:Microsoft.Office.Interop.Word.Document> dans le modèle objet Word.

 L’exemple de code suivant montre comment utiliser le modèle objet Word pour enregistrer le document qui fait partie d’une personnalisation au niveau du document pour Word. Cet exemple est destiné à être exécuté à partir de la classe `ThisDocument` .

```vb
Me.Save()
```

```csharp
this.Save();
```

 Pour effectuer la même opération depuis l'extérieur de la classe `ThisDocument` , utilisez l'objet `Globals` pour accéder à la classe `ThisDocument` . Par exemple, vous pouvez ajouter ce code à un fichier de code du volet Actions si vous voulez inclure un bouton **Enregistrer** dans l’interface utilisateur de ce volet Actions.

```vb
Globals.ThisDocument.Save()
```

```csharp
Globals.ThisDocument.Save();
```

 Puisque la classe `ThisDocument` obtient la plupart de ses membres à partir de l’élément hôte <xref:Microsoft.Office.Tools.Word.Document> , la méthode `Save` appelée dans ce code correspond vraiment à la méthode <xref:Microsoft.Office.Tools.Word.Document.Save%2A> de l’élément hôte <xref:Microsoft.Office.Tools.Word.Document> . Cette méthode correspond à la méthode <xref:Microsoft.Office.Interop.Word._Document.Save%2A> de l’objet <xref:Microsoft.Office.Interop.Word.Document> dans le modèle objet Word.

 Pour plus d’informations sur les modèles d’objet de Word et Excel, consultez [vue d’ensemble du modèle d’objet Word](../vsto/word-object-model-overview.md) et [vue d’ensemble du modèle d’objet Excel](../vsto/excel-object-model-overview.md).

 Pour plus d’informations sur la `Globals` d’objets, consultez [d’accès Global aux objets dans les projets Office](../vsto/global-access-to-objects-in-office-projects.md).

## <a name="add-controls-to-documents"></a>Ajouter des contrôles aux documents
 Pour personnaliser l’interface utilisateur du document, vous pouvez ajouter des contrôles Windows Forms ou des *contrôles hôtes* à la surface du document. En combinant plusieurs jeux de contrôles et en écrivant du code, vous pouvez lier les contrôles à des données, recueillir des informations auprès de l’utilisateur et répondre aux actions de l’utilisateur.

 Les contrôles hôtes sont des classes qui étendent certains objets du modèle objet Word et Excel. Par exemple, le contrôle hôte <xref:Microsoft.Office.Tools.Excel.ListObject> fournit toutes les fonctionnalités de <xref:Microsoft.Office.Interop.Excel.ListObject> dans Excel. En revanche, le contrôle hôte <xref:Microsoft.Office.Tools.Excel.ListObject> possède également des événements supplémentaires et des fonctionnalités de liaison de données.

 Pour plus d’informations, consultez [éléments hôtes et héberger de vue d’ensemble des contrôles](../vsto/host-items-and-host-controls-overview.md) et [Windows forms des contrôles sur la vue d’ensemble des documents Office](../vsto/windows-forms-controls-on-office-documents-overview.md).

## <a name="combine-vba-and-document-level-customizations"></a>Combiner VBA et personnalisations au niveau du document
 Vous pouvez utiliser du code VBA dans un document qui fait partie d’une personnalisation au niveau du document. Vous pouvez appeler du code VBA dans le document à partir de l’assembly de personnalisation ou configurer votre projet pour permettre au code VBA du document d’appeler du code dans l’assembly de personnalisation.

 Pour plus d’informations, consultez [combiner de VBA et de personnalisations au niveau du document](../vsto/combining-vba-and-document-level-customizations.md).

## <a name="manage-documents-on-a-server"></a>Gérer des documents sur un serveur
 Vous pouvez gérer différents aspects des personnalisations au niveau du document sur un serveur sur lequel Microsoft Office Word ou Microsoft Office Excel ne sont pas installés. Par exemple, vous pouvez accéder aux données du cache du document et les modifier. Vous pouvez également gérer l’assembly de personnalisation associé au document. Par exemple, vous pouvez, par programmation, supprimer l’assembly du document pour qu’il n’exécute plus votre code. Vous pouvez aussi, par programmation, attacher un assembly à un document.

 Pour plus d’informations, consultez [gérer des documents sur un serveur à l’aide de la classe ServerDocument](../vsto/managing-documents-on-a-server-by-using-the-serverdocument-class.md).

## <a name="customize-the-user-interface-of-microsoft-office-applications"></a>Personnaliser l’interface utilisateur des applications Microsoft Office
 Vous pouvez personnaliser l’interface utilisateur de Word et Excel comme suit à l’aide d’une personnalisation au niveau du document :

- Ajouter des contrôles hôtes ou des contrôles Windows Forms à la surface du document.

   Pour plus d’informations, consultez [automatisation de Word à l’aide d’objets étendus](../vsto/automating-word-by-using-extended-objects.md), [automatisation d’Excel à l’aide d’objets étendus](../vsto/automating-excel-by-using-extended-objects.md), et [des contrôles de Windows Forms dans les documents Office](../vsto/windows-forms-controls-on-office-documents-overview.md).

- Ajouter un volet Actions au document.

   Pour plus d’informations, consultez [vue d’ensemble du volet Actions](../vsto/actions-pane-overview.md).

- Ajouter des onglets personnalisés au ruban.

   Pour plus d’informations, consultez [vue d’ensemble du ruban](../vsto/ribbon-overview.md).

- Ajouter des groupes personnalisés à un onglet prédéfini du ruban.

   Pour plus d'informations, voir [Procédure : Personnaliser un onglet intégré](../vsto/how-to-customize-a-built-in-tab.md).

  Pour plus d’informations sur la personnalisation de l’interface utilisateur des applications Microsoft Office, consultez [personnalisation de l’interface utilisateur Office](../vsto/office-ui-customization.md).

## <a name="get-extended-objects-from-native-office-objects-in-document-level-customizations"></a>Obtenir des objets étendus à partir d’objets Office natifs dans les personnalisations au niveau du document
 De nombreux gestionnaires d’événements Office reçoivent un objet Office natif qui représente le classeur, la feuille de calcul ou le document qui a déclenché l’événement. Dans certains cas, vous pouvez avoir besoin d’exécuter du code uniquement si le classeur ou le document de votre personnalisation au niveau du document a déclenché l’événement. Par exemple, dans une personnalisation au niveau du document pour Excel, vous pouvez avoir besoin d’exécuter du code quand l’utilisateur active l’une des feuilles de calcul d’un classeur personnalisé, mais pas quand il active une feuille de calcul incluse dans un autre classeur ouvert en même temps.

 Quand vous avez un objet Office natif, vous pouvez tester si cet objet a été étendu dans un *élément hôte* ou *contrôle hôte* dans une personnalisation au niveau du document. Les éléments hôtes et les contrôles hôtes sont des types fournis par [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] qui ajoutent des fonctionnalités aux objets qui existent en mode natif dans les modèles objet Word ou Excel (appelés *objets Office natifs*). Collectivement, les éléments hôtes et les contrôles hôtes sont également appelés *objets étendus*. Pour plus d’informations sur les éléments hôtes et contrôles hôtes, consultez [éléments hôtes et héberger de vue d’ensemble des contrôles](../vsto/host-items-and-host-controls-overview.md).

## <a name="understand-the-getvstoobject-and-hasvstoobject-methods"></a>Comprendre les méthodes GetVstoObject et HasVstoObject
 Pour tester un objet Office natif, utilisez les méthodes `HasVstoObject` et `GetVstoObject` dans votre projet :

- Utilisez la méthode `HasVstoObject` pour déterminer si l’objet Office natif possède un objet étendu dans votre personnalisation. Cette méthode retourne **true** si l’objet Office natif possède un objet étendu et **false** dans le cas contraire.

- Utilisez la méthode `GetVstoObject` pour obtenir l’objet étendu d’un objet Office natif. Cette méthode retourne un objet <xref:Microsoft.Office.Tools.Excel.ListObject>, <xref:Microsoft.Office.Tools.Excel.Workbook>, <xref:Microsoft.Office.Tools.Excel.Worksheet>ou <xref:Microsoft.Office.Tools.Word.Document> si l’objet Office natif spécifié en possède un. Sinon, `GetVstoObject` retourne **null**. Par exemple, la méthode `GetVstoObject` retourne un objet <xref:Microsoft.Office.Tools.Word.Document> si l’objet <xref:Microsoft.Office.Interop.Word.Document> spécifié est l’objet sous-jacent du document dans votre projet de document Word.

  Dans les projets au niveau du document, vous ne pouvez pas utiliser le `GetVstoObject` pour créer une nouvelle méthode <xref:Microsoft.Office.Tools.Excel.Workbook>, <xref:Microsoft.Office.Tools.Excel.Worksheet>, ou <xref:Microsoft.Office.Tools.Word.Document> élément hôte lors de l’exécution. Vous pouvez utiliser cette méthode uniquement pour accéder aux éléments hôtes existants, générés dans votre projet au moment du design. Si vous souhaitez créer des éléments hôtes lors de l’exécution, vous devez développer un projet de complément VSTO. Pour plus d’informations, consultez [limitations de programmation des éléments hôtes et contrôles hôtes](../vsto/programmatic-limitations-of-host-items-and-host-controls.md) et [documents Word d’étendre et classeurs Excel dans des Compléments VSTO lors de l’exécution](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).

## <a name="use-the-getvstoobject-and-hasvstoobject-methods"></a>Utilisez les méthodes GetVstoObject et HasVstoObject
 Pour appeler le `HasVstoObject` et `GetVstoObject` (méthode), utilisez le `Globals.Factory.GetVstoObject` ou `Globals.Factory.HasVstoObject` (méthode) et passez l’objet Word ou Excel natif (comme un <xref:Microsoft.Office.Interop.Word.Document> ou <xref:Microsoft.Office.Interop.Excel.Worksheet>) que vous souhaitez tester.

## <a name="see-also"></a>Voir aussi
- [Contrôles sur des documents Office](../vsto/controls-on-office-documents.md)
- [Combiner VBA et personnalisations au niveau du document](../vsto/combining-vba-and-document-level-customizations.md)
- [Gérer des documents sur un serveur à l’aide de la classe ServerDocument](../vsto/managing-documents-on-a-server-by-using-the-serverdocument-class.md)
- [Écrire du code dans les solutions Office](../vsto/writing-code-in-office-solutions.md)
