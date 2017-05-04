---
title: "&#201;v&#233;nements dans les projets Office | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "Sheet1_Startup"
  - "ThisDocument_Shutdown"
  - "ThisDocument_Startup"
  - "compléments d’application (développement Office dans Visual Studio), événements"
  - "gestionnaires d'événements (développement Office dans Visual Studio)"
  - "ThisWorkbook_Startup"
  - "Sheet2_Startup"
  - "ThisWorkbook_Shutdown"
  - "personnalisations au niveau du document (développement Office dans Visual Studio), événements"
  - "Sheet2_Shutdown"
  - "Startup (événement)"
  - "Sheet3_Shutdown"
  - "compléments (développement Office dans Visual Studio), événements"
  - "Shutdown (événement)"
  - "ThisAddIn_Startup"
  - "Sheet3_Startup"
  - "Startup (méthode) (développement Office dans Visual Studio)"
  - "Shutdown (méthode) (développement Office dans Visual Studio)"
  - "Sheet1_Shutdown"
  - "événements (développement Office dans Visual Studio)"
  - "ThisAddIn_Shutdown"
ms.assetid: 666d7f23-ef85-4f2e-9cd3-258df5bdc6fd
caps.latest.revision: 51
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 50
---
# &#201;v&#233;nements dans les projets Office
  Chaque modèle de projet Office génère automatiquement plusieurs gestionnaires d'événements. Les gestionnaires d’événements pour les personnalisations au niveau du document sont légèrement différents de ceux pour les compléments VSTO.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
## Projets au niveau du document  
 Visual Studio fournit du code behind généré pour les documents ou feuilles de calcul nouveaux ou existants dans les personnalisations au niveau du document. Ce code déclenche deux événements différents : **Startup** et **Shutdown**.  
  
### Événement Startup  
 L'événement **Startup** est déclenché pour chacun des éléments hôtes \(document, classeur ou feuille de calcul\) après l'exécution du document et de tout le code d'initialisation dans l'assembly. Il s'agit de la dernière opération à exécuter dans le constructeur de la classe dans laquelle votre code est exécuté. Pour plus d’informations sur les éléments hôtes, consultez [Vue d'ensemble des éléments hôtes et des contrôles hôtes](../vsto/host-items-and-host-controls-overview.md).  
  
 Quand vous créez un projet au niveau du document, Visual Studio crée des gestionnaires d'événements pour l'événement **Startup** dans les fichiers de code générés :  
  
-   Pour les projets Microsoft Office Word, le gestionnaire d'événements s'appelle `ThisDocument_Startup`.  
  
-   Pour les projets Microsoft Office Excel, les gestionnaires d'événements portent les noms suivants :  
  
    -   `Sheet1_Startup`  
  
    -   `Sheet2_Startup`  
  
    -   `Sheet3_Startup`  
  
    -   `ThisWorkbook_Startup`  
  
### Événement Shutdown  
 L'événement  **Shutdown**  est déclenché pour chacun des éléments hôtes \(document ou feuille de calcul\) quand le domaine d'application dans lequel votre code est chargé est sur le point d'être déchargé. Il s'agit de la dernière opération à appeler dans la classe pendant le déchargement.  
  
 Quand vous créez un projet au niveau du document, Visual Studio crée des gestionnaires d'événements pour l'événement **Shutdown** dans les fichiers de code générés :  
  
-   Pour les projets Microsoft Office Word, le gestionnaire d'événements s'appelle `ThisDocument_Shutdown`.  
  
-   Pour les projets Microsoft Office Excel, les gestionnaires d'événements portent les noms suivants :  
  
    -   `Sheet1_Shutdown`  
  
    -   `Sheet2_Shutdown`  
  
    -   `Sheet3_Shutdown`  
  
    -   `ThisWorkbook_Shutdown`  
  
> [!NOTE]  
>  Ne supprimez pas les contrôles par programme quand le gestionnaire d'événements **Shutdown** du document est actif. Les éléments d'interface utilisateur du document ne sont plus disponibles quand l'événement **Shutdown** se produit. Pour supprimer les contrôles avant la fermeture de l'application, ajoutez votre code à un autre gestionnaire d'événements tel que **BeforeClose** ou **BeforeSave**.  
  
