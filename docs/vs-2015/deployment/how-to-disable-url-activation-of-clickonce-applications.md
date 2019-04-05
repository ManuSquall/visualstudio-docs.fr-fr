---
title: 'Procédure : Désactiver l’Activation des URL des Applications ClickOnce | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- disallowUrlActivation
- URL activation, ClickOnce applications
- ClickOnce deployment, URL activation
ms.assetid: db31a16b-960f-4264-91d7-c7c40f876068
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: c22128d20bf83a8c6f2295b79653eabb3439c4b9
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58953094"
---
# <a name="how-to-disable-url-activation-of-clickonce-applications"></a>Procédure : Suspendre l’activation des URL des applications ClickOnce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

En règle générale, une application [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] se lance automatiquement immédiatement après son installation à partir d'un serveur web. Pour des raisons de sécurité, vous pouvez décider de désactiver ce comportement et d’inviter plutôt les utilisateurs à lancer l’application à partir du menu **Démarrer**. La procédure suivante décrit comment désactiver l'activation d'URL.  
  
 Cette technique peut être utilisée uniquement pour les applications [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] installées sur l'ordinateur de l'utilisateur à partir d'un serveur web. Elle ne peut pas être utilisée pour les applications en ligne uniquement, qui peuvent être lancées uniquement à l'aide de leur URL. Pour plus d’informations sur la différence entre les applications en ligne uniquement et les applications installées, consultez [Choix d’une stratégie de déploiement ClickOnce](../deployment/choosing-a-clickonce-deployment-strategy.md).  
  
 Cette procédure utilise l'outil du [!INCLUDE[winsdklong](../includes/winsdklong-md.md)] MageUI.exe. Pour plus d’informations sur cet outil, consultez [MageUI.exe (Manifest Generation and Editing Tool, Graphical Client)](http://msdn.microsoft.com/library/f9e130a6-8117-49c4-839c-c988f641dc14). Vous pouvez également effectuer cette procédure avec [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
## <a name="procedure"></a>Procédure  
  
#### <a name="to-disable-url-activation-for-your-application"></a>Pour désactiver l'activation d'URL pour votre application  
  
1.  Ouvrez votre manifeste de déploiement dans MageUI.exe. Si vous n’en n'avez pas encore créé un, suivez les étapes de [procédure pas à pas : déploiement manuel d’une application ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md).  
  
2.  Sélectionnez l’onglet **Options de déploiement**.  
  
3.  Décochez la case **Exécuter automatiquement l’application après l’installation**.  
  
4.  Enregistrez et signez le manifeste.  
  
## <a name="see-also"></a>Voir aussi  
 [Publication d’applications ClickOnce](../deployment/publishing-clickonce-applications.md)
