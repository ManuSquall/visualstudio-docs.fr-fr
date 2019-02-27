---
title: Responsabilités des administrateurs | Visual Studio Marketplace
author: evanwindom
ms.author: jaunger
manager: evelynp
ms.date: 03/13/2018
ms.topic: conceptual
description: Découvrez les responsabilités des administrateurs des abonnements.
searchscope: VS Subscription
ms.openlocfilehash: ca1dc2dd7a2232a85a7e6aefece63272bb0039fc
ms.sourcegitcommit: 23feea519c47e77b5685fec86c4bbd00d22054e3
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/26/2019
ms.locfileid: "56842349"
---
# <a name="overview-of-administrator-responsibilities"></a>Vue d’ensemble des responsabilités des administrateurs
En tant qu’administrateur, vous avez la possibilité de gérer les abonnements pour votre organisation.  Le rôle d’administrateur a également la responsabilité de vérifier que les abonnements sont gérés conformément aux termes du contrat de licence. Cet article présente les responsabilités, les avantages et les limitations du rôle d’administrateur.

## <a name="roles--responsibilities"></a>Rôles et responsabilités
Quatre principales responsabilités incombent à un administrateur Visual Studio :
1.  **Comprendre les avantages et restrictions des abonnements Visual Studio.** Bien comprendre vos avantages peut vous permettre de réduire les coûts en terme de matériel par l’utilisation des services cloud, et de réduire les coûts en termes de logiciels avec des licences par utilisateur pour les environnements de préproduction.
2.  **Attribuer des abonnements Visual Studio à des personnes spécifiques nommées et encourager leur utilisation.** Votre contrat exige que les abonnements Visual Studio soient attribués à des personnes spécifiques nommées. Vérifiez auprès des personnes auxquelles un abonnement a été attribué qu’elles accèdent aux avantages inclus dans leur abonnement Visual Studio et qu’elles en exploitent tout le potentiel.
3.  **Faire un inventaire précis de votre environnement de préproduction.** Cette opération est essentielle pour garantir que tous les utilisateurs qui interagissent avec des logiciels sous licence Visual Studio disposent des licences appropriées avec leur propre abonnement Visual Studio.
4.  **Effectuer le suivi des changements d’attributions d’utilisateurs et acquérir des licences supplémentaires dans les délais.** Les contrats de licence en volume Microsoft et MPSA vous donnent toute la souplesse nécessaire pour utiliser et attribuer des abonnements Visual Studio. En retour, vous êtes censé effectuer le suivi des changements apportés à l’utilisation des logiciels et des attributions d’utilisateurs, et traiter les commandes de licences supplémentaires selon la planification indiquée dans le contrat.

## <a name="benefits-and-limitations"></a>Avantages et limitations
Les abonnements Visual Studio permettent aux membres de l’équipe de développement d’installer et d’utiliser des logiciels pour concevoir, développer, tester, évaluer et présenter d’autres logiciels. Les logiciels des abonnements Visual Studio ne sont pas concédés sous licence pour les environnements de production.

