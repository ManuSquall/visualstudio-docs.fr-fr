---
title: 'Comment : suspendre l’Activation des URL des Applications ClickOnce à l’aide du Concepteur | Microsoft Docs'
ms.date: 11/04/2016
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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 46786b0a11c4be6614732a224b755542b637d662
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 02/21/2019
ms.locfileid: "56635447"
---
# <a name="how-to-disable-url-activation-of-clickonce-applications-by-using-the-designer"></a>Guide pratique pour suspendre l’activation des URL des applications ClickOnce à l’aide du concepteur
En règle générale, un [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] application démarrera automatiquement immédiatement après son installation à partir d’un serveur Web. Pour des raisons de sécurité, vous pouvez décider de désactiver ce comportement et indiquer aux utilisateurs de démarrer l’application à partir de la **Démarrer** menu à la place. La procédure suivante décrit comment désactiver l'activation d'URL.

 Cette technique peut être utilisée uniquement pour les applications [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] installées sur l'ordinateur de l'utilisateur à partir d'un serveur web. Il ne peut pas être utilisé pour les applications en ligne uniquement, ce qui peuvent être démarrées uniquement à l’aide de leur URL. Pour plus d’informations sur la différence entre les applications en ligne uniquement et sont installées, consultez [choix d’une stratégie de déploiement ClickOnce](../deployment/choosing-a-clickonce-deployment-strategy.md).

 Cette procédure utilise [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Vous pouvez également effectuer cette tâche à l’aide de la [!INCLUDE[winsdklong](../deployment/includes/winsdklong_md.md)]. Pour plus d’informations, consultez [Comment : désactiver les URL d’Activation de ClickOnce Applications](../deployment/how-to-disable-url-activation-of-clickonce-applications.md).

## <a name="procedure"></a>Procédure

#### <a name="to-disable-url-activation-for-your-application"></a>Pour désactiver l'activation d'URL pour votre application

1.  Cliquez sur le nom de votre projet dans **l’Explorateur de solutions**, puis cliquez sur **propriétés**.

2.  Sur le **propriétés** , cliquez sur le **publier** onglet.

3.  Cliquez sur **Options**.

4.  Cliquez sur **manifestes**.

5.  Activez la case à cocher intitulée **bloquer l’activation via une URL de l’application**.

6.  Déployez votre application.

## <a name="see-also"></a>Voir aussi
- [Publication d’applications ClickOnce](../deployment/publishing-clickonce-applications.md)