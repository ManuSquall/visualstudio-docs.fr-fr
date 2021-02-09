---
title: Appel des modèles d’objet SharePoint | Microsoft Docs
description: Découvrez comment appeler les deux modèles d’objet différents que vous pouvez utiliser dans les extensions des outils SharePoint.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, client object model
- SharePoint development in Visual Studio, server object model
- SharePoint commands [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, extensibility features
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 14358b5cc84f63227fd5001731c261002a324492
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99928937"
---
# <a name="call-into-the-sharepoint-object-models"></a>Appeler les modèles d’objet SharePoint
  Lorsque vous créez des extensions pour les outils SharePoint dans Visual Studio, vous devrez peut-être appeler des API SharePoint pour effectuer certaines tâches. Par exemple, si vous créez une étape de déploiement personnalisée pour des projets SharePoint, vous devrez peut-être appeler des API SharePoint pour effectuer certaines des tâches de déploiement de solutions.

 [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] et [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] fournissent deux modèles d’objet différents que vous pouvez utiliser dans les extensions des outils SharePoint : un modèle d’objet serveur et un modèle objet client. Chaque modèle objet présente des avantages et des inconvénients dans le contexte des extensions d’outils SharePoint.

 Pour obtenir une vue d’ensemble des modèles objet SharePoint, consultez [vue d’ensemble du modèle de programmation des extensions d’outils SharePoint](../sharepoint/overview-of-the-programming-model-of-sharepoint-tools-extensions.md).

## <a name="use-the-client-object-model-in-extension-projects"></a>Utiliser le modèle d’objet client dans des projets d’extension
 Lorsque vous développez une extension pour les outils SharePoint, vous pouvez utiliser le modèle d’objet client de votre projet comme n’importe quel autre ensemble d’API gérées. Vous pouvez ajouter des références aux assemblys dans le modèle objet client à votre projet, et vous pouvez appeler des API dans le modèle objet client directement à partir de votre code.

 Toutefois, le modèle objet client présente deux inconvénients dans le contexte des extensions d’outils SharePoint :

- Le modèle d’objet client fournit uniquement un sous-ensemble du modèle d’objet serveur. Si vous devez utiliser des fonctionnalités SharePoint qui ne sont pas exposées dans le modèle objet client, vous devez utiliser le modèle d’objet serveur.

- Même si l’utilisation du modèle d’objet client dans les extensions des outils SharePoint doit fonctionner dans la plupart des cas, vous pouvez rencontrer des scénarios où les appels au modèle objet client ne fonctionnent pas comme prévu. Le modèle d’objet client est conçu pour être utilisé dans les applications clientes pour appeler des sites SharePoint sur un serveur ou une batterie de serveurs distant. Les outils SharePoint dans Visual Studio fonctionnent uniquement avec une installation SharePoint locale sur l’ordinateur de développement. Par conséquent, lorsque vous utilisez le modèle d’objet client dans une extension d’outils SharePoint, vous appelez un site SharePoint sur l’ordinateur local, ce qui n’est pas la manière dont le modèle d’objet client a été conçu pour être utilisé.

  Pour obtenir une procédure pas à pas qui montre comment utiliser le modèle d’objet client dans une extension des outils SharePoint dans Visual Studio, consultez [procédure pas à pas : appeler le modèle d’objet client SharePoint dans une extension de Explorateur de serveurs](../sharepoint/walkthrough-calling-into-the-sharepoint-client-object-model-in-a-server-explorer-extension.md).

## <a name="use-the-server-object-model-in-extension-projects"></a>Utiliser le modèle objet serveur dans les projets d’extension
 Le modèle objet serveur est un sur-ensemble du modèle objet client. Lorsque vous utilisez le modèle objet serveur, vous pouvez utiliser toutes les fonctionnalités de [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] et [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] exposer par programme.

 Les extensions des outils SharePoint peuvent utiliser des API dans le modèle objet serveur, mais elles ne peuvent pas appeler les API directement. Le modèle d’objet serveur ne peut être appelé qu’à partir d’un processus 64 bits qui cible le .NET Framework 3,5. Toutefois, les extensions d’outils SharePoint nécessitent le [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] et elles s’exécutent dans le processus Visual Studio 32 bits. Cela empêche les extensions des outils SharePoint de référencer directement les assemblys dans le modèle objet serveur SharePoint.

 Si vous souhaitez utiliser le modèle d’objet serveur dans une extension d’outils SharePoint, vous devez créer une *commande SharePoint* personnalisée pour appeler l’API. Vous définissez la commande SharePoint dans un assembly secondaire qui peut appeler directement le modèle d’objet serveur. Dans votre projet d’extension, vous appelez la commande SharePoint indirectement à l’aide de la méthode ExecuteCommand d’un <xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection> objet.

 Pour plus d’informations sur la création et l’utilisation de commandes SharePoint, consultez [procédure : créer une commande SharePoint](../sharepoint/how-to-create-a-sharepoint-command.md) et [procédure : exécuter une commande SharePoint](../sharepoint/how-to-execute-a-sharepoint-command.md). Pour plus d’informations sur le déploiement des commandes SharePoint, consultez [déployer des extensions pour les outils SharePoint dans Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).

 Pour obtenir des procédures pas à pas qui montrent comment créer et utiliser des commandes SharePoint, consultez [procédure pas à pas : créer une étape de déploiement personnalisée pour les projets SharePoint](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md) et [procédure pas à pas : étendre Explorateur de serveurs pour afficher des composants WebPart](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md).

### <a name="understand-how-sharepoint-commands-are-executed"></a>Comprendre comment les commandes SharePoint sont exécutées
 Les assemblys qui définissent les commandes SharePoint sont chargés dans un processus hôte 64 bits nommé *vssphost4.exe*. Après avoir appelé une commande SharePoint dans une extension d’outils SharePoint, la commande est exécutée par *vssphost4.exe* au lieu du processus Visual Studio 32 bits (*devenv.exe*). Vous pouvez contrôler certains aspects de la façon dont les commandes SharePoint sont exécutées en définissant des valeurs dans le registre. Pour plus d’informations, consultez [extensions de débogage pour les outils SharePoint dans Visual Studio](../sharepoint/debugging-extensions-for-the-sharepoint-tools-in-visual-studio.md).

## <a name="see-also"></a>Voir aussi
- [Comment : créer une commande SharePoint](../sharepoint/how-to-create-a-sharepoint-command.md)
- [Comment : exécuter une commande SharePoint](../sharepoint/how-to-execute-a-sharepoint-command.md)
- [Vue d’ensemble du modèle de programmation des extensions d’outils SharePoint](../sharepoint/overview-of-the-programming-model-of-sharepoint-tools-extensions.md)
