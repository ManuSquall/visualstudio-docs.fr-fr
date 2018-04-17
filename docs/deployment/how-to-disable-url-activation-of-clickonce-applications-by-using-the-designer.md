---
title: 'Comment : désactiver l’Activation des URL des Applications ClickOnce à l’aide du Concepteur | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- disallowURLActivation
- URL activation, ClickOnce applications
- ClickOnce deployment, URL activation
ms.assetid: a337a582-e67c-409a-b52e-607cd1a8fc57
author: stevehoag
ms.author: shoag
manager: wpickett
ms.workload:
- multiple
ms.openlocfilehash: 0300b81a73deef2dabb89631f778d56ff89e820e
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-disable-url-activation-of-clickonce-applications-by-using-the-designer"></a>Comment : suspendre l'activation des URL des applications ClickOnce à l'aide du concepteur
En règle générale, un [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] application démarrera automatiquement immédiatement après son installation à partir d’un serveur Web. Pour des raisons de sécurité, vous pouvez décider de désactiver ce comportement et inviter les utilisateurs à démarrer l’application à partir de la **Démarrer** menu à la place. La procédure suivante décrit comment désactiver l'activation d'URL.  
  
 Cette technique peut être utilisée uniquement pour les applications [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] installées sur l'ordinateur de l'utilisateur à partir d'un serveur web. Il ne peut pas être utilisé pour les applications en ligne uniquement, ce qui peuvent être démarrées uniquement à l’aide de leur URL. Pour plus d’informations sur la différence entre les applications en ligne uniquement et installées, consultez [choix d’une stratégie de déploiement ClickOnce](../deployment/choosing-a-clickonce-deployment-strategy.md).  
  
 Cette procédure utilise [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Vous pouvez également accomplir cette tâche à l’aide de la [!INCLUDE[winsdklong](../deployment/includes/winsdklong_md.md)]. Pour plus d’informations, consultez [Comment : désactiver les URL d’Activation de ClickOnce Applications](../deployment/how-to-disable-url-activation-of-clickonce-applications.md).  
  
## <a name="procedure"></a>Procédure  
  
#### <a name="to-disable-url-activation-for-your-application"></a>Pour désactiver l'activation d'URL pour votre application  
  
1.  Cliquez sur le nom de votre projet dans **l’Explorateur de solutions**, puis cliquez sur **propriétés**.  
  
2.  Sur le **propriétés** , cliquez sur le **publier** onglet.  
  
3.  Cliquez sur **Options**.  
  
4.  Cliquez sur **manifestes**.  
  
5.  Activez la case à cocher **bloquer l’activation via une URL de l’application**.  
  
6.  Déployez votre application.  
  
## <a name="see-also"></a>Voir aussi  
 [Publication d’applications ClickOnce](../deployment/publishing-clickonce-applications.md)