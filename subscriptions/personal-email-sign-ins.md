---
title: Affichage des e-mails personnels dans VLSC
author: evanwindom
ms.author: jaunger
manager: evelynp
ms.date: 01/23/2018
ms.topic: Get-Started-Article
description: Abonnements Visual Studio – Pourquoi les adresses Hotmail ou Gmail de mes abonnés sont-elles affichées ?
ms.prod: vs-subscription
ms.technology: vs-subscriptions
searchscope: VS Subscription
ms.openlocfilehash: 3ac8a86bae706b4a68b8e3ccde94a9ee84d608a9
ms.sourcegitcommit: 928885ace538bef5b25961358d4f166d648f196a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2018
---
# <a name="visual-studio-subscriptions--why-am-i-seeing-hotmail-or-gmail-addresses-for-my-subscribers"></a>Abonnements Visual Studio – pourquoi les adresses Hotmail ou Gmail de mes abonnés sont-elles affichées ? 

Au fur et à mesure que les entreprises migrent du Centre de gestion des licences en volume (VLSC) vers le nouveau [portail d’administration des abonnements](https://manage.visualstudio.com) Visual Studio, les administrateurs peuvent être surpris de découvrir que « l’adresse e-mail de connexion » de certains abonnés correspond à une adresse e-mail tierce, telle que Yahoo, Gmail ou Hotmail.  Pour plus d’informations, regardez [cette vidéo](https://www.youtube.com/watch?v=1op-i1zEMfY&t=0s&list=PLReL099Y5nRfDyvvwzNDBaZe7qTxmuM2T&index=6).

## <a name="cause"></a>Cause

Ceci est dû à des processus de connexion qui ont été associés à l’expérience héritée pour les abonnés MSDN. Les utilisateurs ont migré du centre de gestion des licences en volume (VLSC) vers le nouveau portail sans effectuer de modifications. Les administrateurs ignoraient peut-être que des utilisateurs utilisaient des comptes personnels pour accéder aux avantages de leurs abonnements. Avant les migrations des abonnés Visual Studio, qui se sont terminées en 2016, deux actions étaient nécessaires pour pouvoir utiliser un abonnement de Visual Studio :
1. L’administrateur « attribuait » l’abonnement à un abonné spécifique, à l’aide de son adresse e-mail professionnelle ou scolaire.
2. L’abonné « activait » l’abonnement.

Au cours du processus d’activation de l’abonné, un compte Microsoft (MSA) était nécessaire pour se connecter. Si l’abonné ne cherchait pas à définir son compte professionnel ou scolaire (par exemple, tasha@contoso.com) en tant que compte MSA, il pouvait créer un compte MSA ou en utiliser un existant. C’est la raison pour laquelle son « adresse e-mail de connexion » était différente de son « adresse e-mail attribuée ».

> [!NOTE] 
> La nouvelle expérience des abonnés sur [https://my.visualstudio.com](https://my.visualstudio.com?wt.mc_id=o~msft~docs) prend en charge à la fois les types d’identité Compte professionnel/scolaire et Compte Microsoft (MAA).

Enfin, étant donné que la migration des administrateurs utilise des données de VLSC concernant « l’adresse e-mail de connexion » des abonnés pour renseigner la nouvelle expérience de gestion des abonnés, les administrateurs qui ont récemment migré peuvent voir ces comptes personnels jusque-là passés inaperçus en raison des modifications apportées à l’interface utilisateur qui rendent cette information plus visible.

## <a name="solution"></a>Solution

Pour corriger ce problème, vous devez modifier les informations des abonnés pour mettre à jour leurs adresses e-mail de connexion.  Les modifications peuvent être effectuées pour des abonnés spécifiques ou en masse. Pour plus d’informations, consultez [Modifier un abonnement](/visualstudio/subscriptions/edit-license).  

Une fois les adresses e-mail des abonnés mises à jour, vous pouvez informer ces derniers que leurs informations de connexion ont été modifiées.  Ils recevront également un e-mail contenant les informations mises à jour.   