---
title: Vue d’ensemble du modèle de programmation de SharePoint les Extensions d’outils | Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Visual Studio, extending tools
- SharePoint development in Visual Studio, extensibility object models
- SharePoint development in Visual Studio, extending tools
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: e575ac4d73464ba216d98bbd126a0165fdc9a2a9
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53941938"
---
# <a name="overview-of-the-programming-model-of-sharepoint-tools-extensions"></a>Extensions d’outils de la vue d’ensemble du modèle de programmation de SharePoint
  Quand vous créez une extension pour les outils SharePoint dans Visual Studio, vous commencez par implémenter une ou plusieurs interfaces d’extensibilité qui sont exposées par ces outils. Dans la plupart des cas, vous utilisez également d'autres types fournis par les outils SharePoint pour implémenter des fonctionnalités dans votre extension. Dans certains scénarios, vous pouvez également utiliser des types dans d'autres modèles objet fournis par Visual Studio et SharePoint. Vous devez comprendre l’objectif de chacun de ces modèles objet et savez comment les utiliser avec eux pour créer des extensions pour les outils SharePoint.  

## <a name="extend-the-sharepoint-tools-by-implementing-extensibility-interfaces"></a>Étendre les outils SharePoint en implémentant des interfaces d’extensibilité
 Visual Studio utilise Managed Extensibility Framework (MEF) dans .NET Framework 4 pour fournir le modèle d'extensibilité pour les outils SharePoint. MEF est une API (implémentée dans l’assembly System.ComponentModel.Composition) qui permet aux applications d’exposer des points d’extensibilité et de découvrir et de charger des extensions au moment de l’exécution. Pour plus d’informations sur MEF, consultez [Managed Extensibility Framework &#40;MEF&#41;](/dotnet/framework/mef/index).  

 Pour étendre les outils SharePoint, implémentez une ou plusieurs interfaces d'extensibilité qui sont exposées par Visual Studio. Vous devez également appliquer l'attribut <xref:System.ComponentModel.Composition.ExportAttribute> et, si nécessaire, des attributs supplémentaires spécifiques aux outils SharePoint, à l'implémentation de votre interface. Le tableau suivant répertorie les interfaces que vous pouvez implémenter pour étendre les outils SharePoint.  

|Interface|Description|  
|---------------|-----------------|  
|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider>|Implémentez cette interface pour définir un nouveau type d'élément de projet SharePoint. Pour obtenir un exemple, consultez [Comment : Définir un type d’élément de projet SharePoint](../sharepoint/how-to-define-a-sharepoint-project-item-type.md).|  
|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension>|Implémentez cette interface pour étendre un type d'élément de projet SharePoint qui est déjà installé dans Visual Studio. Pour obtenir un exemple, consultez [Comment : Créer une extension d’élément de projet SharePoint](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md).|  
|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension>|Implémentez cette interface pour étendre des projets SharePoint. Pour obtenir un exemple, consultez [Comment : Créer une extension de projet SharePoint](../sharepoint/how-to-create-a-sharepoint-project-extension.md).|  
|<xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentStep>|Implémentez cette interface pour définir une nouvelle étape de déploiement qui peut être exécutée quand un élément de projet SharePoint est déployé ou retiré. Pour obtenir un exemple, consultez [procédure pas à pas : Créer une étape de déploiement personnalisée pour les projets SharePoint](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md).|  
|<xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension>|Implémentez cette interface pour étendre un nœud existant sous le **connexions SharePoint** nœud dans le **Explorateur de serveurs** fenêtre. Pour obtenir un exemple, consultez [Comment : Étendre un nœud SharePoint dans l’Explorateur de serveurs](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md).|  
|<xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeProvider>|Implémentez cette interface pour définir un nouveau type de nœud sous la **connexions SharePoint** nœud dans le **Explorateur de serveurs** fenêtre. Pour obtenir un exemple, consultez [Comment : Étendre un nœud SharePoint dans l’Explorateur de serveurs](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md).|  
|<xref:Microsoft.VisualStudio.SharePoint.Validation.IFeatureValidationRule>|Implémentez cette interface pour définir une règle de validation de fonctionnalité personnalisée. Pour obtenir un exemple, consultez [Comment : Créer des règles de validation pour les solutions SharePoint fonctionnalité personnalisée et un package](../sharepoint/how-to-create-custom-feature-and-package-validation-rules-for-sharepoint-solutions.md).|  
|<xref:Microsoft.VisualStudio.SharePoint.Validation.IPackageValidationRule>|Implémentez cette interface pour définir une règle de validation de package personnalisée. Pour obtenir un exemple, consultez [Comment : Créer des règles de validation pour les solutions SharePoint fonctionnalité personnalisée et un package](../sharepoint/how-to-create-custom-feature-and-package-validation-rules-for-sharepoint-solutions.md).|  

 Après avoir implémenté une extension des outils SharePoint, vous devez déployer l’assembly d’extension dans un package d’extension Visual Studio pour permettre à Visual Studio de découvrir et de charger l’extension. Pour plus d’informations, consultez [déployer des extensions pour les outils SharePoint dans Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).  

