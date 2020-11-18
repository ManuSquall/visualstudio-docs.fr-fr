---
title: Création de solutions de flux de travail SharePoint | Microsoft Docs
description: Créer des solutions de flux de travail SharePoint à l’aide d’outils pour créer des flux de travail personnalisés qui gèrent le cycle de vie des documents et des éléments de liste dans les sites Web SharePoint.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: overview
f1_keywords:
- VSTO.NewSharePointWorkflowWizard.Page3
- VS.SharePointTools.Workflow.WorkflowName
- VSTO.NewSharePointWorkflowWizard.Page2
- VSTO.NewSharePointWorkflowWizard.Page1
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, workflows
- workflows [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: dd3f88df661537434c79a8b0049f90ddbce14c70
ms.sourcegitcommit: ad2c820b280b523a7f7aef89742cdb719354748f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94850609"
---
# <a name="create-sharepoint-workflow-solutions"></a>Créer des solutions de flux de travail SharePoint

[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] fournit des outils pour vous aider à créer des flux de travail personnalisés qui gèrent le cycle de vie des documents et des éléments de liste dans un site Web SharePoint. Les éléments fournis incluent un concepteur, un ensemble de contrôles d’activité et les références d’assembly nécessaires. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] comprend également l' **Assistant Personnalisation de SharePoint**, pour faciliter la création et la configuration des flux de travail.

Pour plus d’informations sur SharePoint, consultez [produits et technologies Microsoft SharePoint](/sharepoint/dev/).

## <a name="workflows-in-sharepoint"></a>Flux de travail dans SharePoint
 Lorsque vous ajoutez un flux de travail à une bibliothèque ou à une liste SharePoint, vous appliquez un processus d’entreprise à tous les éléments de la bibliothèque ou de la liste. Un flux de travail décrit les actions que le système ou les utilisateurs doivent effectuer sur chaque élément, comme l’envoi de l’élément à modifier, puis le réviser. Ces actions, appelées *activités*, sont les blocs de construction du flux de travail.

 Vous pouvez créer des flux de travail SharePoint dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] et les déployer sur un site Web SharePoint. Une fois qu’un flux de travail est déployé sur SharePoint, vous l’associez à une bibliothèque ou une liste. Il peut ensuite être démarré automatiquement, par un processus ou manuellement, par un utilisateur. Pour plus d’informations sur l’opération de flux de travail, consultez [développer des flux de travail SharePoint à l’aide de Visual Studio](/sharepoint/dev/general-development/develop-sharepoint-workflows-using-visual-studio).

## <a name="create-custom-sharepoint-workflows"></a>Créer des flux de travail SharePoint personnalisés
 Deux projets de flux de travail SharePoint sont disponibles dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] : **Workflow séquentiel** et **flux de travail d’ordinateur d’État**.

 Un *flux de travail séquentiel* représente une série d’étapes. Les étapes sont exécutées l’une après l’autre jusqu’à la fin de la dernière activité. Les workflows séquentiels sont toujours strictement séquentiels dans leur exécution. Étant donné qu’ils peuvent recevoir des événements externes et inclure des flux logiques parallèles, l’ordre exact d’exécution peut varier. L’illustration suivante montre un exemple de workflow séquentiel.

 ![Flux de travail séquentiel](../sharepoint/media/sp-sequential.png "Flux de travail séquentiel")

 Un *flux de travail d’ordinateur d’État* représente un ensemble d’États, de transitions et d’actions. Les étapes d’un flux de travail d’ordinateur d’État s’exécutent de façon asynchrone. Cela signifie qu’elles ne sont pas nécessairement exécutées l’une après l’autre, mais qu’elles sont déclenchées par des actions et des États. Un État est affecté comme état de démarrage, puis, en fonction d’un événement, une transition est effectuée vers un autre État. La machine à États peut avoir un état final qui détermine la fin du Workflow. Le diagramme suivant montre un exemple de workflow d’ordinateur d’État.

 ![Flux de travail de l'ordinateur d'état](../sharepoint/media/sp-state.png "Flux de travail de l'ordinateur d'état")

 Pour plus d’informations sur les types de flux de travail, consultez [types de flux de travail](/previous-versions/office/developer/sharepoint-2010/ms468447(v=office.14)).

