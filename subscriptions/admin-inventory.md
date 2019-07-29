---
title: Inventaire des environnements de préproduction | Visual Studio Marketplace
author: evanwindom
ms.author: lank
manager: lank
ms.date: 07/23/2019
ms.topic: conceptual
description: Découvrir en quoi consiste la responsabilité des administrateurs pour l’exécution des inventaires de préproduction
ms.openlocfilehash: d400e216d81601583dc08f66f1a6a185cbe41b91
ms.sourcegitcommit: 59e5758036223ee866f3de5e3c0ab2b6dbae97b6
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/23/2019
ms.locfileid: "68420550"
---
# <a name="inventory-of-pre-production-environment"></a>Inventaire de l’environnement de préproduction
Les abonnements Visual Studio simplifient la gestion des actifs en comptant les utilisateurs plutôt que les appareils.

Les administrateurs Visual Studio doivent attribuer les abonnements Visual Studio à des **personnes spécifiques nommées**. Les conventions de nommage telles que Dev1, Dev2 ou l’utilisation de noms d’équipes tels que « FeatureTeam » ne sont **pas autorisées**.

Voici plusieurs façons de simplifier l’inventaire de votre environnement de préproduction :
- Vérifiez vos attributions d’utilisateurs. Microsoft fournit un site web appelé [portail d’administration Visual Studio](https://manage.visualstudio.com/) pour vous aider à effectuer le suivi des attributions d’abonnements Visual Studio.
- Utilisez votre annuaire Active Directory local ou basé sur le cloud pour répertorier les utilisateurs. Si vous utilisez Active Directory pour gérer l’accès utilisateur, vous pouvez identifier les utilisateurs de développement et de test par leur appartenance à l’annuaire.
- Utilisez des outils automatisés pour faire un inventaire des systèmes. Vous devrez peut-être aussi utiliser un outil d’inventaire de logiciels pour vous aider à gérer vos licences logicielles et distinguer les environnements de préproduction des environnements de production. De nombreux clients disposant de Microsoft System Center créent des conventions de nommage pour vous aider à automatiser cette partie du processus d’inventaire.
- Obtenez de l’aide pour un rapprochement manuel. Inscrivez votre personnel pour faciliter le rapprochement de vos utilisateurs de développement et de test avec votre environnement de développement et de test.

## <a name="resources"></a>Ressources
- [Livre blanc sur la gestion des licences Visual Studio](https://aka.ms/vslicensing)
- [Prise en charge des abonnements et de l’administration de Visual Studio](https://visualstudio.microsoft.com/support/support-overview-vs)
- [Conditions du programme de licence en volume](https://www.microsoft.com/licensing/product-licensing/products.aspx)

## <a name="next-steps"></a>Étapes suivantes
En savoir plus sur les responsabilités des administrateurs :
- [Responsabilités de l’administrateur](admin-responsibilities.md)
- [Gérer de grandes équipes et des fournisseurs externes](manage-teams.md)
- [Suivre les affectations d’utilisateurs et traiter les commandes](assignments-orders.md)
- Utiliser le rapport [Utilisation maximale](maximum-usage.md) pour suivre les engagements d’achat