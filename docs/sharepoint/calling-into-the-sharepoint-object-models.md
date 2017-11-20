---
title: "Appel des modèles d’objet SharePoint | Documents Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, client object model
- SharePoint development in Visual Studio, server object model
- SharePoint commands [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, extensibility features
ms.assetid: 99934f9e-901e-464e-ac8c-22c6c86440f4
caps.latest.revision: "38"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 3bd3f81580af908d06fe7389c04a6559d14f1075
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="calling-into-the-sharepoint-object-models"></a>Appel des modèles d'objet SharePoint
  Lorsque vous créez des extensions pour les outils SharePoint dans Visual Studio, vous devrez appeler APIs SharePoint pour effectuer certaines tâches. Par exemple, si vous créez une étape de déploiement personnalisée pour les projets SharePoint, vous devez appeler APIs SharePoint pour effectuer certaines tâches pour déployer des solutions.  
  
 [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)]et [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] fournissent deux modèles objet différents que vous pouvez utiliser dans les extensions d’outils SharePoint : un modèle d’objet serveur et un modèle d’objet client. Chaque modèle objet présente les avantages et inconvénients dans le contexte d’extensions d’outils SharePoint.  
  
 Pour une vue d’ensemble des modèles d’objet SharePoint, consultez [vue d’ensemble de la programmation de modèle d’Extensions d’outils SharePoint](../sharepoint/overview-of-the-programming-model-of-sharepoint-tools-extensions.md).  
  
## <a name="using-the-client-object-model-in-extension-projects"></a>À l’aide du modèle d’objet Client dans les projets d’Extension  
 Lorsque vous développez une extension pour les outils SharePoint, vous pouvez utiliser le modèle objet client dans votre projet comme tout autre ensemble d’API managées. Vous pouvez ajouter des références aux assemblys dans le modèle objet client pour votre projet, et vous pouvez appeler des API dans le modèle objet client directement à partir de votre code.  
  
 Toutefois, le modèle objet client présente deux inconvénients dans le contexte d’extensions d’outils SharePoint :  
  
-   Le modèle objet client fournit uniquement un sous-ensemble du modèle d’objet serveur. Si vous devez utiliser les fonctionnalités de SharePoint qui ne sont pas exposée dans le modèle objet client, vous devez utiliser le modèle objet serveur.  
  
-   Bien qu’à l’aide du modèle d’objet client dans les extensions d’outils SharePoint doit fonctionner dans la plupart des cas, vous pouvez rencontrer certains scénarios où les appels au modèle d’objet client ne fonctionnent pas comme prévu. Le modèle objet client est conçu pour être utilisé dans les applications clientes pour appeler dans des sites SharePoint sur un serveur distant ou une batterie de serveurs. Les outils SharePoint dans Visual Studio fonctionnent uniquement avec une installation SharePoint locale sur l’ordinateur de développement. Par conséquent, lorsque vous utilisez le modèle objet client dans une extension des outils SharePoint, vous appelez à un site SharePoint sur l’ordinateur local, ce qui n’est pas la façon dont le modèle objet client a été conçu pour être utilisé.  
  
 Pour une procédure pas à pas qui montre comment utiliser le modèle objet client dans une extension des outils SharePoint dans Visual Studio, consultez [procédure pas à pas : appel dans le modèle d’objet Client SharePoint dans une Extension de l’Explorateur de serveurs](../sharepoint/walkthrough-calling-into-the-sharepoint-client-object-model-in-a-server-explorer-extension.md).  
  
## <a name="using-the-server-object-model-in-extension-projects"></a>À l’aide du modèle d’objet serveur dans les projets d’Extension  
 Le modèle objet serveur est un sur-ensemble du modèle d’objet client. Lorsque vous utilisez le modèle objet serveur, vous pouvez utiliser toutes les fonctionnalités qui [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] et [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] exposent par programmation.  
  
 Les extensions d’outils SharePoint peuvent utiliser des API dans le modèle objet serveur, mais ils ne peuvent pas appeler directement les API. Le modèle objet serveur peut être appelé uniquement à partir d’un processus 64 bits qui cible le .NET Framework 3.5. Toutefois, les extensions des outils SharePoint nécessitent le [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] et elles s’exécutent dans le processus de Visual Studio 32 bits. Cela empêche des extensions des outils SharePoint de référencer directement les assemblys dans le modèle d’objet serveur SharePoint.  
  
 Si vous souhaitez utiliser le modèle objet serveur dans une extension des outils SharePoint, vous devez créer une personnalisée *commande SharePoint* pour appeler l’API. Vous définissez la commande SharePoint dans un assembly secondaire peut appeler directement dans le modèle objet serveur. Dans votre projet d’extension, vous appelez la commande SharePoint indirectement à l’aide de la méthode ExecuteCommand d’un <xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection> objet.  
  
 Pour plus d’informations sur la création et à l’aide des commandes SharePoint, consultez [Comment : créer une commande SharePoint](../sharepoint/how-to-create-a-sharepoint-command.md) et [Comment : exécuter une commande SharePoint](../sharepoint/how-to-execute-a-sharepoint-command.md). Pour plus d’informations sur le déploiement des commandes SharePoint, consultez [déploiement d’Extensions pour les outils SharePoint dans Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).  
  
 Pour les procédures pas à pas qui montrent comment créer et utiliser les commandes SharePoint, consultez [procédure pas à pas : création d’une étape de déploiement personnalisée pour les projets SharePoint](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md) et [procédure pas à pas : extension de l’Explorateur de serveurs pour l’affichage Web Parties](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md).  
  
### <a name="understanding-how-sharepoint-commands-are-executed"></a>Comprendre comment les commandes SharePoint sont exécutées.  
 Les assemblys qui définissent des commandes SharePoint sont chargés dans un processus hôte 64 bits nommé vssphost4.exe. Après avoir appelé une commande SharePoint dans une extension des outils SharePoint, la commande est exécutée par vssphost4.exe, au lieu du processus de Visual Studio (devenv.exe) 32 bits. Vous pouvez contrôler certains aspects de l’exécution des commandes SharePoint en définissant des valeurs dans le Registre. Pour plus d’informations, consultez [débogage d’Extensions pour les outils SharePoint dans Visual Studio](../sharepoint/debugging-extensions-for-the-sharepoint-tools-in-visual-studio.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Comment : créer une commande SharePoint](../sharepoint/how-to-create-a-sharepoint-command.md)   
 [Comment : exécuter une commande SharePoint](../sharepoint/how-to-execute-a-sharepoint-command.md)   
 [Vue d’ensemble du modèle de programmation des extensions d’outils SharePoint](../sharepoint/overview-of-the-programming-model-of-sharepoint-tools-extensions.md)  
  
  