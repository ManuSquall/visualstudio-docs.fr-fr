---
title: "Calling into the SharePoint Object Models"
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
  - "SharePoint development in Visual Studio, client object model"
  - "SharePoint development in Visual Studio, server object model"
  - "SharePoint commands [SharePoint development in Visual Studio]"
  - "SharePoint development in Visual Studio, extensibility features"
ms.assetid: 99934f9e-901e-464e-ac8c-22c6c86440f4
caps.latest.revision: 38
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 37
---
# Calling into the SharePoint Object Models
  Lorsque vous créez des extensions pour les outils sharepoint dans Visual Studio, vous devrez peut\-être appeler des API SharePoint pour effectuer certaines tâches.  Si vous définissez, par exemple, une étape de déploiement personnalisée pour les projets SharePoint, certaines des tâches de déploiement des solutions peuvent nécessiter des API Sharepoint.  
  
 [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] et [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] offrent deux modèles d'objet différent utilisables dans des extensions d'outils SharePoint : un modèle d'objet serveur et un modèle d'objet client.  Chaque modèle d'objet a ses propres avantages et inconvénients dans le contexte d'extensions d'outils SharePoint.  
  
 Pour obtenir une vue d'ensemble des modèles d'objet SharePoint, consultez [Overview of the Programming Model of SharePoint Tools Extensions](../sharepoint/overview-of-the-programming-model-of-sharepoint-tools-extensions.md).  
  
## Utilisation du modèle d'objet client dans les projets d'extension  
 Lorsque vous développez une extension pour les outils SharePoint, vous pouvez tirer parti du modèle d'objet client dans votre projet comme tout autre jeu d'API managées.  Vous être libre d'intégrer à votre projet des références aux assemblys du modèle d'objet client et de faire appel aux API du modèle d'objet client directement à partir de votre code.  
  
 Toutefois, le modèle d'objet client présente deux inconvénients dans le contexte des extensions d'outils SharePoint :  
  
-   Le modèle d'objet client fournit uniquement un sous\-ensemble du modèle d'objet serveur.  Si vous comptez exploiter des fonctionnalités SharePoint qui ne sont pas exposées dans le modèle d'objet client, vous devez alors recourir au modèle d'objet serveur.  
  
-   Même si l'utilisation du modèle d'objet client dans les extensions d'outils SharePoint ne pose pas de problème en principe, il arrive, dans certains scénarios, que les appels au modèle d'objet client ne donnent pas les résultats attendus.  Le modèle d'objet client est conçu pour procéder dans les applications clientes à des appels dans des sites SharePoint sur un serveur ou une batterie à distance.  Le fonctionnement des outils SharePoint dans Visual Studio est conditionné à une installation SharePoint locale sur l'ordinateur de développement.  Par conséquent, lorsque vous utilisez le modèle d'objet client dans une extension d'outils SharePoint, vous faites appel à un site SharePoint sur l'ordinateur local, ce qui n'est pas l'objectif d'utilisation du modèle d'objet client.  
  
 Pour une procédure pas \- à \- pas qui montre comment utiliser le modèle d'objet client dans une extension d'outils sharepoint dans Visual Studio, consultez [Walkthrough: Calling into the SharePoint Client Object Model in a Server Explorer Extension](../sharepoint/walkthrough-calling-into-the-sharepoint-client-object-model-in-a-server-explorer-extension.md).  
  
## Utilisation du modèle d'objet serveur dans les projets d'extension  
 Le modèle d'objet serveur est un sur\-ensemble du modèle d'objet client.  Lorsque vous utilisez le modèle d'objet serveur, vous pouvez profiter de toutes les fonctionnalités exposées par programmation par [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] et [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)].  
  
 Les extensions d'outils SharePoint peuvent tirer parti des API dans le modèle d'objet serveur, sans pour autant faire appel directement aux API.  Le modèle d'objet serveur peut être appelé uniquement à partir d'un processus 64 bits qui cible .NET Framework 3.5.  Toutefois, les extensions d'outils SharePoint ont besoin du [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] et s'exécutent dans le cadre du processus Visual Studio 32 bits.  Cela empêche des extensions d'outils SharePoint de référencer directement les assemblys dans le modèle d'objet serveur SharePoint.  
  
 Si vous souhaitez appliquer le modèle d'objet serveur à une extension d'outils SharePoint, vous devez créer une *commande SharePoint* personnalisée pour appeler l'API.  Vous définissez la commande SharePoint dans un assembly secondaire capable d'appeler directement dans le modèle d'objet serveur.  Dans votre projet d'extension, vous appelez indirectement la commande SharePoint à l'aide de la méthode ExecuteCommand d'un objet <xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection>.  
  
 Pour plus d'informations sur la création et l'utilisation de commandes SharePoint, consultez [How to: Create a SharePoint Command](../sharepoint/how-to-create-a-sharepoint-command.md) et [How to: Execute a SharePoint Command](../sharepoint/how-to-execute-a-sharepoint-command.md).  Pour plus d'informations sur le déploiement de commandes SharePoint, consultez [Deploying Extensions for the SharePoint Tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).  
  
 Pour apprendre à créer et à utiliser les commandes SharePoint, consultez [Walkthrough: Creating a Custom Deployment Step for SharePoint Projects](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md) et [Walkthrough: Extending Server Explorer to Display Web Parts](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md).  
  
### Présentation du mode d'exécution des commandes SharePoint  
 Les assemblys qui définissent des commandes SharePoint sont chargés dans un processus hôte 64 bits nommé vssphost4.exe.  Une fois que vous avez appelé une commande SharePoint dans une extension d'outils SharePoint, la commande est exécutée par vssphost4.exe, au lieu du processus Visual Studio 32 bits \(devenv.exe\).  Vous pouvez contrôler certains aspects de l'exécution des commandes SharePoint en définissant des valeurs dans le Registre.  Pour plus d'informations, consultez [Debugging Extensions for the SharePoint Tools in Visual Studio](../sharepoint/debugging-extensions-for-the-sharepoint-tools-in-visual-studio.md).  
  
## Voir aussi  
 [How to: Create a SharePoint Command](../sharepoint/how-to-create-a-sharepoint-command.md)   
 [How to: Execute a SharePoint Command](../sharepoint/how-to-execute-a-sharepoint-command.md)   
 [Overview of the Programming Model of SharePoint Tools Extensions](../sharepoint/overview-of-the-programming-model-of-sharepoint-tools-extensions.md)  
  
  