## <a name="understand-the-object-models-that-you-use-in-sharepoint-tools-extensions"></a>Comprendre les modèles d’objet que vous utilisez dans les extensions d’outils SharePoint
 Vous pouvez utiliser plusieurs modèles objet quand vous créez des extensions pour les outils SharePoint :  

-   *Modèle objet des outils SharePoint*. Ce modèle objet fournit les interfaces d'extensibilité que vous implémentez pour créer des extensions d'outils SharePoint et d'autres types connexes.  

-   *Visual Studio automation et intégration d’objet des modèles*. Utilisez ces modèles objet pour accéder aux fonctionnalités de Visual Studio qui dépassent le cadre du modèle objet des outils SharePoint.  

    > [!NOTE]  
    >  Vous pouvez convertir certains objets du modèle objet des outils SharePoint en objets des modèles objet d'intégration et d'automation Visual Studio et vice versa, en utilisant le service de projet SharePoint. Pour plus d’informations, consultez [effectuer des conversions entre types de système de projet SharePoint et d’autres types de projet Visual Studio](../sharepoint/converting-between-sharepoint-project-system-types-and-other-visual-studio-project-types.md).  

-   *Modèles d’objet serveur et client SharePoint*. Utilisez ces modèles objet pour modifier un site SharePoint ou pour extraire des données d’un site SharePoint à partir du contexte d’une extension des outils SharePoint.  

### <a name="sharepoint-tools-object-model"></a>Modèle objet des outils SharePoint
 Chaque extension des outils SharePoint utilise des types dans le modèle objet des outils SharePoint pour définir les fonctionnalités et le comportement principaux de l’extension. Les tableaux suivants décrivent les espaces de noms qui sont incluses dans ce modèle objet, à l’assemby qui les contient.

#### <a name="microsoftvisualstudiosharepointdll"></a>Microsoft.VisualStudio.SharePoint.dll    

