---
title: Personnaliser votre modèle avec des profils et des stéréotypes | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- UML model, profiles
- UML model, stereotypes
- UML model, customizing
ms.assetid: fd607157-0d3a-4583-a84e-427a4b2a5acb
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: b634b11418ef2d4220dc4eb07c825b514ab5494c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "74301196"
---
# <a name="customize-your-model-with-profiles-and-stereotypes"></a>Personnaliser votre modèle avec des profils et des stéréotypes
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Dans Visual Studio, vous pouvez adapter les éléments de modèle UML standard, tels que les classes et les composants, pour les personnaliser à des fins spécifiques. Vous pouvez appliquer un *stéréotype* à un élément de modèle qui peut modifier la liste des propriétés de l’élément. Les stéréotypes sont définis dans des collections appelées *profils*.

 Pour connaître les versions de Visual Studio qui prennent en charge cette fonctionnalité, consultez [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

 Pour utiliser un stéréotype, vous liez un package à un profil. Cela vous permet d'appliquer les stéréotypes définis dans le profil aux éléments du package. Certains profils sont installés avec Visual Studio. Vous pouvez par ailleurs définir vos propres profils.

 Les stéréotypes peuvent être définis dans la liste des propriétés d'un élément. Pour les principaux genres de formes sur un diagramme, les stéréotypes appliqués s'affichent également dans la forme, comme le montre cet exemple.

 ![Classe UML avec un stéréotype.](../modeling/media/uml-class-stereotype.png "UML_class_stereotype")

> [!NOTE]
> Si vous utilisez un profil pour créer un modèle et le partager avec un autre utilisateur, ce dernier ne pourra consulter les stéréotypes que s'il a installé le même profil sur son ordinateur.

## <a name="related-topics"></a>Rubriques connexes

|Intitulé|Description|
|-----------|-----------------|
|[Ajouter des stéréotypes à des éléments de modèle UML](../modeling/add-stereotypes-to-uml-model-elements.md)|Placement d'un élément de modèle dans un package, liaison du package à un profil et application d'un stéréotype à l'élément.|
|[Stéréotypes standard pour les modèles UML](../modeling/standard-stereotypes-for-uml-models.md)|Les profils standard UML L2 et L3 sont installés avec Visual Studio, et chaque modèle est lié à eux par défaut. Ils fournissent des stéréotypes que vous pouvez utiliser pour annoter vos modèles.<br /><br /> Par exemple, vous pouvez appliquer le stéréotype « spécification » à une classe pour indiquer qu'il vise uniquement à définir le comportement extérieurement visible de ses instances.|
|[Définir un profil pour étendre UML](../modeling/define-a-profile-to-extend-uml.md)|Vous pouvez définir vos propres stéréotypes et outils adaptés à votre zone d'application.<br /><br /> Par exemple, si vous développez un logiciel bancaire, vous pouvez définir un stéréotype « Compte » qui peut être appliqué aux classes. Vous pouvez ensuite utiliser des diagrammes de classes pour décrire les différents types de comptes et leurs relations.|
|[Installer un profil UML](../modeling/install-a-uml-profile.md)|Si quelqu'un vous a donné un profil UML, vous pouvez l'installer sur votre ordinateur.|
|[Définir un élément de boîte à outils de modélisation personnalisé](../modeling/define-a-custom-modeling-toolbox-item.md)|Un élément de boîte à outils personnalisé vous dispense de définir à plusieurs reprises un stéréotype sur les nouveaux éléments.|
