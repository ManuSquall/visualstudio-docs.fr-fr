---
title: Programmer les compléments VSTO
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VST.ProjectItem.Addin
- VST.ProjectItem.AddinProject
- thisAddIn
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ICustomTaskPaneConsumer interface
- add-ins [Office development in Visual Studio], programming
- IRibbonExtensibility interface
- UI customizing [Office development in Visual Studio]
- Office applications [Office development in Visual Studio], application-level add-ins
- programming [Office development in Visual Studio], application-level add-ins
- ThisAddIn class
- user interfaces [Office development in Visual Studio], customizing
- writing code for Office solutions
- host items [Office development in Visual Studio], AddIn
- application development [Office development in Visual Studio], application-level add-ins
- add-ins [Office development in Visual Studio], ThisAddIn class
- application-level add-ins [Office development in Visual Studio], ThisAddIn class
- FormRegionStartup interface
- ThisAddIn_Startup
- application-level add-ins [Office development in Visual Studio], programming
- ThisAddIn_Shutdown
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 93470ebcea306d3cea762d60e061994b2bf27cc8
ms.sourcegitcommit: 3154387056160bf4c36ac8717a7fdc0cd9faf3f9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/06/2020
ms.locfileid: "78409729"
---
# <a name="program-vsto-add-ins"></a>Programmer les compléments VSTO
  Quand vous étendez une application Microsoft Office en créant un complément VSTO, vous écrivez directement le code par rapport à la classe `ThisAddIn` de votre projet. Vous pouvez utiliser cette classe pour effectuer des tâches telles qu’accéder au modèle objet de l’application hôte Microsoft Office, personnaliser l’interface utilisateur de l’application et exposer des objets de votre complément VSTO à d’autres solutions Office.

 [!INCLUDE[appliesto_allapp](../vsto/includes/appliesto-allapp-md.md)]

 Certains aspects de l’écriture de code des projets de complément VSTO diffèrent des autres types de projets dans Visual Studio. Une grande partie de ces différences ont pour origine la façon dont les modèles objet Office sont exposés au code managé. Pour plus d’informations, consultez [écrire du code dans les solutions Office](../vsto/writing-code-in-office-solutions.md).

 Pour obtenir des informations générales sur les compléments VSTO et d’autres types de solutions que vous pouvez créer à l’aide des outils de développement Office dans Visual Studio, consultez [vue d’ensemble &#40;du développement des solutions Office VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md).

## <a name="use-the-thisaddin-class"></a>Utiliser la classe ThisAddIn
 Vous pouvez commencer à écrire votre code de complément VSTO dans la classe `ThisAddIn` . Visual Studio génère automatiquement cette classe dans le fichier de code *ThisAddIn. vb* (dans [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)]) ou C#ThisAddIn.cs (dans) dans votre projet de complément VSTO. [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] instancie automatiquement cette classe quand l’application Microsoft Office charge votre complément VSTO.

 La classe `ThisAddIn` contient deux gestionnaires d'événements par défaut. Pour exécuter du code quand le complément VSTO est chargé, ajoutez du code au gestionnaire d’événements `ThisAddIn_Startup` . Pour exécuter du code juste avant que le complément VSTO soit déchargé, ajoutez du code au gestionnaire d’événements `ThisAddIn_Shutdown` . Pour plus d’informations sur ces gestionnaires d’événements, consultez [événements dans les projets Office](../vsto/events-in-office-projects.md).

> [!NOTE]
> Dans Outlook, par défaut, le gestionnaire d’événements `ThisAddIn_Shutdown` n’est pas toujours appelé quand le complément VSTO est déchargé. Pour plus d’informations, consultez [événements dans les projets Office](../vsto/events-in-office-projects.md).

### <a name="access-the-object-model-of-the-host-application"></a>Accéder au modèle objet de l’application hôte
 Pour accéder au modèle objet de l'application hôte, utilisez le champ `Application` de la classe `ThisAddIn` . Ce champ retourne un objet qui représente l'instance actuelle de l'application hôte. Le tableau suivant indique le type de la valeur de retour pour le champ `Application` dans chaque projet de complément VSTO.

|Application hôte|Type de valeur de retour|
|----------------------|-----------------------|
|Microsoft Office Excel|<xref:Microsoft.Office.Interop.Excel.Application>|
|Microsoft Office InfoPath|<xref:Microsoft.Office.Interop.InfoPath.Application>|
|Microsoft Office Outlook|<xref:Microsoft.Office.Interop.Outlook.Application>|
|Microsoft Office PowerPoint|[Application](/previous-versions/office/developer/office-2010/ff764034(v=office.14))|
|Microsoft Office Project|Microsoft.Office.Interop.MSProject.Application|
|Microsoft Office Visio|Microsoft.Office.Interop.Visio.Application|
|Microsoft Office Word|<xref:Microsoft.Office.Interop.Word.Application>|

 L’exemple de code suivant montre comment utiliser le champ `Application` pour créer un nouveau classeur dans un complément VSTO pour Microsoft Office Excel. Cet exemple est destiné à être exécuté à partir de la classe `ThisAddIn` .

