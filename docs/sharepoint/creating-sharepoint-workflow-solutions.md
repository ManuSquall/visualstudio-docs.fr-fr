---
title: "Création de Solutions de flux de travail SharePoint | Documents Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
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
ms.assetid: fe79b99a-cb7c-4a14-8d9f-bce0c0805ba0
caps.latest.revision: "23"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 256eaf2b451f91abdcc90c2beeedb7f689e95db6
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="creating-sharepoint-workflow-solutions"></a>Création de solutions de flux de travail SharePoint
  [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]Fournit des outils pour vous aider à créer des flux de travail personnalisés qui gèrent le cycle de vie des documents et des éléments de liste dans un site SharePoint Web. Les éléments fournis incluent un concepteur, un ensemble de contrôles de l’activité et les références d’assembly nécessaires. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]inclut également le **Assistant Personnalisation de SharePoint**, pour aider à créer et configurer les flux de travail.  
  
 Pour obtenir la liste des composants requis pour la création de projets SharePoint dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], consultez [configuration requise pour le développement de Solutions SharePoint](../sharepoint/requirements-for-developing-sharepoint-solutions.md). Pour plus d’informations sur SharePoint, consultez [Microsoft produits et Technologies SharePoint](http://go.microsoft.com/fwlink/?LinkId=178470).  
  
## <a name="workflows-in-sharepoint"></a>Flux de travail SharePoint  
 Lorsque vous ajoutez un flux de travail à une bibliothèque ou liste SharePoint, vous appliquez un processus d’entreprise sur tous les éléments dans la liste ou bibliothèque. Un flux de travail décrit les actions que le système ou les utilisateurs doivent effectuer sur chaque élément, telles que l’envoi de l’élément à modifier puis à réviser. Ces actions, appelées *activités*, sont les blocs de construction du flux de travail.  
  
 Vous pouvez créer des flux de travail SharePoint dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] et les déployer sur un site SharePoint Web. Une fois un flux de travail est déployé dans SharePoint, associez-la à une bibliothèque ou liste. Il peut ensuite être démarré automatiquement par un processus ou manuellement par un utilisateur. Pour plus d’informations sur l’opération de flux de travail, consultez [à l’aide de flux de travail pour gérer les processus](http://go.microsoft.com/fwlink/?LinkId=79757).  
  
## <a name="creating-custom-sharepoint-workflows"></a>Création de flux de travail SharePoint personnalisé  
 Deux projets de flux de travail SharePoint sont disponibles dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]: **Workflow séquentiel** et **Workflow d’ordinateur d’état**.  
  
 A *workflow séquentiel* représente une série d’étapes. Les étapes sont effectuées une après l’autre jusqu'à ce que la dernière activité est terminée. Flux de travail séquentiels est toujours strictement séquentielles dans leur exécution. Car ils peuvent recevoir des événements externes et inclure des flux logiques parallèles, l’ordre exact d’exécution peut varier. L’illustration suivante montre un exemple de workflow séquentiel.  
  
 ![Flux de travail séquentiel](../sharepoint/media/sp-sequential.png "Workflow séquentiel")  
  
 A *workflow d’ordinateur d’état* représente un ensemble d’états, les transitions et les actions. Les étapes d’un workflow de machine d’état exécutent de façon asynchrone. Cela signifie qu’ils ne sont pas nécessairement exécutées une après l’autre, mais elles sont déclenchées par des actions et des États. Un état qui est désigné comme l’état de démarrage, puis, en fonction d’un événement, une transition est faite à un autre état. L’ordinateur d’état peut avoir un état final qui détermine la fin du flux de travail. Le diagramme suivant montre un exemple d’un workflow de machine d’état.  
  
 ![Workflow d’ordinateur d’état](../sharepoint/media/sp-state.png "Workflow d’ordinateur d’état")  
  
 Pour plus d’informations sur les types de flux de travail, consultez [les Types de flux de travail](http://go.microsoft.com/fwlink/?LinkId=178995).  
  
### <a name="using-the-wizard"></a>À l’aide de l’Assistant  
 Lorsque vous créez un projet de flux de travail SharePoint dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], vous spécifiez tout d’abord ses paramètres dans le **Assistant Personnalisation de SharePoint**. L’Assistant utilise ces paramètres pour créer un projet dans **l’Explorateur de solutions**. Ce projet contient un fichier de code, plusieurs fichiers sont utilisés pour déployer le flux de travail et des références aux assemblys qui sont nécessaires pour créer un flux de travail SharePoint personnalisé.  
  
 Après avoir créé le flux de travail, vous pouvez modifier ses propriétés dans la fenêtre Propriétés. Bien que la plupart des propriétés de flux de travail peuvent être modifiés directement dans la fenêtre Propriétés, certains vous obliger à cliquer sur un bouton de sélection (![ellipse de concepteur ASP.NET Mobile](../sharepoint/media/mwellipsis.gif "ellipse de concepteur ASP.NET Mobile")) à modifier leurs valeurs. Ce bouton redémarre le **Assistant Personnalisation de SharePoint**. Après avoir apporté la propriété de valeur est modifiée, choisissez le **Terminer** bouton pour finaliser les.  
  
