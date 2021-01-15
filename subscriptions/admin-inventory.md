---
title: Inventaire de pré-production dans l’abonnement Visual Studio | Visual Studio Marketplace
author: evanwindom
ms.author: v-evwin
manager: cabuschl
ms.assetid: 7d74e113-8fb2-490e-8502-48cce7b1327a
ms.date: 01/14/2021
ms.topic: conceptual
description: En savoir plus sur la responsabilité des administrateurs pour effectuer des inventaires de pré-production
ms.openlocfilehash: abcb3c8c1213885b5e543b05cf912c418acaa3f5
ms.sourcegitcommit: 4ee20054afe7bcf5c0aed504dec01e18059fbbd0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/15/2021
ms.locfileid: "98226485"
---
# <a name="inventory-of-pre-production-environment"></a>Inventaire de l’environnement de préproduction
Les abonnements Visual Studio simplifient la gestion des actifs en comptant les utilisateurs plutôt que les appareils.

Les administrateurs Visual Studio doivent attribuer des abonnements Visual Studio à **des personnes spécifiques nommées**. Les conventions de nommage telles que Dev1, Dev2 ou l’utilisation de noms d’équipes tels que « FeatureTeam » ne sont **pas autorisées**.

Voici plusieurs façons de simplifier l’inventaire de votre environnement de préproduction :
- Vérifiez vos attributions d’utilisateurs. Microsoft fournit un site web appelé [portail d’administration Visual Studio](https://manage.visualstudio.com/) pour vous aider à effectuer le suivi des attributions d’abonnements Visual Studio.
- Utilisez votre annuaire Active Directory local ou basé sur le cloud pour répertorier les utilisateurs. Si vous utilisez Active Directory pour gérer l’accès utilisateur, vous pouvez identifier les utilisateurs de développement et de test par leur appartenance à l’annuaire.
- Utilisez des outils automatisés pour faire un inventaire des systèmes. Vous devrez peut-être aussi utiliser un outil d’inventaire de logiciels pour vous aider à gérer vos licences logicielles et distinguer les environnements de préproduction des environnements de production. De nombreux clients disposant de Microsoft System Center créent des conventions de nommage pour vous aider à automatiser cette partie du processus d’inventaire.
- Obtenez de l’aide pour un rapprochement manuel. Inscrivez votre personnel pour faciliter le rapprochement de vos utilisateurs de développement et de test avec votre environnement de développement et de test.

> [!NOTE]
> Les logiciels des abonnements Visual Studio ne disposent pas d’une licence pour les environnements de production, dont tout environnement accessible par les utilisateurs finaux pour plus que des tests d’acceptation ou des commentaires, un environnement se connectant à une base de données de production, prenant en charge la récupération d’urgence ou la sauvegarde de production, ou un environnement utilisé pour la production pendant les pics d’activité. Des avantages spécifiques offerts par certains niveaux d’abonnement, décrits dans le [Livre blanc sur la gestion des licences Visual Studio](https://aka.ms/vslicensing), en sont une exception.  

## <a name="resources"></a>Ressources
- [Livre blanc sur la gestion des licences Visual Studio](https://visualstudio.microsoft.com/wp-content/uploads/2019/06/Visual-Studio-Licensing-Whitepaper-May-2019.pdf)
- [Prise en charge des abonnements et de l’administration de Visual Studio](https://visualstudio.microsoft.com/support/support-overview-vs)
- [Termes du contrat de licence en volume](https://www.microsoft.com/licensing/product-licensing/products.aspx)

## <a name="see-also"></a>Voir aussi
- [Documentation de Visual Studio](/visualstudio/)
- [Documentation Azure DevOps](/azure/devops/)
- [Documentation Azure](/azure/)
- [Documentation Microsoft 365](/microsoft-365/)

## <a name="next-steps"></a>Étapes suivantes
En savoir plus sur les responsabilités pour les administrateurs :
- [Responsabilités de l’administrateur](admin-responsibilities.md)
- [Gérer des grandes équipes et des prestataires externes](manage-teams.md)
- [Suivre les affectations d’utilisateurs et traiter les commandes](assignments-orders.md)
- Utiliser le rapport [Utilisation maximale](maximum-usage.md) pour suivre les engagements d’achat