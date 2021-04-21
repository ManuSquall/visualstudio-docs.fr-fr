---
title: Événements dans les projets Office
description: Découvrez comment chaque modèle de projet Office génère plusieurs gestionnaires d’événements et comment ces gestionnaires d’événements sont légèrement différents de ceux des gestionnaires d’événements pour les compléments VSTO.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Sheet1_Startup
- ThisDocument_Shutdown
- ThisDocument_Startup
- application-level add-ins [Office development in Visual Studio], events
- event handlers [Office development in Visual Studio]
- ThisWorkbook_Startup
- Sheet2_Startup
- ThisWorkbook_Shutdown
- document-level customizations [Office development in Visual Studio], events
- Sheet2_Shutdown
- Startup event
- Sheet3_Shutdown
- add-ins [Office development in Visual Studio], events
- Shutdown event
- ThisAddIn_Startup
- Sheet3_Startup
- Startup method [Office development in Visual Studio]
- Shutdown method [Office development in Visual Studio]
- Sheet1_Shutdown
- events [Office development in Visual Studio]
- ThisAddIn_Shutdown
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: be1625be3d8c3fce409562be948c83a34d40d7b1
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/21/2021
ms.locfileid: "107825678"
---
# <a name="events-in-office-projects"></a>Événements dans les projets Office
  Chaque modèle de projet Office génère automatiquement plusieurs gestionnaires d'événements. Les gestionnaires d’événements pour les personnalisations au niveau du document sont légèrement différents de ceux pour les compléments VSTO.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

## <a name="document-level-projects"></a>Projets au niveau du document
 Visual Studio fournit du code behind généré pour les documents ou feuilles de calcul nouveaux ou existants dans les personnalisations au niveau du document. Ce code déclenche deux événements différents : **Startup** et **Shutdown**.

### <a name="startup-event"></a>Startup (événement)
 L'événement **Startup** est déclenché pour chacun des éléments hôtes (document, classeur ou feuille de calcul) après l'exécution du document et de tout le code d'initialisation dans l'assembly. Il s'agit de la dernière opération à exécuter dans le constructeur de la classe dans laquelle votre code est exécuté. Pour plus d’informations sur les éléments hôtes, consultez [vue d’ensemble des éléments hôtes et des contrôles hôtes](../vsto/host-items-and-host-controls-overview.md).

 Quand vous créez un projet au niveau du document, Visual Studio crée des gestionnaires d'événements pour l'événement **Startup** dans les fichiers de code générés :

- Pour les projets Microsoft Office Word, le gestionnaire d'événements s'appelle `ThisDocument_Startup`.

- Pour les projets Microsoft Office Excel, les gestionnaires d'événements portent les noms suivants :

  - `Sheet1_Startup`

  - `Sheet2_Startup`

  - `Sheet3_Startup`

  - `ThisWorkbook_Startup`

### <a name="shutdown-event"></a>Shutdown (événement)
 L'événement **Shutdown** est déclenché pour chacun des éléments hôtes (document ou feuille de calcul) quand le domaine d'application dans lequel votre code est chargé est sur le point d'être déchargé. Il s'agit de la dernière opération à appeler dans la classe pendant le déchargement.

 Quand vous créez un projet au niveau du document, Visual Studio crée des gestionnaires d'événements pour l'événement **Shutdown** dans les fichiers de code générés :

- Pour les projets Microsoft Office Word, le gestionnaire d'événements s'appelle `ThisDocument_Shutdown`.

- Pour les projets Microsoft Office Excel, les gestionnaires d'événements portent les noms suivants :

  - `Sheet1_Shutdown`

  - `Sheet2_Shutdown`

  - `Sheet3_Shutdown`

  - `ThisWorkbook_Shutdown`

> [!NOTE]
> Ne supprimez pas les contrôles par programme quand le gestionnaire d'événements **Shutdown** du document est actif. Les éléments d'interface utilisateur du document ne sont plus disponibles quand l'événement **Shutdown** se produit. Pour supprimer les contrôles avant la fermeture de l'application, ajoutez votre code à un autre gestionnaire d'événements tel que **BeforeClose** ou **BeforeSave**.

### <a name="event-handler-method-declarations"></a>Déclarations de méthode de gestionnaire d’événements
 Les mêmes arguments sont passés aux déclarations de méthode de gestionnaire d'événements : *sender* et *e*. Dans Excel, l'argument *sender* fait référence à la feuille, par exemple `Sheet1` ou `Sheet2`; dans Word, l'argument *sender* fait référence au document. L'argument *e* fait référence aux arguments standard d'un événement, qui ne sont pas utilisés dans ce cas.

 L'exemple de code suivant montre les gestionnaires d'événements par défaut dans les projets au niveau du document pour Word.

 :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet121":::
 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet121":::

 L'exemple de code suivant montre les gestionnaires d'événements par défaut dans les projets au niveau du document pour Excel.

> [!NOTE]
> L'exemple de code suivant montre les gestionnaires d'événements dans la classe `Sheet1` . Les noms des gestionnaires d'événements des autres classes d'élément hôte correspondent au nom de la classe. Par exemple, dans la classe `Sheet2` , le gestionnaire d'événements **Startup** s'appelle `Sheet2_Startup`. Dans la classe `ThisWorkbook` , le gestionnaire d'événements **Startup** s'appelle `ThisWorkbook_Startup`.

 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet83":::
 :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet83":::

