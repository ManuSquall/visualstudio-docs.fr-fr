---
title: "How to: Create a SharePoint Command | Microsoft Docs"
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
  - "SharePoint commands [SharePoint development in Visual Studio], creating"
ms.assetid: e1fda8f0-eae1-4278-91c1-19a5e1fc327f
caps.latest.revision: 22
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 21
---
# How to: Create a SharePoint Command
  Si vous souhaitez appliquer le modèle d'objet serveur à une extension d'outils SharePoint, vous devez créer une *commande SharePoint* personnalisée pour appeler l'API.  Vous définissez la commande SharePoint dans un assembly capable d'appeler directement dans le modèle d'objet serveur.  
  
 Pour plus d'informations sur la finalité des commandes SharePoint, consultez [Calling into the SharePoint Object Models](../sharepoint/calling-into-the-sharepoint-object-models.md).  
  
### Pour créer une commande SharePoint  
  
1.  Créez un projet de bibliothèque de classes avec la configuration suivante :  
  
    -   Cible .NET Framework 3.5.  Pour plus d'informations sur le choix de la version cible du .NET Framework, consultez [Comment : cibler une version du .NET Framework](../Topic/How%20to:%20Target%20a%20Version%20of%20the%20.NET%20Framework.md).  
  
    -   Cible la plateforme AnyCPU ou x64.  Par défaut, la plateforme cible pour les projets de bibliothèque de classes est AnyCPU.  Pour plus d'informations sur le choix de la plateforme cible, consultez [NIB: How to: Optimize an Application for a Specific CPU Type](http://msdn.microsoft.com/fr-fr/294a75d2-4279-4b72-8298-2bea05be907a).  
  
    > [!NOTE]  
    >  Vous ne pouvez pas implémenter une commande SharePoint dans le même projet que celui définissant une extension d'outils SharePoint, car les commandes SharePoint ciblent .NET Framework 3.5 et les extensions d'outils SharePoint ciblent le [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)].  Vous devez définir toutes les commandes SharePoint utilisées par votre extension dans un projet séparé.  Pour plus d'informations, consultez [Deploying Extensions for the SharePoint Tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).  
  
2.  Ajoutez des références aux assemblys suivants :  
  
    -   Microsoft.VisualStudio.SharePoint.Commands  
  
    -   Microsoft.SharePoint  
  
3.  Dans une classe du projet, créez une méthode qui définit votre commande SharePoint.  La méthode doit respecter les instructions suivantes :  
  
    -   Elle peut avoir un ou deux paramètres.  
  
         Le premier paramètre doit être un objet <xref:Microsoft.VisualStudio.SharePoint.Commands.ISharePointCommandContext>.  Cet objet fournit le Microsoft.SharePoint.SPSite ou Microsoft.SharePoint.SPWeb dans lequel la commande est exécutée.  Il fournit également un objet <xref:Microsoft.VisualStudio.SharePoint.Commands.ISharePointCommandLogger> qui peut être utilisé pour écrire des messages dans la fenêtre **Sortie** ou la fenêtre **Liste d'erreurs** dans Visual Studio.  
  
         Le deuxième paramètre peut être un type de votre choix, mais ce paramètre est facultatif.  Vous pouvez ajouter ce paramètre à votre commande SharePoint si vous devez communiquer des données de votre extension d'outils SharePoint à la commande.  
  
    -   Une valeur de retour, facultative elle aussi, peut lui être associée.  
  
    -   Le deuxième paramètre et la valeur de retour doivent correspondre à un type susceptible d'être sérialisé par Windows Communication Foundation \(WCF\).  Pour plus d'informations, consultez [Types pris en charge par le sérialiseur de contrat de données](../Topic/Types%20Supported%20by%20the%20Data%20Contract%20Serializer.md) et [Utilisation de la classe XmlSerializer](../Topic/Using%20the%20XmlSerializer%20Class.md).  
  
    -   La méthode peut avoir n'importe quelle visibilité \(**public**, **internal** ou **private**\) et être statique ou non statique.  
  
4.  Appliquez l'<xref:Microsoft.VisualStudio.SharePoint.Commands.SharePointCommandAttribute> à la méthode.  Cet attribut spécifie un identificateur unique pour la commande, lequel ne correspond pas nécessairement au nom réel de la méthode.  
  
     Vous devez spécifier le même identificateur unique lorsque vous appelez la commande à partir de votre extension d'outils SharePoint.  Pour plus d'informations, consultez [How to: Execute a SharePoint Command](../sharepoint/how-to-execute-a-sharepoint-command.md).  
  
## Exemple  
 L'exemple de code suivant montre une commande SharePoint désignée par l'identificateur `Contoso.Commands.UpgradeSolution`.  Cette commande utilise des API dans le modèle objet serveur à mettre à niveau vers une solution déployée.  
  
 [!code-csharp[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#5](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectextension.upgradedeploymentstep/CS/SharePointCommands/Commands.cs#5)]
 [!code-vb[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#5](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectextension.upgradedeploymentstep/vb/sharepointcommands/commands.vb#5)]  
  
 Outre le premier paramètre <xref:Microsoft.VisualStudio.SharePoint.Commands.ISharePointCommandContext> implicite, cette commande a également un paramètre de chaîne personnalisé qui contient le chemin d'accès complet du fichier .wsp mis à niveau vers le site SharePoint.  Pour voir ce code dans le contexte d'une procédure pas à pas plus vaste, consultez [Walkthrough: Creating a Custom Deployment Step for SharePoint Projects](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md).  
  
## Compilation du code  
 Cet exemple nécessite des références aux assemblys suivants :  
  
-   Microsoft.VisualStudio.SharePoint.Commands  
  
-   Microsoft.SharePoint  
  
## Déploiement de la commande  
 Pour déployer la commande, incluez l'assembly de commande dans le même package d'extension [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] \(VSIX\) avec l'assembly d'extension qui utilise la commande.  Vous devez également ajouter une entrée pour l'assembly de commande dans le fichier extension.vsixmanifest.  Pour plus d'informations, consultez [Deploying Extensions for the SharePoint Tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).  
  
## Voir aussi  
 [Calling into the SharePoint Object Models](../sharepoint/calling-into-the-sharepoint-object-models.md)   
 [How to: Execute a SharePoint Command](../sharepoint/how-to-execute-a-sharepoint-command.md)   
 [Walkthrough: Extending Server Explorer to Display Web Parts](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)  
  
  