|                                          |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
|------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Licences utilisateur                     | Les plateformes MSDN et tous les niveaux des abonnements Visual Studio sont concédés avec des licences par utilisateur. Chaque membre de l’équipe de développement qui va interagir (installer, configurer ou accéder) avec les logiciels inclus avec ces produits et services doit disposer de son propre abonnement Visual Studio.                                                                                                                                                                                                                                                                                                                                  |
| Installations illimitées                  | Chaque utilisateur titulaire d’une licence peut installer et utiliser les logiciels sur un nombre illimité d’appareils pour concevoir, développer, tester, évaluer et présenter des logiciels. Microsoft Office, qui est concédé sous licence pour un seul ordinateur de bureau, fait exception. Les logiciels sous licence Visual Studio peuvent être installés et utilisés au bureau, à domicile, dans des établissements scolaires et sur des appareils se trouvant dans les bureaux d’un client ou sur du matériel dédié hébergé par un tiers.                                                                                                                                                                                                                                  |
| Non destinés aux environnements de production | Les logiciels des abonnements Visual Studio ne disposent pas d’une licence pour les environnements de production, dont tout environnement accessible par les utilisateurs finaux pour plus que des tests d’acceptation ou des commentaires, un environnement se connectant à une base de données de production, prenant en charge la récupération d’urgence ou la sauvegarde de production, ou un environnement utilisé pour la production pendant les pics d’activité. Des avantages spécifiques offerts par certains niveaux d’abonnement, décrits dans le [Livre blanc sur la gestion des licences Visual Studio](https://aka.ms/vslicensing), en sont une exception.                                                                                            |
| Réattribution de licences                     | Quand un utilisateur quitte une équipe et ne nécessite plus de licence, vous pouvez réattribuer la licence passé un délai de 90 jours. Quand vous réattribuez une licence, toutes les clés de produit qui ont déjà été utilisées restent disponibles, mais elles ne seront pas remplacées. Pour les organisations qui ont des contrats Entreprise, les avantages qui ont été utilisés par l’utilisateur initial, comme une formation Pluralsight, seront réinitialisés.                                                                                                                                                                                                                                                 |
| Exception pour les utilisateurs finaux                  | À la fin d’un projet de développement de logiciel, les utilisateurs finaux vérifient généralement une application et déterminent si elle répond aux critères exigés pour la mise en production. Ce processus est appelé « test d’acceptation utilisateur (UAT) ». Les membres d’équipe, tels qu’un commanditaire ou un chef de produit, peuvent jouer le rôle de proxy pour les utilisateurs finaux. Les utilisateurs finaux qui ne disposent pas d’un abonnement Visual Studio peuvent accéder aux logiciels pour le test UAT à condition que l’utilisation des logiciels soit conforme à tous les termes du contrat de licence Visual Studio. Il est rare qu’un utilisateur dont le rôle principal est de concevoir, de développer ou de tester le logiciel soit également considéré comme un « utilisateur final ». |

## <a name="inventory-of-pre-production-environment"></a>Inventaire de l’environnement de préproduction
Les abonnements Visual Studio simplifient la gestion des actifs en comptant les utilisateurs plutôt que les appareils.

Les administrateurs Visual Studio doivent attribuer les abonnements Visual Studio à des **personnes spécifiques nommées**. Les conventions de nommage telles que Dev1, Dev2 ou Dev3, ne sont **pas autorisées**.

Voici plusieurs façons de simplifier l’inventaire de votre environnement de préproduction :
- Vérifiez vos attributions d’utilisateurs. Microsoft fournit un site web appelé [portail d’administration Visual Studio](https://manage.visualstudio.com/) pour vous aider à effectuer le suivi des attributions d’abonnements Visual Studio.
- Utilisez votre annuaire Active Directory local ou basé sur le cloud pour répertorier les utilisateurs. Si vous utilisez Active Directory pour gérer l’accès utilisateur, vous pouvez identifier les utilisateurs de développement et de test par leur appartenance à l’annuaire.
- Utilisez des outils automatisés pour faire un inventaire des systèmes. Vous devrez peut-être aussi utiliser un outil d’inventaire de logiciels pour vous aider à gérer vos licences logicielles et distinguer les environnements de préproduction des environnements de production. De nombreux clients disposant de Microsoft System Center créent des conventions de nommage pour vous aider à automatiser cette partie du processus d’inventaire.
- Obtenez de l’aide pour un rapprochement manuel. Inscrivez votre personnel pour faciliter le rapprochement de vos utilisateurs de développement et de test avec votre environnement de développement et de test.

## <a name="large-teams-and-external-contractors"></a>Grandes équipes et prestataires externes
Les administrateurs d’abonnements Visual Studio sont chargés de garantir que chaque utilisateur qui interagit avec les logiciels sous licence Visual Studio dispose des licences appropriées avec son propre abonnement Visual Studio.

### <a name="internal-teams"></a>Équipes internes
En général, les organisations logicielles modernes incluent des parties prenantes issues de plusieurs groupes. Identifiez les contacts de chaque groupe qui peuvent vous aider à effectuer le suivi de l’inventaire des utilisateurs et des modifications.
Chaque organisation est différente, mais voici une liste type des équipes impliquées dans le développement :
- Équipes d’ingénierie logicielle.
- Équipes commerciales, qui incluent les directeurs de produit et les analystes d’entreprise.
- Équipes de gestion de projet.
- Équipes qualité, qui incluent le personnel de l’assurance qualité et les testeurs manuels.
- Personnel des opérations informatiques, qui inclut les gestionnaires d’infrastructure de préproduction et de laboratoire.

### <a name="external-contractors-and-partners"></a>Partenaires et prestataires externes
Les prestataires externes peuvent apporter des licences pour prendre part à votre environnement sous licence Visual Studio. Les partenaires Microsoft Certified Partner peuvent recevoir quelques abonnements Visual Studio gratuits pour un usage interne. Toutefois, ces abonnements n’englobent pas les activités génératrices de revenus telles que le développement de logiciels personnalisés pour un client. Demandez aux partenaires de vous envoyer une lettre décrivant les licences qu’ils fournissent et celles qu’ils vous demandent de fournir.

## <a name="track-user-assignment-and-process-orders"></a>Effectuer le suivi de l’attribution des utilisateurs et traiter les commandes
Les administrateurs d’abonnements Visual Studio sont censés effectuer le suivi de l’utilisation de Visual Studio et traiter les commandes de toute augmentation d’utilisation selon la planification indiquée dans leur contrat de licence en volume ou dans leur Contrat de Fourniture de Produits et de Services Microsoft. Le nouveau portail d’administration des abonnements Visual Studio facilite cette opération grâce à un dispositif de suivi utile qui affiche vos licences disponibles et utilisées.

### <a name="high-water-mark-of-usage"></a>Limite supérieure d’utilisation
**L’obligation de votre société d’acheter des abonnements Visual Studio prend effet immédiatement dans les cas suivants :**
- Une licence est attribuée à un utilisateur.
- Un utilisateur interagit avec le logiciel Visual Studio.

Votre obligation d’effectuer l’achat est déterminée par la **limite supérieure d’utilisation**. Cette limite est le point culminant en attributions d’utilisateurs par jour ou en utilisateurs qui interagissent avec le logiciel Visual Studio, la valeur la plus élevée l’emportant.
1.  Les administrateurs d’abonnements Visual Studio peuvent augmenter la limite supérieure d’utilisation en attribuant des abonnements Visual Studio à des personnes individuelles.
2.  Les administrateurs d’abonnements Visual Studio peuvent réattribuer des abonnements d’un abonné à un autre si 90 jours se sont écoulés depuis l’attribution initiale. Pour éviter une limite artificielle, effectuez toujours cette opération en supprimant tout d’abord l’abonnement existant, puis en ajoutant le nouveau.
3.  Les administrateurs d’abonnements Visual Studio peuvent modifier le niveau d’abonnement attribué pour une personne, ce qui constituerait une diminution dans une attribution et une augmentation dans une autre. Quand vous réduisez le niveau d’abonnement attribué d’un abonné, la personne doit immédiatement cesser d’utiliser tout ce qui se trouve uniquement dans l’abonnement de niveau supérieur et le désinstaller.

### <a name="cloud-subscriptions-open-license-or-open-value"></a>Abonnements cloud, Licence open ou Open Value
Vous pouvez attribuer des abonnements via un programme comme Abonnements Microsoft cloud, Licence open ou Open Value. Dans ce cas, vous devez traiter votre commande d’utilisateurs supplémentaires au cours du mois où les utilisateurs (employés ou prestataires externes) commencent à interagir avec les logiciels sous licence Visual Studio.

### <a name="enterprise-mpsa-and-select-agreements"></a>Contrats Entreprise, MPSA et Select
Les contrats Entreprise (EA), MPSA et Select Plus Microsoft vous donnent toute la souplesse nécessaire pour utiliser et concéder sous licence le logiciel Visual Studio au fil du temps. Les administrateurs Visual Studio doivent effectuer une commande de régularisation annuelle pour amener leurs licences logicielles à la limite supérieure d’utilisation établie pendant la durée du contrat.