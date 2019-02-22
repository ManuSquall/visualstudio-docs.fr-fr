---
title: Appel des modèles d’objet SharePoint | Microsoft Docs
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 24634143a40f7b163c0b658bddb5596041868033
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/21/2019
ms.locfileid: "56595214"
---
# <a name="call-into-the-sharepoint-object-models"></a>Appeler des modèles d’objet SharePoint
  Lorsque vous créez des extensions pour les outils SharePoint dans Visual Studio, vous devrez peut-être appeler APIs SharePoint pour effectuer certaines tâches. Par exemple, si vous créez une étape de déploiement personnalisée pour les projets SharePoint, vous devez appeler APIs SharePoint pour effectuer certaines tâches pour déployer des solutions.

 [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] et [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] fournissent deux modèles d’objet que vous pouvez utiliser dans les extensions d’outils SharePoint : un modèle d’objet serveur et un modèle d’objet client. Chaque modèle objet présente des avantages et inconvénients dans le contexte d’extensions d’outils SharePoint.

 Pour une vue d’ensemble des modèles d’objet SharePoint, consultez [extensions d’outils de la vue d’ensemble du modèle de programmation de SharePoint](../sharepoint/overview-of-the-programming-model-of-sharepoint-tools-extensions.md).

## <a name="use-the-client-object-model-in-extension-projects"></a>Utiliser le modèle objet client dans les projets d’extension
 Lorsque vous développez une extension pour les outils SharePoint, vous pouvez utiliser le modèle objet client dans votre projet comme tout autre ensemble d’API managées. Vous pouvez ajouter des références aux assemblys dans le modèle objet client à votre projet, et vous pouvez appeler des API dans le modèle objet client directement à partir de votre code.

 Toutefois, le modèle objet client présente deux inconvénients dans le contexte d’extensions d’outils SharePoint :

- Le modèle objet client fournit uniquement un sous-ensemble du modèle d’objet serveur. Si vous devez utiliser les fonctionnalités de SharePoint ne sont pas exposée dans le modèle objet client, vous devez utiliser le modèle objet serveur.

- Bien qu’à l’aide du modèle objet client dans les extensions d’outils SharePoint doit fonctionner dans la plupart des cas, vous pouvez rencontrer certains scénarios où les appels au modèle objet client ne fonctionnent pas comme prévu. Le modèle objet client est conçu pour être utilisé dans les applications clientes pour appeler dans des sites SharePoint sur un serveur distant ou une batterie de serveurs. Les outils SharePoint dans Visual Studio fonctionnent uniquement avec une installation SharePoint locale sur l’ordinateur de développement. Par conséquent, lorsque vous utilisez le modèle objet client dans une extension des outils SharePoint, vous appelez dans un site SharePoint sur l’ordinateur local, ce qui n’est pas la façon dont le modèle objet client a été conçu pour être utilisé.

  Pour une procédure pas à pas qui montre comment utiliser le modèle objet client dans une extension des outils SharePoint dans Visual Studio, consultez [procédure pas à pas : Appeler le modèle d’objet client SharePoint dans une extension de l’Explorateur de serveurs](../sharepoint/walkthrough-calling-into-the-sharepoint-client-object-model-in-a-server-explorer-extension.md).

## <a name="use-the-server-object-model-in-extension-projects"></a>Utiliser le modèle objet serveur dans les projets d’extension
 Le modèle objet serveur est un sur-ensemble du modèle d’objet client. Lorsque vous utilisez le modèle objet serveur, vous pouvez utiliser toutes les fonctionnalités qui [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] et [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] exposent par programmation.

 Extensions d’outils SharePoint peuvent utiliser des API dans le modèle d’objet serveur, mais ils ne peuvent pas appeler directement les API. Le modèle objet serveur peut être appelé uniquement à partir d’un processus 64 bits qui cible le .NET Framework 3.5. Toutefois, les extensions d’outils SharePoint nécessitent le [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] et elles s’exécutent dans le processus de Visual Studio 32 bits. Cela empêche les extensions d’outils SharePoint de référencer les assemblys dans le modèle d’objet serveur SharePoint directement.

 Si vous souhaitez utiliser le modèle objet serveur dans une extension des outils SharePoint, vous devez créer un personnalisé *commande SharePoint* pour appeler l’API. Vous définissez la commande SharePoint dans un assembly secondaire peut appeler directement dans le modèle objet serveur. Dans votre projet d’extension, vous appelez la commande SharePoint indirectement à l’aide de la méthode ExecuteCommand d’un <xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection> objet.

 Pour plus d’informations sur la création et à l’aide des commandes SharePoint, consultez [Comment : Créer une commande SharePoint](../sharepoint/how-to-create-a-sharepoint-command.md) et [Comment : Exécuter une commande SharePoint](../sharepoint/how-to-execute-a-sharepoint-command.md). Pour plus d’informations sur le déploiement des commandes SharePoint, consultez [déployer des extensions pour les outils SharePoint dans Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).

 Pour les procédures pas à pas qui montrent comment créer et utiliser les commandes SharePoint, consultez [procédure pas à pas : Créer une étape de déploiement personnalisée pour les projets SharePoint](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md) et [procédure pas à pas : Étendre l’Explorateur de serveurs pour afficher des WebParts](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md).

### <a name="understand-how-sharepoint-commands-are-executed"></a>Comprendre l’exécution des commandes SharePoint
 Les assemblys qui définissent des commandes SharePoint sont chargés dans un processus hôte 64 bits nommé *vssphost4.exe*. Une fois que vous appelez une commande SharePoint dans une extension des outils SharePoint, la commande est exécutée par *vssphost4.exe* au lieu du processus de Visual Studio 32 bits (*devenv.exe*). Vous pouvez contrôler certains aspects de l’exécution des commandes SharePoint en définissant des valeurs dans le Registre. Pour plus d’informations, consultez [déboguer des extensions pour les outils SharePoint dans Visual Studio](../sharepoint/debugging-extensions-for-the-sharepoint-tools-in-visual-studio.md).

## <a name="see-also"></a>Voir aussi
- [Guide pratique pour Créer une commande SharePoint](../sharepoint/how-to-create-a-sharepoint-command.md)
- [Guide pratique pour Exécuter une commande SharePoint](../sharepoint/how-to-execute-a-sharepoint-command.md)
- [Extensions d’outils de la vue d’ensemble du modèle de programmation de SharePoint](../sharepoint/overview-of-the-programming-model-of-sharepoint-tools-extensions.md)