|Espace de noms|Description|  
|-|-|  
|<xref:Microsoft.VisualStudio.SharePoint>|Contient des types qui vous permettent d'étendre et d'automatiser le système de projet SharePoint. Par exemple, vous pouvez étendre les éléments de projet et les projets SharePoint intégrés, ou vous pouvez créer vos propres éléments de projet. Pour plus d’informations, consultez [étendre le système de projet SharePoint](../sharepoint/extending-the-sharepoint-project-system.md).|  
|<xref:Microsoft.VisualStudio.SharePoint.Deployment>|Contient des types qui vous permettent d'étendre le processus de déploiement des projets SharePoint, comme la création de vos propres étapes et configurations de déploiement. Pour plus d’informations, consultez [SharePoint étendre empaquetage et déploiement](../sharepoint/extending-sharepoint-packaging-and-deployment.md).|  
|<xref:Microsoft.VisualStudio.SharePoint.Explorer>|Contient des types qui vous permettent d’étendre les nœuds sous le **connexions SharePoint** nœud dans le **Explorateur de serveurs** fenêtre, ou pour définir de nouveaux types de nœuds. Pour plus d’informations, consultez [étendre le nœud Connexions SharePoint dans l’Explorateur de serveurs](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md).|  
|<xref:Microsoft.VisualStudio.SharePoint.Features>|Contient des types qui vous permettent d’accéder aux définitions de fonctionnalité dans un projet SharePoint.|  
|<xref:Microsoft.VisualStudio.SharePoint.Packages>|Contient des types qui vous permettent d'accéder à la définition de package dans une solution SharePoint.|  
|<xref:Microsoft.VisualStudio.SharePoint.Validation>|Contient des types qui vous permettent de personnaliser le comportement de validation de fonctionnalité et de package pour les projets SharePoint. Pour plus d'informations, voir [Procédure : Créer des règles de validation pour les solutions SharePoint fonctionnalité personnalisée et un package](../sharepoint/how-to-create-custom-feature-and-package-validation-rules-for-sharepoint-solutions.md).| 

#### <a name="microsoftvisualstudiosharepointcommandsdll"></a>Microsoft.VisualStudio.SharePoint.Commands.dll

|Espace de noms|Description|  
|-|-|  
|<xref:Microsoft.VisualStudio.SharePoint.Commands>|Contient des types que vous pouvez utiliser pour créer des *commandes SharePoint*. Une commande SharePoint est une méthode qui appelle le modèle objet serveur SharePoint à partir d’une extension des outils SharePoint. Pour plus d’informations, consultez [appeler des modèles d’objet SharePoint](../sharepoint/calling-into-the-sharepoint-object-models.md).|

#### <a name="microsoftvisualstudiosharepointexplorerextensionsdll"></a>Microsoft.VisualStudio.SharePoint.Explorer.Extensions.dll

|Espace de noms|Description|  
|-|-| 
|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions>|Contient des types que vous pouvez utiliser pour obtenir des informations sur intégrée **Explorateur de serveurs** nœuds qui représentent des composants individuels d’un site SharePoint, tel qu’un nœud qui représente une liste, un champ ou un type de contenu. Pour plus d’informations, consultez [étendre le nœud Connexions SharePoint dans l’Explorateur de serveurs](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md).|  

### <a name="visual-studio-automation-object-model"></a>Modèle d’objet automation Visual Studio
 Le modèle objet automation Visual Studio fournit des API que vous pouvez utiliser pour automatiser des projets Visual Studio et l'IDE. Utilisez le modèle objet Visual Studio pour effectuer des tâches relatives au projet qui ne sont pas spécifiques aux projets SharePoint, ou pour effectuer d'autres tâches d'automatisation générales dans Visual Studio. En règle générale, ce modèle objet est souvent utilisé dans les macros et les compléments Visual Studio, mais vous pouvez également l’utiliser dans les extensions des outils SharePoint.  

 La partie principale du modèle objet automation Visual Studio est définie dans le *EnvDTE.dll* assembly. Le *EnvDTE\\<version>.dll* assemblys fournissent des fonctionnalités supplémentaires qui a été introduite dans des versions spécifiques de Visual Studio. Ces assemblys sont inclus avec Visual Studio.  

 Pour plus d’informations sur le modèle objet automation, consultez [référence du Kit de développement logiciel Visual Studio](../extensibility/visual-studio-sdk-reference.md).  

