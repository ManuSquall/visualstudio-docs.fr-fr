---
title: Programme VSTO Add-ins
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
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/13/2020
ms.locfileid: "79301705"
---
# <a name="program-vsto-add-ins"></a>Programme VSTO Add-ins
  Quand vous étendez une application Microsoft Office en créant un complément VSTO, vous écrivez directement le code par rapport à la classe `ThisAddIn` de votre projet. Vous pouvez utiliser cette classe pour effectuer des tâches telles qu’accéder au modèle objet de l’application hôte Microsoft Office, personnaliser l’interface utilisateur de l’application et exposer des objets de votre complément VSTO à d’autres solutions Office.

 [!INCLUDE[appliesto_allapp](../vsto/includes/appliesto-allapp-md.md)]

 Certains aspects de l’écriture de code des projets de complément VSTO diffèrent des autres types de projets dans Visual Studio. Une grande partie de ces différences ont pour origine la façon dont les modèles objet Office sont exposés au code managé. Pour plus d’informations, voir [Code Écrire dans les solutions Office](../vsto/writing-code-in-office-solutions.md).

 Pour obtenir des informations générales sur les add-ins VSTO et d’autres types de solutions que vous pouvez créer en utilisant les outils de développement Office dans Visual Studio, consultez [l’aperçu du développement des solutions Office &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md).

## <a name="use-the-thisaddin-class"></a>Utilisez la classe ThisAddIn
 Vous pouvez commencer à écrire votre code de complément VSTO dans la classe `ThisAddIn` . Visual Studio génère automatiquement cette classe dans le fichier [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)]de code *ThisAddIn.vb* (en) ou *ThisAddIn.cs* (en C) dans votre projet VSTO Add-in. [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] instancie automatiquement cette classe quand l’application Microsoft Office charge votre complément VSTO.

 La classe `ThisAddIn` contient deux gestionnaires d'événements par défaut. Pour exécuter du code quand le complément VSTO est chargé, ajoutez du code au gestionnaire d’événements `ThisAddIn_Startup` . Pour exécuter du code juste avant que le complément VSTO soit déchargé, ajoutez du code au gestionnaire d’événements `ThisAddIn_Shutdown` . Pour plus d’informations sur ces gestionnaires d’événements, voir [les projets Événements en bureau](../vsto/events-in-office-projects.md).

> [!NOTE]
> Dans Outlook, par défaut, le gestionnaire d’événements `ThisAddIn_Shutdown` n’est pas toujours appelé quand le complément VSTO est déchargé. Pour plus d’informations, voir [Événements en bureau projets](../vsto/events-in-office-projects.md).

### <a name="access-the-object-model-of-the-host-application"></a>Accédez au modèle d’objet de l’application hôte
 Pour accéder au modèle objet de l'application hôte, utilisez le champ `Application` de la classe `ThisAddIn` . Ce champ retourne un objet qui représente l'instance actuelle de l'application hôte. Le tableau suivant indique le type de la valeur de retour pour le champ `Application` dans chaque projet de complément VSTO.

|Application hôte|Type de valeur de retour|
|----------------------|-----------------------|
|Microsoft Office Excel|<xref:Microsoft.Office.Interop.Excel.Application>|
|Microsoft Office InfoPath|<xref:Microsoft.Office.Interop.InfoPath.Application>|
|Microsoft Office Outlook|<xref:Microsoft.Office.Interop.Outlook.Application>|
|Microsoft Office PowerPoint|[Application](/previous-versions/office/developer/office-2010/ff764034(v=office.14))|
|Microsoft Office Project|Microsoft.Office.Interop.MSProject.Application|
|Microsoft Office Visio|Microsoft.Office.Interop.Visio.Application|
|Microsoft Office Word|<xref:Microsoft.Office.Interop.Word.Application>|

 L’exemple de code suivant `Application` montre comment utiliser le champ pour créer un nouveau cahier de travail dans un add-in VSTO pour Microsoft Office Excel. Cet exemple est destiné à être exécuté à partir de la classe `ThisAddIn` .

```vb
Dim newWorkbook As Excel.Workbook = Me.Application.Workbooks.Add()
```

```csharp
Excel.Workbook newWorkbook = this.Application.Workbooks.Add(System.Type.Missing);
```

 Pour effectuer la même opération depuis l'extérieur de la classe `ThisAddIn` , utilisez l'objet `Globals` pour accéder à la classe `ThisAddIn` . Pour plus d’informations sur l’objet, `Globals` voir [l’accès global aux objets dans les projets Office](../vsto/global-access-to-objects-in-office-projects.md).

```vb
Dim newWorkbook As Excel.Workbook = Globals.ThisAddIn.Application.Workbooks.Add()
```