```vb
Dim newWorkbook As Excel.Workbook = Me.Application.Workbooks.Add()
```

```csharp
Excel.Workbook newWorkbook = this.Application.Workbooks.Add(System.Type.Missing);
```

 Pour effectuer la même opération depuis l'extérieur de la classe `ThisAddIn` , utilisez l'objet `Globals` pour accéder à la classe `ThisAddIn` . Pour plus d’informations sur l’objet `Globals`, consultez [accès global aux objets dans les projets Office](../vsto/global-access-to-objects-in-office-projects.md).

```vb
Dim newWorkbook As Excel.Workbook = Globals.ThisAddIn.Application.Workbooks.Add()
```

```csharp
Excel.Workbook newWorkbook = Globals.ThisAddIn.Application.Workbooks.Add(System.Type.Missing);
```

 Pour plus d'informations sur les modèles objet d'applications Microsoft Office spécifiques, consultez les rubriques suivantes :

- [Vue d’ensemble du modèle objet Excel](../vsto/excel-object-model-overview.md)

- [Vue d’ensemble du modèle objet Word](../vsto/word-object-model-overview.md)

- [Vue d’ensemble du modèle objet Outlook](../vsto/outlook-object-model-overview.md)

- [Solutions InfoPath](../vsto/infopath-solutions.md)

- [Solutions PowerPoint](../vsto/powerpoint-solutions.md)

- [Solutions de projet](../vsto/project-solutions.md)

- [Vue d’ensemble du modèle objet Visio](../vsto/visio-object-model-overview.md)

