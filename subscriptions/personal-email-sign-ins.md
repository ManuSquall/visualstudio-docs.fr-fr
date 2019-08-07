---
title: E-mails personnels affichés dans VLSC
author: evanwindom
ms.author: lank
manager: lank
ms.date: 07/24/2019
ms.topic: conceptual
description: Abonnements Visual Studio – Pourquoi les adresses Hotmail ou Gmail de mes abonnés sont-elles affichées ?
ms.openlocfilehash: 8418a177e793f0b4fe9a5019d2cf62fa724312ff
ms.sourcegitcommit: ce1ab8a25c66a83e60eab80ed8e1596fe66dd85c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/29/2019
ms.locfileid: "68605758"
---
# <a name="visual-studio-subscriptions--why-am-i-seeing-hotmail-or-gmail-addresses-for-my-subscribers"></a>Abonnements Visual Studio – pourquoi les adresses Hotmail ou Gmail de mes abonnés sont-elles affichées ?
Après que les entreprises ont migré du Centre de gestion des licences en volume (VLSC) vers le nouveau [portail d’administration des abonnements](https://manage.visualstudio.com) Visual Studio, les administrateurs ont été surpris de découvrir que « l’adresse e-mail de connexion » de certains abonnés corresponde à une adresse e-mail de tiers, comme Hotmail, Gmail ou Yahoo.  Pour plus d’informations, regardez [cette vidéo](https://www.youtube.com/watch?v=J61EYaVN-dQ&list=PLReL099Y5nReJhZ6o8CQFPSBgzGCHX99_&index=6).

## <a name="cause"></a>Cause
Ceci est dû à des processus de connexion qui ont été associés à l’expérience héritée pour les abonnés MSDN. Les utilisateurs ont été migrés du centre de gestion des licences en volume (VLSC) vers le portail d’administration des abonnements Visual Studio sans modifications. Les administrateurs ignoraient peut-être que des utilisateurs utilisaient des comptes personnels pour accéder aux avantages de leurs abonnements. Avant les migrations des abonnés Visual Studio, qui se sont terminées en 2016, deux actions étaient nécessaires pour pouvoir utiliser un abonnement de Visual Studio :
1. L’administrateur « attribuait » l’abonnement à un abonné spécifique, à l’aide de son adresse e-mail professionnelle ou scolaire.
2. L’abonné « activait » l’abonnement.

Pendant le processus d’activation de l’abonné : Un compte Microsoft (MSA) était nécessaire pour la connexion. Si l’abonné ne cherchait pas à définir son compte professionnel ou scolaire (par exemple, tasha@contoso.com) en tant que compte MSA, il pouvait créer un compte MSA ou en utiliser un existant. C’est la raison pour laquelle son « adresse e-mail de connexion » était différente de son « adresse e-mail attribuée ».

> [!NOTE]
> La nouvelle expérience des abonnés sur [https://my.visualstudio.com](https://my.visualstudio.com?wt.mc_id=o~msft~docs) prend en charge à la fois les types d’identité Compte professionnel/scolaire et Compte Microsoft (MAA).

Enfin, étant donné que la migration des administrateurs utilisait des données de VLSC concernant « l’adresse e-mail de connexion » des abonnés pour renseigner la nouvelle expérience de gestion des abonnés, les administrateurs récemment migrés peuvent avoir vu ces comptes personnels jusque-là passés inaperçus en raison des modifications apportées à l’interface utilisateur qui ont rendu ces informations plus visibles.

## <a name="solution"></a>Solution
Pour corriger ce problème, vous devez modifier les informations des abonnés pour mettre à jour leurs adresses e-mail de connexion.  Les modifications peuvent être effectuées pour des abonnés spécifiques ou en masse. Pour plus d’informations, consultez [Modifier des abonnements](edit-license.md).

##  <a name="next-steps"></a>Étapes suivantes
- Si vous avez mis à jour les adresses e-mail des abonnés, vous pouvez informer ces derniers que leurs informations de connexion ont été modifiées.  Ils recevront également un e-mail contenant les informations mises à jour.
- Il peut être utile de [filtrer la liste des abonnés](search-license.md) de votre organisation pour rechercher les adresses e-mail de connexion qui peuvent nécessiter une modification.  