> [!NOTE]  
>  Le **Type de flux de travail** propriété est en lecture seule et ne peut pas être modifiée. Si vous souhaitez modifier le type de flux de travail, vous devez créer un autre workflow.  
  
## <a name="designing-a-sharepoint-workflow"></a>Conception d’un flux de travail SharePoint  
 Une fois que vous définissez toutes les étapes dans le processus d’entreprise, utilisez le [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] le Concepteur de flux de travail pour concevoir le flux de travail SharePoint. Pour ouvrir le concepteur, double-cliquez sur Workflow1.cs ou Workflow1.vb dans **l’Explorateur de solutions**, ou ouvrez le menu contextuel pour une de ces fichiers, puis choisissez **ouvrir**.  
  
### <a name="activities"></a>Activités  
 Pour concevoir un flux de travail, ajouter des activités à partir de la **boîte à outils** à un *planification de flux de travail* sur le concepteur. Une planification de flux de travail contient la séquence d’activités dans l’ordre qu’ils doivent être effectuées.  
  
 Il existe deux types d’activités :  
  
-   *Les activités simples* exécutent une seule unité de travail, tels que « délai de 1 jour » ou « démarrer le service Web ».  
  
-   *Les activités composites* contiennent d’autres activités ; par exemple, une activité conditionnelle peut contenir deux branches.  
  
 Les deux types d’activités sont disponibles dans le **boîte à outils**.  
  
 Activités peuvent avoir des propriétés, méthodes et événements. Utilisez le **propriétés** fenêtre pour définir les propriétés d’une activité.  
  
 Vous pouvez également créer une activité personnalisée. Pour plus d’informations, consultez [procédure pas à pas : création d’une activité de flux de travail de Site personnalisé](../sharepoint/walkthrough-create-a-custom-site-workflow-activity.md).  
  
 Les activités sont réparties dans les onglets suivants dans le **boîte à outils**:  
  
-   **Flux de travail SharePoint**  
  
-   **Windows Workflow v3.0**  
  
