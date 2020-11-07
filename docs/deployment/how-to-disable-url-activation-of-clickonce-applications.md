---
title: Désactiver l’activation d’URL des applications ClickOnce
description: Découvrez comment désactiver le démarrage automatique lors de l’installation pour votre application ClickOnce, au cas où vous souhaiteriez que les utilisateurs démarrent l’application à partir du menu Démarrer.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- disallowUrlActivation
- URL activation, ClickOnce applications
- ClickOnce deployment, URL activation
ms.assetid: db31a16b-960f-4264-91d7-c7c40f876068
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 46e46278f5465de029aa9536744f51843397d743
ms.sourcegitcommit: 75bfdaab9a8b23a097c1e8538ed1cde404305974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2020
ms.locfileid: "94351230"
---
# <a name="how-to-disable-url-activation-of-clickonce-applications"></a>Guide pratique pour suspendre l’activation des URL des applications ClickOnce

En règle générale, une application [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] se lance automatiquement immédiatement après son installation à partir d'un serveur web. Pour des raisons de sécurité, vous pouvez décider de désactiver ce comportement et d’inviter plutôt les utilisateurs à lancer l’application à partir du menu **Démarrer**. La procédure suivante décrit comment désactiver l'activation d'URL.

Cette technique peut être utilisée uniquement pour les applications [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] installées sur l'ordinateur de l'utilisateur à partir d'un serveur web. Elle ne peut pas être utilisée pour les applications en ligne uniquement, qui peuvent être lancées uniquement à l'aide de leur URL. Pour plus d’informations sur la différence entre les applications en ligne uniquement et les applications installées, consultez [Choix d’une stratégie de déploiement ClickOnce](../deployment/choosing-a-clickonce-deployment-strategy.md).

Cette procédure utilise l’outil du kit de développement logiciel (SDK) Windows MageUI.exe. Pour plus d’informations sur cet outil, consultez [MageUI.exe (outil Manifest Generation and Editing, client graphique)](/dotnet/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client). Vous pouvez également effectuer cette procédure à l’aide de Visual Studio.

## <a name="procedure"></a>Procédure

### <a name="to-disable-url-activation-for-your-application"></a>Pour désactiver l'activation d'URL pour votre application

1. Ouvrez votre manifeste de déploiement dans MageUI.exe. Si vous n’en avez pas encore créé un, suivez les étapes de la [procédure pas à pas : déployer manuellement une application ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md).

2. Sélectionnez l’onglet **Options de déploiement**.

3. Décochez la case **Exécuter automatiquement l’application après l’installation**.

4. Enregistrez et signez le manifeste.

## <a name="see-also"></a>Voir aussi

- [Publier des applications ClickOnce](../deployment/publishing-clickonce-applications.md)