### Déclarations de méthode de gestionnaire d'événements  
 Les mêmes arguments sont passés aux déclarations de méthode de gestionnaire d'événements : *sender* et *e*. Dans Excel, l'argument *sender* fait référence à la feuille, par exemple `Sheet1` ou `Sheet2` ; dans Word, l'argument *sender* fait référence au document. L'argument *e* fait référence aux arguments standard d'un événement, qui ne sont pas utilisés dans ce cas.  
  
 L'exemple de code suivant montre les gestionnaires d'événements par défaut dans les projets au niveau du document pour Word.  
  
 [!code-csharp[Trin_VstcoreWordAutomation#121](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#121)]
 [!code-vb[Trin_VstcoreWordAutomation#121](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#121)]  
  
 L'exemple de code suivant montre les gestionnaires d'événements par défaut dans les projets au niveau du document pour Excel.  
  
> [!NOTE]  
>  L'exemple de code suivant montre les gestionnaires d'événements dans la classe `Sheet1`. Les noms des gestionnaires d'événements des autres classes d'élément hôte correspondent au nom de la classe. Par exemple, dans la classe `Sheet2`, le gestionnaire d'événements **Startup** s'appelle `Sheet2_Startup`. Dans la classe `ThisWorkbook`, le gestionnaire d'événements **Startup** s'appelle `ThisWorkbook_Startup`.  
  
 [!code-csharp[Trin_VstcoreExcelAutomation#83](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#83)]
 [!code-vb[Trin_VstcoreExcelAutomation#83](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#83)]  
  
### Ordre des événements dans les projets Excel au niveau du document  
 Les gestionnaires d'événements **Startup** dans les projets Excel sont appelés dans l'ordre suivant :  
  
1.  `ThisWorkbook_Startup`.  
  
2.  `Sheet1_Startup`.  
  
3.  `Sheet2_Startup`.  
  
4.  `Sheet3_Startup`.  
  
5.  Autres feuilles dans l'ordre.  
  
 Les gestionnaires d'événements  **Shutdown** dans une solution de classeur sont appelés dans l'ordre suivant :  
  
1.  `ThisWorkbook_Shutdown`.  
  
2.  `Sheet1_Shutdown`.  
  
3.  `Sheet2_Shutdown`.  
  
4.  `Sheet3_Shutdown`.  
  
5.  Autres feuilles dans l'ordre.  
  
 L'ordre est déterminé lors de la compilation du projet. Si l'utilisateur réorganise les feuilles au moment de l'exécution, il ne change pas l'ordre dans lequel les événements sont déclenchés la prochaine fois que le classeur est ouvert ou fermé.  
  
## Projets de complément VSTO  
 Visual Studio fournit du code généré dans les compléments VSTO. Ce code déclenche deux événements différents : <xref:Microsoft.Office.Tools.AddInBase.Startup> et <xref:Microsoft.Office.Tools.AddInBase.Shutdown>.  
  
### Événement Startup  
 L’événement <xref:Microsoft.Office.Tools.AddIn.Startup> est déclenché une fois que le complément VSTO est chargé et que tout le code d’initialisation dans l’assembly a été exécuté. Cet événement est géré par la méthode `ThisAddIn_Startup` dans le fichier de code généré.  
  
 Le code dans le gestionnaire d’événements `ThisAddIn_Startup` est le premier code utilisateur à être exécuté, sauf si votre complément VSTO se substitue à la méthode <xref:Microsoft.Office.Tools.AddInBase.RequestComAddInAutomationService%2A>. Dans ce cas, le gestionnaire d'événements `ThisAddIn_Startup` est appelé après <xref:Microsoft.Office.Tools.AddInBase.RequestComAddInAutomationService%2A>.  
  
 N'ajoutez pas de code au gestionnaire d'événements `ThisAdd-In_Startup` si le code nécessite un document ouvert. Au lieu de cela, ajoutez ce code à un événement que l'application Office déclenche quand un utilisateur crée ou ouvre un document. Pour plus d'informations, consultez [Accès à un document lorsque l'application Office démarre](../vsto/programming-vsto-add-ins.md#AccessingDocuments).  
  
 Pour plus d’informations sur la séquence de démarrage des compléments VSTO, consultez [Architecture des compléments VSTO](../vsto/architecture-of-vsto-add-ins.md).  
  
### Événement Shutdown  
 L'événement <xref:Microsoft.Office.Tools.AddInBase.Shutdown> est déclenché quand le domaine d'application dans lequel votre code est chargé est sur le point d'être déchargé. Cet événement est géré par la méthode `ThisAddIn_Shutdown` dans le fichier de code généré. Ce gestionnaire d’événements est le dernier code utilisateur à être exécuté quand le complément VSTO est déchargé.  
  
#### Événement Shutdown dans les compléments VSTO Outlook  
 L’événement <xref:Microsoft.Office.Tools.AddInBase.Shutdown> est déclenché uniquement quand l’utilisateur désactive le complément VSTO à l’aide de la boîte de dialogue Compléments COM dans Outlook. Il n'est pas déclenché quand vous quittez Outlook. Si vous disposez de code devant être exécuté quand vous quittez Outlook, gérez l'un ou l'autre des événements suivants :  
  
-   Événement <xref:Microsoft.Office.Interop.Outlook.ApplicationEvents_11_Event.Quit> de l'objet <xref:Microsoft.Office.Interop.Outlook.Application>  
  
-   Événement <xref:Microsoft.Office.Interop.Outlook.ExplorerEvents_10_Event.Close> de l'objet <xref:Microsoft.Office.Interop.Outlook.Explorer>  
  
> [!NOTE]  
>  Vous pouvez forcer Outlook à déclencher l'événement <xref:Microsoft.Office.Tools.AddInBase.Shutdown> au moment de sa fermeture en modifiant le Registre. Toutefois, si un administrateur annule ce paramètre, tout code que vous ajouterez à la méthode `ThisAddIn_Shutdown` ne sera plus exécuté après la fermeture d'Outlook. Pour plus d’informations, consultez [Modifications de l’arrêt d’Outlook 2010](http://go.microsoft.com/fwlink/?LinkID=184614).  
  
## Voir aussi  
 [Développement de solutions Office](../vsto/developing-office-solutions.md)   
 [Comment : créer des projets Office dans Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [Programmation de personnalisations au niveau du document](../vsto/programming-document-level-customizations.md)   
 [Programmation de compléments VSTO](../vsto/programming-vsto-add-ins.md)   
 [Vue d'ensemble des modèles de projet Office](../vsto/office-project-templates-overview.md)  
  
  