-   **Windows Workflow v3.5**  
  
 Pas toutes les activités de workflow de base sont pris en charge par SharePoint. Pour plus d’informations, consultez [vue d’ensemble des activités de flux de travail pour Windows SharePoint Services](http://go.microsoft.com/fwlink/?LinkID=156094).  
  
#### <a name="sharepoint-workflow-activities"></a>Activités de flux de travail SharePoint  
 Le **flux de travail SharePoint** onglets contiennent des activités spécialisées pour une utilisation dans [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)]. Ces activités simplifieront et rationalisent le développement de flux de travail cycle de vie du document. Pour plus d’informations sur les activités répertoriées dans le **flux de travail SharePoint** , consultez la rubrique [vue d’ensemble des activités de flux de travail pour Windows SharePoint Services](http://go.microsoft.com/fwlink/?LinkID=156094).  
  
#### <a name="windows-workflow-activities"></a>Activités de flux de travail Windows  
 Le **Windows Workflow** onglets contiennent les activités fournies par le [!INCLUDE[TLA#tla_workflow](../sharepoint/includes/tlasharptla-workflow-md.md)]. Vous pouvez utiliser ces activités pour créer des planifications de flux de travail pour tout type d’application de flux de travail Windows.  
  
 Pour plus d’informations sur les activités répertoriées dans le **flux de travail Windows** , consultez la rubrique [activités Windows Workflow Foundation](http://go.microsoft.com/fwlink/?LinkID=156096). Pour plus d’informations sur Windows Workflow Foundation, consultez [vue d’ensemble de Windows Workflow Foundation](http://go.microsoft.com/fwlink/?LinkID=128632).  
  
### <a name="working-with-activities-in-the-designer"></a>Gestion des activités dans le Concepteur  
 Votre planification de flux de travail peut contenir une combinaison des activités Windows Workflow et des activités de flux de travail SharePoint.  
  
 Le concepteur affiche des signaux visuels pour vous aider à positionner et configurer correctement des activités. Lorsque vous faites glisser ou copiez une activité sur la planification de flux de travail, le concepteur affiche des icônes de vert signe plus (+) qui affichent des emplacements valides pour cette activité dans le flux de travail. Vous ne pouvez pas positionner une activité dans un emplacement où il ne serait pas valide. Par exemple, vous ne peut pas positionner d’activité envoyer comme première activité dans une branche d’activité d’écoute. Pour plus d’informations, consultez [centre de développement SharePoint](http://go.microsoft.com/fwlink/?LinkId=178476).  
  
## <a name="collecting-information-during-the-workflow"></a>Collecte des informations pendant le flux de travail  
 Vous pouvez souhaiter recueillir des informations à partir des utilisateurs à des moments prédéfinis dans le flux de travail. Vous pouvez collecter des informations à l’aide des formulaires ou des propriétés de l’élément.  
  
### <a name="forms"></a>Formulaires  
 Les formulaires sont comme des boîtes de dialogue qui contiennent des questions et permettent aux utilisateurs de fournir des réponses.  
  
 Il existe quatre types de formulaires qui peuvent être utilisés dans un flux de travail :  
  
-   Association  
  
-   Émission  
  
-   Modification  
  
-   Tâche  
  
 Parmi ceux-ci, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] inclut des modèles d’élément pour les formulaires d’association et d’initiation. Un exemple d’une *formulaire d’association* qui permet à l’administrateur de l’installation du flux de travail est entrer les paramètres liés au flux de travail, telles que la limite de dépense pour un workflow de dépenses. Un exemple d’une *formulaire d’initiation* est celle qui permet à l’utilisateur d’un workflow dépenses Entrez la quantité dévolu dans le flux de travail. Pour plus d’informations sur ces types de formulaires, consultez [projets et modèles d’élément de projet SharePoint](../sharepoint/sharepoint-project-and-project-item-templates.md).  
  
### <a name="item-properties"></a>Propriétés de l’élément  
 Vous pouvez également collecter des informations à partir des utilisateurs en utilisant les propriétés d’un élément dans la liste ou bibliothèque SharePoint. Le fichier de code principal (Workflow1.cs ou Workflow1.vb) déclare une instance de la classe Microsoft.SharePoint.Workflow.SPWorkflowActivationProperties.WorkflowProperties nommée `workflowProperties`. Utilisez le `workflowProperties` objet pour accéder aux propriétés de la bibliothèque ou dans le code. Pour obtenir un exemple, consultez [procédure pas à pas : création et débogage d’une Solution de flux de travail SharePoint](../sharepoint/walkthrough-creating-and-debugging-a-sharepoint-workflow-solution.md).  
  
## <a name="debugging-a-sharepoint-workflow-template"></a>Débogage d’un modèle de flux de travail SharePoint  
 Vous pouvez déboguer un projet de flux de travail SharePoint le même comme autre [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] projets Web. Lorsque vous démarrez le [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] débogueur, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] utilise les paramètres que vous spécifiez dans le **Assistant Personnalisation de SharePoint** pour ouvrir le site SharePoint Web approprié et associer automatiquement le modèle de flux de travail avec la bibliothèque appropriée ou la liste. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]attache également la [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] du débogueur pour le [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] processus nommé w3wp.exe.  
  
 Pour tester le flux de travail, vous devez démarrer manuellement. Pour plus d’informations, consultez la section « Débogage de Workflows » dans [débogage de Solutions SharePoint](../sharepoint/debugging-sharepoint-solutions.md). Pour plus d’informations sur [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] débogage de l’application Web, consultez [débogage d’Applications Web et le Script](/visualstudio/debugger/debugging-web-applications-and-script).  
  
## <a name="deploying-a-sharepoint-workflow-template"></a>Déploiement d’un modèle de flux de travail SharePoint  
 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]Déploiement des projets de flux de travail SharePoint comme autre [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] les projets SharePoint. Pour plus d’informations, consultez [empaquetage et déploiement de Solutions SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md).  
  
## <a name="importing-globally-reusable-workflows"></a>L’importation de flux de travail globalement réutilisables  
 Outre la création de flux de travail réutilisables spécifiques au site, SharePoint Designer vous permet de créer *globalement réutilisables*, qui sont des flux de travail qui peut être utilisé par n’importe quel site SharePoint. Le projet importer le flux de travail réutilisable dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] n’importe pas les flux de travail globalement réutilisables. Toutefois, vous pouvez utiliser SharePoint Designer pour convertir un flux de travail globalement réutilisable dans un flux de travail réutilisable, ou importer le flux de travail comme un flux de travail déclaratif non converti. Pour plus d’informations, consultez [l’importation d’éléments à partir d’un SharePoint Site existant](../sharepoint/importing-items-from-an-existing-sharepoint-site.md).  
  