### <a name="visual-studio-integration-object-model"></a>Modèle objet d’intégration Visual Studio
 Le modèle d’objet Intégration fournit des API que vous pouvez utiliser pour ajouter des fonctionnalités à Visual Studio en créant un *VSPackage*. Un package Visual Studio est un module qui étend l’IDE Visual Studio en fournissant des fonctionnalités personnalisées telles que les fenêtres Outil, les éditeurs, les concepteurs, les services et les projets.  

 Vous pouvez utiliser le modèle objet d'intégration si vous souhaitez ajouter une nouvelle fonctionnalité Visual Studio à utiliser avec les outils SharePoint intégrés. Par exemple, si vous créez un élément de projet SharePoint personnalisé qui représente une action personnalisée pour un site SharePoint, vous pouvez également créer un package Visual Studio qui implémente un concepteur pour l'action personnalisée. Vous pouvez associer le concepteur à l’action personnalisée en ajoutant un élément de menu contextuel à l’élément de projet qui représente l’action personnalisée dans **l’Explorateur de solutions**. Vous pouvez ouvrir votre concepteur en ouvrant le menu contextuel (soit en double-cliquant sur l’élément de projet d’action personnalisée ou en sélectionnant puis en choisissant le **MAJ**+**F10** clés), puis en choisissant **Open**.  

 Ce modèle objet est défini dans un jeu d'assemblys qui sont inclus dans le Kit de développement logiciel (SDK) Visual Studio. Voici quelques-uns des principaux assemblys dans ce modèle objet *Microsoft.VisualStudio.Shell.11.0.dll*, *Microsoft.VisualStudio.Shell.Interop.dll*, et  *Microsoft.VisualStudio.OLE.Interop.dll*.  

 Pour plus d’informations sur le modèle objet d’intégration, consultez [vue d’ensemble du modèle Automation](../extensibility/internals/automation-model-overview.md) et [référence du Kit de développement logiciel Visual Studio](../extensibility/visual-studio-sdk-reference.md).  

### <a name="sharepoint-object-models"></a>Modèles d’objet SharePoint
 Les extensions des outils SharePoint peuvent utiliser des API SharePoint pour modifier un site SharePoint ou pour extraire des données d’un site SharePoint. [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] et [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] fournissent deux modèles objet différents : un modèle objet serveur et un modèle objet client.  

 Vous pouvez utiliser des API dans les deux modèles objet dans une extension des outils SharePoint, mais chaque modèle objet présente ses propres avantages et inconvénients dans le contexte des extensions des outils SharePoint. Pour plus d’informations, consultez [appeler des modèles d’objet SharePoint](../sharepoint/calling-into-the-sharepoint-object-models.md).  

|Modèle objet|Description|  
|------------------|-----------------|  
|Modèle objet serveur|Le modèle objet serveur fournit l'accès à toutes les fonctionnalités que [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] et [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] exposent par programmation. Ce modèle objet est conçu pour être utilisé par les solutions SharePoint qui s'exécutent sur le serveur SharePoint. La majeure partie de ce modèle d’objet est définie dans le *Microsoft.SharePoint.dll* assembly. Pour plus d’informations sur le modèle objet serveur, consultez [à l’aide du modèle d’objet SharePoint Foundation côté serveur](http://go.microsoft.com/fwlink/?LinkId=177796).|  
|Modèle objet client|Le modèle objet client est un sous-ensemble du modèle objet serveur qui permet d'interagir avec des données SharePoint à partir d'un client ou serveur distant. Il est conçu pour réduire le nombre d’allers-retours qui doivent être exécutés pour effectuer des tâches courantes. La majeure partie du modèle objet client est définie dans le *Microsoft.SharePoint.Client.dll* et *Microsoft.SharePoint.Client.Runtime.dll* assemblys. Pour plus d’informations sur le modèle objet client, consultez [modèle objet Client managé](http://go.microsoft.com/fwlink/?LinkId=177797).|  

## <a name="see-also"></a>Voir aussi
 [Étendre les outils SharePoint dans Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md)   
 [Appeler des modèles d’objet SharePoint](../sharepoint/calling-into-the-sharepoint-object-models.md)   
 [Utiliser le service de projet SharePoint](../sharepoint/using-the-sharepoint-project-service.md)  