### <a name="AccessingDocuments"></a>Accéder à un document lorsque l’application Office démarre
 Toutes les applications [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)] n'ouvrent pas automatiquement un document lorsque vous les démarrer, et aucune des applications [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] n'ouvre un document lorsque vous les démarrez. Par conséquent, n’ajoutez pas de code dans le gestionnaire d’événements `ThisAdd-In_Startup` si le code nécessite l’ouverture d’un document. Au lieu de cela, ajoutez ce code à un événement que l'application Office déclenche quand un utilisateur crée ou ouvre un document. Ainsi, vous pouvez garantir qu'un document est ouvert avant que votre code effectue des opérations dessus.

 L'exemple de code suivant fonctionne avec un document dans Word uniquement lorsque l'utilisateur crée un document ou ouvre un document existant.

 [!code-csharp[Trin_WordAddIn_Menus#3](../vsto/codesnippet/CSharp/trin_wordaddin_menus.cs/thisaddin.cs#3)]
 [!code-vb[Trin_WordAddIn_Menus#3](../vsto/codesnippet/VisualBasic/trin_wordaddin_menus.vb/thisaddin.vb#3)]

### <a name="thisaddin-members-to-use-for-other-tasks"></a>Membres ThisAddIn à utiliser pour d’autres tâches
 Le tableau suivant décrit d'autres tâches courantes et montre quels membres de la classe `ThisAddIn` utiliser pour effectuer ces tâches.

|Tâche|Membre à utiliser|
|----------|-------------------|
|Exécuter le code pour initialiser le complément VSTO quand ce dernier est chargé.|Ajouter le code à la méthode `ThisAddIn_Startup` . Il s'agit du gestionnaire d'événements par défaut pour l'événement <xref:Microsoft.Office.Tools.AddInBase.Startup> . Pour plus d’informations, consultez [événements dans les projets Office](../vsto/events-in-office-projects.md).|
|Exécuter le code pour nettoyer les ressources utilisées par le complément VSTO avant que ce dernier soit déchargé.|Ajouter le code à la méthode `ThisAddIn_Shutdown` . Il s'agit du gestionnaire d'événements par défaut pour l'événement <xref:Microsoft.Office.Tools.AddInBase.Shutdown> . Pour plus d’informations, consultez [événements dans les projets Office](../vsto/events-in-office-projects.md). **Remarque :**  Dans Outlook, par défaut, le gestionnaire d’événements `ThisAddIn_Startup` n’est pas toujours appelé quand le complément VSTO est déchargé. Pour plus d’informations, consultez [événements dans les projets Office](../vsto/events-in-office-projects.md).|
|Afficher un volet des tâches personnalisé.|Utiliser le champ `CustomTaskPanes` . Pour plus d’informations, consultez [volets de tâches personnalisés](../vsto/custom-task-panes.md).|
|Exposer les objets de votre complément VSTO à d'autres solutions Microsoft Office.|Remplacez la méthode <xref:Microsoft.Office.Tools.AddInBase.RequestComAddInAutomationService%2A> . Pour plus d’informations, consultez [appeler du code dans des compléments VSTO à partir d’autres solutions Office](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md).|
|Personnaliser une fonctionnalité du système Microsoft Office en implémentant une interface d'extensibilité.|Substituer la méthode <xref:Microsoft.Office.Tools.AddInBase.RequestService%2A> pour retourner une instance d'une classe qui implémente l'interface. Pour plus d’informations, consultez [personnaliser les fonctionnalités de l’interface utilisateur à l’aide d’interfaces d’extensibilité](../vsto/customizing-ui-features-by-using-extensibility-interfaces.md). **Remarque :**  Pour personnaliser l’interface ruban, vous pouvez également substituer la méthode <xref:Microsoft.Office.Tools.AddInBase.CreateRibbonExtensibilityObject%2A>.|

### <a name="understand-the-design-of-the-thisaddin-class"></a>Comprendre la conception de la classe ThisAddIn
 Dans les projets qui ciblent [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)], <xref:Microsoft.Office.Tools.AddIn> est une interface. La classe `ThisAddIn` dérive de la classe <xref:Microsoft.Office.Tools.AddInBase> . Cette classe de base redirige tous les appels à ses membres vers une implémentation interne de l'interface <xref:Microsoft.Office.Tools.AddIn> dans [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)].

 Dans les projets de complément VSTO pour Outlook, la classe `ThisAddIn` dérive de la classe `Microsoft.Office.Tools.Outlook.OutlookAddIn` dans les projets qui ciblent .NET Framework 3.5, et de <xref:Microsoft.Office.Tools.Outlook.OutlookAddInBase> dans les projets qui ciblent [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]. Ces classes de base fournissent des fonctionnalités supplémentaires permettant la prise en charge des zones de formulaire. Pour plus d’informations sur les zones de formulaire, consultez [créer des zones de formulaire Outlook](../vsto/creating-outlook-form-regions.md).

## <a name="customize-the-user-interface-of-microsoft-office-applications"></a>Personnaliser l’interface utilisateur des applications Microsoft Office
 Vous pouvez personnaliser par programmation l’interface utilisateur d’applications Microsoft Office à l’aide d’un complément VSTO. Par exemple, vous pouvez personnaliser le ruban, afficher un volet Office personnalisé, ou créer une zone de formulaire personnalisée dans Outlook. Pour plus d’informations, consultez [Personnalisation de l’interface utilisateur Office](../vsto/office-ui-customization.md).

 Visual Studio fournit des concepteurs et des classes que vous pouvez utiliser pour créer des volets Office personnalisés, des personnalisations de ruban et les zones de formulaire Outlook. Ces concepteurs et classes facilitent le processus de personnalisation de ces fonctionnalités. Pour plus d’informations, consultez [volets de tâches personnalisés](../vsto/custom-task-panes.md), [Concepteur de ruban](../vsto/ribbon-designer.md)et créer des zones de [formulaire Outlook](../vsto/creating-outlook-form-regions.md).

 Si vous souhaitez personnaliser l’une de ces fonctionnalités d’une manière non prise en charge par les classes et les concepteurs, vous pouvez aussi personnaliser ces fonctionnalités en implémentant une *interface d’extensibilité* dans votre complément VSTO. Pour plus d’informations, consultez [personnaliser les fonctionnalités de l’interface utilisateur à l’aide d’interfaces d’extensibilité](../vsto/customizing-ui-features-by-using-extensibility-interfaces.md).

 En outre, vous pouvez modifier l'interface utilisateur des documents Word et des classeurs Excel en générant des éléments hôtes qui étendent le comportement des documents et des classeurs. Cela vous permet d'ajouter des contrôles managés aux documents et aux feuilles de calcul. Pour plus d’informations, consultez [extension de documents Word et de classeurs Excel dans des compléments VSTO au moment](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)de l’exécution.

## <a name="call-code-in-vsto-add-ins-from-other-solutions"></a>Appeler du code dans des compléments VSTO à partir d’autres solutions
 Vous pouvez exposer des objets de votre complément VSTO à d’autres solutions, notamment à d’autres solutions Office. Cette possibilité s’avère utile si votre complément VSTO propose un service que vous voulez permettre à d’autres solutions d’utiliser. Par exemple, si vous avez un complément VSTO pour Microsoft Office Excel qui effectue des calculs sur des données financières à partir d’un service Web, d’autres solutions peuvent effectuer ces calculs en appelant le complément VSTO Excel au moment de l’exécution.

 Pour plus d’informations, consultez [appeler du code dans des compléments VSTO à partir d’autres solutions Office](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md).

## <a name="see-also"></a>Voir aussi
- [Développer des solutions Office](../vsto/developing-office-solutions.md)
- [Étendre des documents Word et des classeurs Excel dans des compléments VSTO au moment de l’exécution](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)
- [Appeler du code dans des compléments VSTO à partir d’autres solutions Office](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md)
- [Procédure pas à pas : appel de code dans un complément VSTO à partir de VBA](../vsto/walkthrough-calling-code-in-a-vsto-add-in-from-vba.md)
- [Personnaliser les fonctionnalités de l’interface utilisateur à l’aide des interfaces d’extensibilité](../vsto/customizing-ui-features-by-using-extensibility-interfaces.md)
- [Comment : créer des projets Office dans Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)
- [Architecture des compléments VSTO](../vsto/architecture-of-vsto-add-ins.md)
- [Écrire du code dans les solutions Office](../vsto/writing-code-in-office-solutions.md)