## <a name="related-topics"></a>Rubriques connexes  
  
|Titre|Description|  
|-----------|-----------------|  
|[Procédure pas à pas : création et débogage d’une solution de flux de travail SharePoint](../sharepoint/walkthrough-creating-and-debugging-a-sharepoint-workflow-solution.md)|Montre comment créer et déboguer un simple [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] flux de travail.|  
|[Procédure pas à pas : création d’un flux de travail avec des formulaires d’association et d’initiation](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md)|Vous guide pas à pas pour la création d’un plus complètes [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] flux de travail est exécuté avec des formulaires d’Association et d’Initiation.|  
|[Procédure pas à pas : ajout d’une page d’application à un flux de travail](../sharepoint/walkthrough-add-an-application-page-to-a-workflow.md)|S’appuie sur la rubrique [procédure pas à pas : création d’un flux de travail avec l’Association et des formulaires d’Initiation](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md) en ajoutant une page d’application .aspx supplémentaire qui signale des données entrées dans le flux de travail.|  
|[Procédure pas à pas : création d’une activité de flux de travail de site personnalisée](../sharepoint/walkthrough-create-a-custom-site-workflow-activity.md)|Montre comment effectuer deux tâches principales : créer un flux de travail au niveau du site et créer une activité de flux de travail personnalisé.|  
|[Procédure pas à pas : importation d’un flux de travail réutilisable de SharePoint Designer dans Visual Studio](../sharepoint/walkthrough-import-a-sharepoint-designer-reusable-workflow-into-visual-studio.md)|Montre comment importer des flux de travail déclaratifs réutilisables créés dans SharePoint Designer 2010 dans un [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] projet SharePoint.|  
  
## <a name="see-also"></a>Voir aussi  
 [Développement de Solutions SharePoint](../sharepoint/developing-sharepoint-solutions.md)   
 [Génération et débogage de solutions SharePoint](../sharepoint/building-and-debugging-sharepoint-solutions.md)   
 [Création de pages d’application pour SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md)  
  
  