### <a name="use-the-wizard"></a>Utiliser l’Assistant
 Lorsque vous créez un projet de flux de travail SharePoint dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] , vous spécifiez d’abord ses paramètres dans l' **Assistant Personnalisation de SharePoint**. L’Assistant utilise ces paramètres pour créer un projet dans **Explorateur de solutions**. Ce projet contient un fichier de code, plusieurs fichiers utilisés pour déployer le flux de travail, ainsi que des références aux assemblys requis pour créer un flux de travail SharePoint personnalisé.

 Après avoir créé le flux de travail, vous pouvez modifier ses propriétés dans la Fenêtre Propriétés. Bien que la plupart des propriétés de flux de travail puissent être modifiées directement dans le Fenêtre Propriétés, vous devez cliquer sur un bouton de sélection (![ellipse ASP.net Mobile designer](../sharepoint/media/mwellipsis.gif "Bouton de sélection du concepteur ASP.NET mobile")) pour modifier leurs valeurs. Ce bouton redémarre l' **Assistant Personnalisation de SharePoint**. Une fois que vous avez modifié la valeur de la propriété, cliquez sur le bouton **Terminer** pour la finaliser.

> [!NOTE]
> La propriété **type de workflow** est en lecture seule et ne peut pas être modifiée. Si vous souhaitez modifier le type de flux de travail, vous devez créer un autre flux de travail.

