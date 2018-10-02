---
title: 'Comment : suspendre l’Activation des URL des Applications ClickOnce à l’aide du Concepteur | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-deployment
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- disallowURLActivation
- URL activation, ClickOnce applications
- ClickOnce deployment, URL activation
ms.assetid: a337a582-e67c-409a-b52e-607cd1a8fc57
caps.latest.revision: 18
author: mikejo5000
ms.author: mikejo
manager: wpickett
ms.openlocfilehash: 6cc5571dffba9daa3ac1f5f78e354487cbc654fe
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47502172"
---
# <a name="how-to-disable-url-activation-of-clickonce-applications-by-using-the-designer"></a>Comment : suspendre l'activation des URL des applications ClickOnce à l'aide du concepteur
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [Comment : désactiver URL d’Activation d’Applications ClickOnce à l’aide du concepteur](https://docs.microsoft.com/visualstudio/deployment/how-to-disable-url-activation-of-clickonce-applications-by-using-the-designer).  
  
En règle générale, un [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] application démarrera automatiquement immédiatement après son installation à partir d’un serveur Web. Pour des raisons de sécurité, vous pouvez décider de désactiver ce comportement et indiquer aux utilisateurs de démarrer l’application à partir de la **Démarrer** menu à la place. La procédure suivante décrit comment désactiver l'activation d'URL.  
  
 Cette technique peut être utilisée uniquement pour les applications [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] installées sur l'ordinateur de l'utilisateur à partir d'un serveur web. Il ne peut pas être utilisé pour les applications en ligne uniquement, ce qui peuvent être démarrées uniquement à l’aide de leur URL. Pour plus d’informations sur la différence entre les applications en ligne uniquement et sont installées, consultez [choix d’une stratégie de déploiement ClickOnce](../deployment/choosing-a-clickonce-deployment-strategy.md).  
  
 Cette procédure utilise [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Vous pouvez également effectuer cette tâche à l’aide de la [!INCLUDE[winsdklong](../includes/winsdklong-md.md)]. Pour plus d’informations, consultez [Comment : désactiver les URL d’Activation de ClickOnce Applications](../deployment/how-to-disable-url-activation-of-clickonce-applications.md).  
  
## <a name="procedure"></a>Procédure  
  
#### <a name="to-disable-url-activation-for-your-application"></a>Pour désactiver l'activation d'URL pour votre application  
  
1.  Cliquez sur le nom de votre projet dans **l’Explorateur de solutions**, puis cliquez sur **propriétés**.  
  
2.  Sur le **propriétés** , cliquez sur le **publier** onglet.  
  
3.  Cliquez sur **Options**.  
  
4.  Cliquez sur **manifestes**.  
  
5.  Activez la case à cocher intitulée **bloquer l’activation via une URL de l’application**.  
  
6.  Déployez votre application.  
  
## <a name="see-also"></a>Voir aussi  
 [Publication d’applications ClickOnce](../deployment/publishing-clickonce-applications.md)