```csharp
Excel.Workbook newWorkbook = Globals.ThisAddIn.Application.Workbooks.Add(System.Type.Missing);
```

 Pour plus d'informations sur les modèles objet d'applications Microsoft Office spécifiques, consultez les rubriques suivantes :

- [Aperçu du modèle d’objet Excel](../vsto/excel-object-model-overview.md)

- [Aperçu du modèle d’objet de mot](../vsto/word-object-model-overview.md)

- [Aperçu du modèle d’objet Outlook](../vsto/outlook-object-model-overview.md)

- [solutions InfoPath](../vsto/infopath-solutions.md)

- [Solutions PowerPoint](../vsto/powerpoint-solutions.md)

- [Solutions de projet](../vsto/project-solutions.md)

- [Aperçu du modèle d’objet Visio](../vsto/visio-object-model-overview.md)

### <a name="access-a-document-when-the-office-application-starts"></a><a name="AccessingDocuments"></a>Accédez à un document lorsque la demande du Bureau commence
 Toutes les applications [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)] n'ouvrent pas automatiquement un document lorsque vous les démarrer, et aucune des applications [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] n'ouvre un document lorsque vous les démarrez. Par conséquent, n’ajoutez `ThisAdd-In_Startup` pas de code dans le gestionnaire d’événements si le code nécessite l’ouverture d’un document. Au lieu de cela, ajoutez ce code à un événement que l'application Office déclenche quand un utilisateur crée ou ouvre un document. Ainsi, vous pouvez garantir qu'un document est ouvert avant que votre code effectue des opérations dessus.

 L'exemple de code suivant fonctionne avec un document dans Word uniquement lorsque l'utilisateur crée un document ou ouvre un document existant.

 [!code-csharp[Trin_WordAddIn_Menus#3](../vsto/codesnippet/CSharp/trin_wordaddin_menus.cs/thisaddin.cs#3)]
 [!code-vb[Trin_WordAddIn_Menus#3](../vsto/codesnippet/VisualBasic/trin_wordaddin_menus.vb/thisaddin.vb#3)]

### <a name="thisaddin-members-to-use-for-other-tasks"></a>ThisAddIn membres à utiliser pour d’autres tâches
 Le tableau suivant décrit d'autres tâches courantes et montre quels membres de la classe `ThisAddIn` utiliser pour effectuer ces tâches.

|Tâche|Membre à utiliser|
|----------|-------------------|
|Exécuter le code pour initialiser le complément VSTO quand ce dernier est chargé.|Ajouter le code à la méthode `ThisAddIn_Startup` . Il s'agit du gestionnaire d'événements par défaut pour l'événement <xref:Microsoft.Office.Tools.AddInBase.Startup> . Pour plus d’informations, voir [Événements en bureau projets](../vsto/events-in-office-projects.md).|
|Exécuter le code pour nettoyer les ressources utilisées par le complément VSTO avant que ce dernier soit déchargé.|Ajouter le code à la méthode `ThisAddIn_Shutdown` . Il s'agit du gestionnaire d'événements par défaut pour l'événement <xref:Microsoft.Office.Tools.AddInBase.Shutdown> . Pour plus d’informations, voir [Événements en bureau projets](../vsto/events-in-office-projects.md). **Note:**  Dans Outlook, par `ThisAddIn_Startup` défaut, le gestionnaire d’événements n’est pas toujours appelé lorsque l’add-in VSTO est déchargé. Pour plus d’informations, voir [Événements en bureau projets](../vsto/events-in-office-projects.md).|
|Afficher un volet des tâches personnalisé.|Utiliser le champ `CustomTaskPanes` . Pour plus d’informations, voir [volets de tâches personnalisées](../vsto/custom-task-panes.md).|
|Exposer les objets de votre complément VSTO à d'autres solutions Microsoft Office.|Remplacez la méthode <xref:Microsoft.Office.Tools.AddInBase.RequestComAddInAutomationService%2A> . Pour plus d’informations, voir [Code d’appel dans les add-ins VSTO d’autres solutions Office](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md).|
|Personnaliser une fonctionnalité du système Microsoft Office en implémentant une interface d'extensibilité.|Substituer la méthode <xref:Microsoft.Office.Tools.AddInBase.RequestService%2A> pour retourner une instance d'une classe qui implémente l'interface. Pour plus d’informations, consultez [les fonctionnalités d’interface utilisateur Customize en utilisant des interfaces d’extéponsabilité](../vsto/customizing-ui-features-by-using-extensibility-interfaces.md). **Note:**  Pour personnaliser l’interface utilisateur ruban, vous <xref:Microsoft.Office.Tools.AddInBase.CreateRibbonExtensibilityObject%2A> pouvez également remplacer la méthode.|

### <a name="understand-the-design-of-the-thisaddin-class"></a>Comprendre la conception de la classe ThisAddIn
 Dans les projets qui ciblent [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)], <xref:Microsoft.Office.Tools.AddIn> est une interface. La classe `ThisAddIn` dérive de la classe <xref:Microsoft.Office.Tools.AddInBase> . Cette classe de base redirige tous les appels à ses membres vers une implémentation interne de l'interface <xref:Microsoft.Office.Tools.AddIn> dans [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)].

 Dans les projets de complément VSTO pour Outlook, la classe `ThisAddIn` dérive de la classe `Microsoft.Office.Tools.Outlook.OutlookAddIn` dans les projets qui ciblent .NET Framework 3.5, et de <xref:Microsoft.Office.Tools.Outlook.OutlookAddInBase> dans les projets qui ciblent [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]. Ces classes de base fournissent des fonctionnalités supplémentaires permettant la prise en charge des zones de formulaire. Pour plus d’informations sur les régions de forme, voir [Create Outlook former regions](../vsto/creating-outlook-form-regions.md).

## <a name="customize-the-user-interface-of-microsoft-office-applications"></a>Personnaliser l’interface utilisateur des applications Microsoft Office
 Vous pouvez personnaliser par programmation l’interface utilisateur d’applications Microsoft Office à l’aide d’un complément VSTO. Par exemple, vous pouvez personnaliser le ruban, afficher un volet Office personnalisé, ou créer une zone de formulaire personnalisée dans Outlook. Pour plus d’informations, voir [La personnalisation de l’interface utilisateur Office](../vsto/office-ui-customization.md).

 Visual Studio fournit des concepteurs et des classes que vous pouvez utiliser pour créer des volets Office personnalisés, des personnalisations de ruban et les zones de formulaire Outlook. Ces concepteurs et classes facilitent le processus de personnalisation de ces fonctionnalités. Pour plus d’informations, voir [les volets de tâche personnalisés](../vsto/custom-task-panes.md), [Ruban Designer](../vsto/ribbon-designer.md), et Créer [des régions de forme Outlook](../vsto/creating-outlook-form-regions.md).

 Si vous souhaitez personnaliser l’une de ces fonctionnalités d’une manière non prise en charge par les classes et les concepteurs, vous pouvez aussi personnaliser ces fonctionnalités en implémentant une *interface d’extensibilité* dans votre complément VSTO. Pour plus d’informations, consultez [les fonctionnalités d’interface utilisateur Customize en utilisant des interfaces d’extéponsabilité](../vsto/customizing-ui-features-by-using-extensibility-interfaces.md).

 En outre, vous pouvez modifier l'interface utilisateur des documents Word et des classeurs Excel en générant des éléments hôtes qui étendent le comportement des documents et des classeurs. Cela vous permet d'ajouter des contrôles managés aux documents et aux feuilles de calcul. Pour plus d’informations, consultez [les documents Extend Word et les cahiers de travail Excel dans les add-ins VSTO à l’heure de l’exécution](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).

## <a name="call-code-in-vsto-add-ins-from-other-solutions"></a>Code d’appel dans les add-ins VSTO d’autres solutions
 Vous pouvez exposer des objets de votre complément VSTO à d’autres solutions, notamment à d’autres solutions Office. Cette possibilité s’avère utile si votre complément VSTO propose un service que vous voulez permettre à d’autres solutions d’utiliser. Par exemple, si vous avez un add-in VSTO pour Microsoft Office Excel qui effectue des calculs sur les données financières d’un service Web, d’autres solutions peuvent effectuer ces calculs en appelant dans l’Add-in Excel VSTO au moment de l’exécution.

 Pour plus d’informations, voir [Code d’appel dans les add-ins VSTO d’autres solutions Office](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md).

## <a name="see-also"></a>Voir aussi
- [Développer des solutions Office](../vsto/developing-office-solutions.md)
- [Extend Word documents et cahiers de travail Excel dans VSTO Add-ins à l’heure de l’exécution](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)
- [Code d’appel dans les add-ins VSTO d’autres solutions Office](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md)
- [Procédure pas à pas : Code d’appel dans un add-in VSTO de VBA](../vsto/walkthrough-calling-code-in-a-vsto-add-in-from-vba.md)
- [Personnaliser les fonctionnalités d’interface utilisateur en utilisant des interfaces d’extéabilité](../vsto/customizing-ui-features-by-using-extensibility-interfaces.md)
- [Comment : Créer des projets Office dans Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)
- [Architecture of VSTO Add-ins](../vsto/architecture-of-vsto-add-ins.md)
- [Rédiger du code dans les solutions Office](../vsto/writing-code-in-office-solutions.md)