## <a name="design-a-sharepoint-workflow"></a>Concevoir un flux de travail SharePoint
 Une fois que vous avez défini toutes les étapes du processus d’entreprise, utilisez le [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Concepteur de workflow pour concevoir le flux de travail SharePoint. Pour ouvrir le concepteur, double-cliquez sur Workflow1.cs ou Workflow1. vb dans **Explorateur de solutions**, ou ouvrez le menu contextuel de l’un de ces fichiers, puis choisissez **ouvrir**.

### <a name="activities"></a>Activités
 Pour concevoir un flux de travail, ajoutez des activités de la **boîte à outils** à une planification de *flux de travail* sur le concepteur. Une planification de flux de travail contient la séquence d’activités dans l’ordre dans lequel elles doivent être exécutées.

 Il existe deux types d’activité :

- Les *activités simples* exécutent une seule unité de travail, par exemple « délai pour 1 jour » ou « démarrer le service Web ».

- Les *activités composites* contiennent d’autres activités ; par exemple, une activité conditionnelle peut contenir deux branches.

  Les deux types d’activités sont disponibles dans la **boîte à outils**.

  Les activités peuvent avoir des propriétés, des méthodes et des événements. Utilisez la fenêtre **Propriétés** pour définir les propriétés d’une activité.

  Vous pouvez également créer une activité personnalisée. Pour plus d’informations, consultez [procédure pas à pas : créer une activité de flux de travail de site personnalisé](../sharepoint/walkthrough-create-a-custom-site-workflow-activity.md).

  Les activités sont organisées dans les onglets suivants de la **boîte à outils**:

- **Flux de travail SharePoint**

- **Windows Workflow v 3.0**

- **Windows Workflow v 3.5**

  Les activités de flux de travail principales ne sont pas toutes prises en charge par SharePoint. Pour plus d’informations, consultez la [vue d’ensemble des activités de flux de travail pour Windows SharePoint Services](/previous-versions/office/developer/sharepoint-2010/ms446847(v=office.14)).

#### <a name="sharepoint-workflow-activities"></a>Activités de flux de travail SharePoint
 Les onglets de **flux de travail SharePoint** contiennent des activités spécialisées à utiliser dans [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] . Ces activités simplifient et rationalisent le développement des flux de travail du cycle de vie des documents. Pour plus d’informations sur les activités listées dans l’onglet **flux de travail SharePoint** , consultez la [vue d’ensemble des activités de flux de travail pour Windows SharePoint Services](/previous-versions/office/developer/sharepoint-2010/ms446847(v=office.14)).

#### <a name="windows-workflow-activities"></a>Activités de flux de travail Windows
 Les onglets **Windows Workflow** contiennent les activités fournies par le [!INCLUDE[TLA#tla_workflow](../sharepoint/includes/tlasharptla-workflow-md.md)] . Vous pouvez utiliser ces activités pour créer des planifications de flux de travail pour n’importe quel type d’application Windows Workflow.

 Pour plus d’informations sur les activités figurant sous l’onglet **Windows workflows** , consultez [Windows Workflow Foundation des activités](/previous-versions/dotnet/netframework-3.5/ms733615(v=vs.90)). Pour plus d’informations sur la Windows Workflow Foundation, consultez [Windows Workflow Foundation vue d’ensemble](/previous-versions/dotnet/netframework-3.5/ms734631(v=vs.90)).

### <a name="work-with-activities-in-the-designer"></a>Utiliser des activités dans le concepteur
 Votre planification de flux de travail peut contenir une combinaison d’activités de flux de travail Windows et d’activités de flux de travail SharePoint.

 Le concepteur affiche des signaux visuels pour vous aider à positionner et à configurer correctement les activités. Lorsque vous faites glisser ou copiez une activité vers la planification de workflow, le concepteur affiche les icônes de signe plus (+) vertes qui indiquent les emplacements valides pour cette activité dans le Workflow. Vous ne pouvez pas positionner une activité à un emplacement où elle ne serait pas valide. Par exemple, vous ne pouvez pas placer une activité d’envoi comme première activité dans une branche d’activité listen. Pour plus d’informations, consultez [Centre de développement SharePoint Designer](https://developer.microsoft.com/office/docs).

## <a name="collect-information-during-the-workflow"></a>Collecter des informations pendant le flux de travail
 Vous souhaiterez peut-être collecter des informations auprès des utilisateurs à des moments prédéfinis dans le flux de travail. Vous pouvez collecter des informations à l’aide de formulaires ou de propriétés d’élément.

### <a name="forms"></a>Formulaires
 Les formulaires sont semblables à des boîtes de dialogue qui contiennent des questions et fournissent des moyens permettant aux utilisateurs de fournir des réponses.

 Il existe quatre types de formulaires qui peuvent être utilisés dans un flux de travail :

- Association

- Initiation

- Modification

- Tâche

  Parmi celles-ci, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] citons les modèles d’élément pour les formulaires d’association et d’initiation. Un exemple de *formulaire d’association* est un formulaire qui permet à l’administrateur d’installer le flux de travail d’entrer des paramètres liés au flux de travail, tels qu’une limite de dépense pour un flux de travail de dépense. Un exemple de *formulaire d’initiation* est un formulaire qui permet à l’utilisateur d’un flux de travail d’entrer le montant qu’il a passé dans le Workflow. Pour plus d’informations sur ces types de formulaires, consultez [modèles de projet et d’élément de projet SharePoint](../sharepoint/sharepoint-project-and-project-item-templates.md).

### <a name="item-properties"></a>Propriétés de l’élément
 Vous pouvez également collecter des informations auprès des utilisateurs à l’aide des propriétés d’un élément dans la bibliothèque ou la liste SharePoint. Le fichier de code principal (Workflow1.cs ou Workflow1. vb) déclare une instance de la classe Microsoft. SharePoint. Workflow. SPWorkflowActivationProperties. WorkflowProperties nommée `workflowProperties` . Utilisez l' `workflowProperties` objet pour accéder aux propriétés de la bibliothèque ou de la liste dans le code. Pour obtenir un exemple, consultez [procédure pas à pas : créer et déboguer une solution de flux de travail SharePoint](../sharepoint/walkthrough-creating-and-debugging-a-sharepoint-workflow-solution.md).

## <a name="debug-a-sharepoint-workflow-template"></a>Déboguer un modèle de flux de travail SharePoint
 Vous pouvez déboguer un projet de flux de travail SharePoint de la même façon que vous déboguez d’autres [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] projets Web. Quand vous démarrez le [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] débogueur, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] utilise les paramètres que vous spécifiez dans l' **Assistant Personnalisation de SharePoint** pour ouvrir le site Web SharePoint approprié et associer automatiquement le modèle de flux de travail à la bibliothèque ou la liste appropriée. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] attache également le [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] débogueur au [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] processus nommé *w3wp.exe*.

 Pour tester le flux de travail, vous devez le démarrer manuellement. Pour plus d’informations, consultez la section « débogage de flux de travail » dans [débogage de solutions SharePoint](../sharepoint/debugging-sharepoint-solutions.md). Pour plus d’informations sur le [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] débogage d’applications Web, consultez [Déboguer des applications et des scripts Web](../debugger/how-to-enable-debugging-for-aspnet-applications.md).

## <a name="deploy-a-sharepoint-workflow-template"></a>Déployer un modèle de flux de travail SharePoint
 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Les projets de flux de travail SharePoint se déploient comme d’autres [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] projets SharePoint. Pour plus d’informations, consultez [empaqueter et déployer des solutions SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md).

## <a name="import-globally-reusable-workflows"></a>Importer des flux de travail réutilisables globalement
 Outre la création de flux de travail réutilisables spécifiques au site, SharePoint Designer vous permet de créer des flux de travail *réutilisables globalement*, qui sont des flux de travail qui peuvent être utilisés par n’importe quel site SharePoint. Le projet importer le flux de travail réutilisable dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] n’importe pas actuellement les flux de travail réutilisables globalement. Toutefois, vous pouvez utiliser SharePoint Designer pour convertir un flux de travail réutilisable globalement en flux de travail réutilisable, ou importer le flux de travail en tant que flux de travail déclaratif non converti. Pour plus d’informations, consultez [importer des éléments à partir d’un site SharePoint existant](../sharepoint/importing-items-from-an-existing-sharepoint-site.md).

## <a name="related-topics"></a>Rubriques connexes

|Intitulé|Description|
|-----------|-----------------|
|[Procédure pas à pas : créer et déboguer une solution de flux de travail SharePoint](../sharepoint/walkthrough-creating-and-debugging-a-sharepoint-workflow-solution.md)|Vous guide pas à pas dans la création et le débogage d’un [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] flux de travail simple.|
|[Procédure pas à pas : créer un flux de travail avec des formulaires d’association et d’initiation](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md)|Vous guide pas à pas pour créer un flux de travail plus complet [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] complet avec des formulaires d’association et d’initiation.|
|[Procédure pas à pas : ajouter une page d’application à un flux de travail](../sharepoint/walkthrough-add-an-application-page-to-a-workflow.md)|S’appuie sur la rubrique [procédure pas à pas : créer un flux de travail avec des formulaires d’association et d’initiation](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md) en ajoutant une page d’application *. aspx* supplémentaire qui rend compte des données entrées dans le Workflow.|
|[Procédure pas à pas : créer une activité de flux de travail de site personnalisé](../sharepoint/walkthrough-create-a-custom-site-workflow-activity.md)|Montre comment effectuer deux tâches principales : créer un flux de travail au niveau du site et créer une activité de flux de travail personnalisée.|
|[Procédure pas à pas : importer un flux de travail réutilisable SharePoint Designer dans Visual Studio](../sharepoint/walkthrough-import-a-sharepoint-designer-reusable-workflow-into-visual-studio.md)|Montre comment importer des flux de travail déclaratifs réutilisables créés dans SharePoint Designer 2010 dans un [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] projet SharePoint.|

## <a name="see-also"></a>Voir aussi

- [Développer des solutions SharePoint](../sharepoint/developing-sharepoint-solutions.md)
- [Générer et déboguer des solutions SharePoint](../sharepoint/building-and-debugging-sharepoint-solutions.md)
- [Créer des pages d’application pour SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md)