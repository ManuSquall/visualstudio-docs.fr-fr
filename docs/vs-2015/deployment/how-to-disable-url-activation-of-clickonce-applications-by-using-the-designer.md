---
title: 'Comment : désactiver l’activation d’URL des applications ClickOnce à l’aide du concepteur | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
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
caps.latest.revision: 18
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 27690ab275d0c7ef2a090fa8ef2e42887ae9daeb
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68153809"
---
# <a name="how-to-disable-url-activation-of-clickonce-applications-by-using-the-designer"></a>Comment : suspendre l'activation des URL des applications ClickOnce à l'aide du concepteur
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

En règle générale, une [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] application se lance automatiquement immédiatement après son installation à partir d’un serveur Web. Pour des raisons de sécurité, vous pouvez décider de désactiver ce comportement et demander aux utilisateurs de démarrer l’application à partir du menu **Démarrer** à la place. La procédure suivante décrit comment désactiver l'activation d'URL.  
  
 Cette technique peut être utilisée uniquement pour les applications [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] installées sur l'ordinateur de l'utilisateur à partir d'un serveur web. Il ne peut pas être utilisé pour les applications en ligne uniquement, qui peuvent être démarrées uniquement à l’aide de leur URL. Pour plus d’informations sur la différence entre les applications en ligne uniquement et les applications installées, consultez [choix d’une stratégie de déploiement ClickOnce](../deployment/choosing-a-clickonce-deployment-strategy.md).  
  
 Cette procédure utilise [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] . Vous pouvez également effectuer cette tâche à l’aide de l' [!INCLUDE[winsdklong](../includes/winsdklong-md.md)] . Pour plus d’informations, consultez [Comment : désactiver l’activation d’URL des applications ClickOnce](../deployment/how-to-disable-url-activation-of-clickonce-applications.md).  
  
## <a name="procedure"></a>Procédure  
  
#### <a name="to-disable-url-activation-for-your-application"></a>Pour désactiver l'activation d'URL pour votre application  
  
1. Cliquez avec le bouton droit sur le nom de votre projet dans **Explorateur de solutions**, puis cliquez sur **Propriétés**.  
  
2. Dans la page **Propriétés** , cliquez sur l’onglet **publier** .  
  
3. Cliquez sur **Options**.  
  
4. Cliquez sur **manifestes**.  
  
5. Cochez la case bloquer l' **activation de l’application via une URL**.  
  
6. Déployez votre application.  
  
## <a name="see-also"></a>Voir aussi  
 [Publication d’applications ClickOnce](../deployment/publishing-clickonce-applications.md)