### <a name="order-of-events-in-document-level-excel-projects"></a>Ordre des événements dans les projets Excel au niveau du document
 Les gestionnaires d'événements **Startup** dans les projets Excel sont appelés dans l'ordre suivant :

1. `ThisWorkbook_Startup`.

2. `Sheet1_Startup`.

3. `Sheet2_Startup`.

4. `Sheet3_Startup`.

5. Autres feuilles dans l'ordre.

   Les gestionnaires d'événements **Shutdown** dans une solution de classeur sont appelés dans l'ordre suivant :

6. `ThisWorkbook_Shutdown`.

7. `Sheet1_Shutdown`.

8. `Sheet2_Shutdown`.

9. `Sheet3_Shutdown`.

10. Autres feuilles dans l'ordre.

    L'ordre est déterminé lors de la compilation du projet. Si l'utilisateur réorganise les feuilles au moment de l'exécution, il ne change pas l'ordre dans lequel les événements sont déclenchés la prochaine fois que le classeur est ouvert ou fermé.

## <a name="vsto-add-in-projects"></a>Projets de complément VSTO
 Visual Studio fournit du code généré dans les compléments VSTO. Ce code déclenche deux événements différents : <xref:Microsoft.Office.Tools.AddInBase.Startup> et <xref:Microsoft.Office.Tools.AddInBase.Shutdown> .

### <a name="startup-event"></a>Startup (événement)
 L’événement <xref:Microsoft.Office.Tools.AddIn.Startup> est déclenché une fois que le complément VSTO est chargé et que tout le code d’initialisation dans l’assembly a été exécuté. Cet événement est géré par la méthode `ThisAddIn_Startup` dans le fichier de code généré.

 Le code dans le gestionnaire d’événements `ThisAddIn_Startup` est le premier code utilisateur à être exécuté, sauf si votre complément VSTO se substitue à la méthode <xref:Microsoft.Office.Tools.AddInBase.RequestComAddInAutomationService%2A> . Dans ce cas, le gestionnaire d'événements `ThisAddIn_Startup` est appelé après <xref:Microsoft.Office.Tools.AddInBase.RequestComAddInAutomationService%2A>.

 N’ajoutez pas de code dans le `ThisAdd-In_Startup` Gestionnaire d’événements si le code requiert l’ouverture d’un document. Au lieu de cela, ajoutez ce code à un événement que l'application Office déclenche quand un utilisateur crée ou ouvre un document. Pour plus d’informations, consultez [accéder à un document lorsque l’application Office démarre](../vsto/programming-vsto-add-ins.md#AccessingDocuments).

 Pour plus d’informations sur la séquence de démarrage des compléments VSTO, consultez [architecture des compléments VSTO](../vsto/architecture-of-vsto-add-ins.md).

### <a name="shutdown-event"></a>Shutdown (événement)
 L'événement <xref:Microsoft.Office.Tools.AddInBase.Shutdown> est déclenché quand le domaine d'application dans lequel votre code est chargé est sur le point d'être déchargé. Cet événement est géré par la méthode `ThisAddIn_Shutdown` dans le fichier de code généré. Ce gestionnaire d’événements est le dernier code utilisateur à être exécuté quand le complément VSTO est déchargé.

#### <a name="shutdown-event-in-outlook-vsto-add-ins"></a>Événement Shutdown dans les compléments VSTO Outlook
 L’événement <xref:Microsoft.Office.Tools.AddInBase.Shutdown> est déclenché uniquement quand l’utilisateur désactive le complément VSTO à l’aide de la boîte de dialogue Compléments COM dans Outlook. Il n'est pas déclenché quand vous quittez Outlook. Si vous disposez de code devant être exécuté quand vous quittez Outlook, gérez l'un ou l'autre des événements suivants :

- Événement <xref:Microsoft.Office.Interop.Outlook.ApplicationEvents_11_Event.Quit> de l'objet <xref:Microsoft.Office.Interop.Outlook.Application>

- Événement <xref:Microsoft.Office.Interop.Outlook.ExplorerEvents_10_Event.Close> de l'objet <xref:Microsoft.Office.Interop.Outlook.Explorer>

> [!NOTE]
> Vous pouvez forcer Outlook à déclencher l'événement <xref:Microsoft.Office.Tools.AddInBase.Shutdown> au moment de sa fermeture en modifiant le Registre. Toutefois, si un administrateur annule ce paramètre, tout code que vous ajouterez à la méthode `ThisAddIn_Shutdown` ne sera plus exécuté après la fermeture d'Outlook. Pour plus d’informations, consultez [modifications de l’arrêt pour Outlook 2010](/previous-versions/office/developer/office-2010/ee720183(v=office.14)).

## <a name="see-also"></a>Voir aussi
- [Développer des solutions Office](../vsto/developing-office-solutions.md)
- [Comment : créer des projets Office dans Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)
- [Personnaliser les personnalisations au niveau du document](../vsto/programming-document-level-customizations.md)
- [Programmer les compléments VSTO](../vsto/programming-vsto-add-ins.md)
- [Vue d’ensemble des modèles de projet Office](../vsto/office-project-templates-overview.md)
