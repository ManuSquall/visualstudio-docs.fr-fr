---
title: Affichage des e-mails personnels dans VLSC
Author: evanwindom
Ms.author: jaunger
Manager: evelynp
Ms.date: 1/23/2018
Ms.topic: Get-Started-Article
Description: "Visual Studio Subscriptions – Why Am I Seeing Hotmail or Gmail Addresses for My Subscribers?"
Ms.prod: vs-subscription
Ms.technology: vs-subscriptions
Searchscope: VS Subscription
ms.openlocfilehash: 2bfe2f39d432be5fc6ff7b24be2a218d02fce961
ms.sourcegitcommit: b18844078a30d59014b48a9c247848dea188b0ee
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/29/2018
---
# <a name="visual-studio-subscriptions--why-am-i-seeing-hotmail-or-gmail-addresses-for-my-subscribers"></a>Abonnements Visual Studio – Pourquoi les adresses Hotmail ou Gmail de mes abonnés sont-elles affichées ? 

Au fur et à mesure que les entreprises migrent du Centre de gestion des licences en volume (VLSC) vers le nouveau [portail d’administration des abonnements](https://manage.visualstudio.com) Visual Studio, les administrateurs peuvent être surpris de découvrir que « l’adresse e-mail de connexion » de certains abonnés correspond à une adresse e-mail tierce, telle que Yahoo, Gmail ou Hotmail.

## <a name="cause"></a>Cause

Ce cas se produit en raison de processus de connexion qui ont été associés à l’expérience d’abonné MSDN héritée. Les utilisateurs ont migré de VLSC vers le nouveau portail sans effectuer de modifications. Certains administrateurs peuvent ignorer que des utilisateurs utilisaient des comptes personnels pour accéder aux avantages de leurs abonnements. Avant les migrations des abonnés Visual Studio, qui se sont terminées en 2016, deux actions étaient nécessaires pour pouvoir utiliser un abonnement de Visual Studio :
1. L’administrateur « attribuait » l’abonnement à un abonné spécifique, à l’aide de son adresse e-mail professionnelle ou scolaire.
2. L’abonné « activait » l’abonnement.

Pendant le processus d’activation de l’abonné :
1. Un compte Microsoft (MSA) était nécessaire pour la connexion.
2. Si l’abonné ne cherchait pas à définir son compte professionnel ou scolaire (par exemple, John@contoso.com) en tant que compte MSA, il pouvait créer un compte MSA ou en utiliser un existant.
3. C’est la raison pour laquelle son « adresse e-mail de connexion » était différente de son « adresse e-mail attribuée ».

> [!NOTE] 
> La nouvelle expérience des abonnés sur [https://my.visualstudio.com](https://my.visualstudio.com?wt.mc_id=o~msft~docs) prend à la fois en charge les types d’identité de compte professionnel/scolaire et de compte Microsoft (MSA).

Enfin, étant donné que la migration des administrateurs utilise des données de VLSC concernant « l’adresse e-mail de connexion » des abonnés pour renseigner la nouvelle expérience de gestion des abonnés, les administrateurs qui ont récemment migré peuvent voir ces comptes personnels jusque-là passés inaperçus en raison des modifications apportées à l’interface utilisateur qui rendent cette information plus visible.

## <a name="solution"></a>Solution

Pour corriger ce problème, vous devez modifier les informations des abonnés pour mettre à jour leurs adresses e-mail de connexion.  Les modifications peuvent être effectuées pour des abonnés spécifiques ou en masse. Pour plus d’informations, consultez [Modifier un abonnement](/visualstudio/subscriptions/edit-license).  

Une fois les adresses e-mail des abonnés mises à jour, vous pouvez informer ces derniers que leurs informations de connexion ont été modifiées.  