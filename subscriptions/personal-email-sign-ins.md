---
title: E-mails personnels affichés dans VLSC
author: evanwindom
ms.author: lank
manager: lank
ms.assetid: 3f4b0528-03f0-4a02-b3c3-a39292a9bbe1
ms.date: 03/17/2020
ms.topic: conceptual
description: Abonnements Visual Studio – Pourquoi les adresses Hotmail ou Gmail de mes abonnés sont-elles affichées ?
ms.openlocfilehash: 7cd6a4761efb7dcad7568bd0a95ba33141407055
ms.sourcegitcommit: f8e3715c64255b476520bfa9267ceaf766bde3b0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/21/2020
ms.locfileid: "79550338"
---
# <a name="visual-studio-subscriptions--why-do-i-see-personal-accounts-for-my-subscribers"></a>Abonnements Visual Studio - Pourquoi vois-je des comptes personnels pour mes abonnés ?
Après que les entreprises ont migré du Volume Licensing Service Center (VLSC) vers le nouveau portail Visual Studio [Subscriptions Administration](https://manage.visualstudio.com), les administrateurs ont été surpris de constater que l’adresse e-mail « Connect-in » pour certains abonnés montre une adresse e-mail personnelle comme Hotmail ou Outlook.  Pour plus d’informations, regardez [cette vidéo](https://www.youtube.com/watch?v=J61EYaVN-dQ&list=PLReL099Y5nReJhZ6o8CQFPSBgzGCHX99_&index=6).

## <a name="cause"></a>Cause :
Ceci est dû à des processus de connexion qui ont été associés à l’expérience héritée pour les abonnés MSDN. Les utilisateurs ont été migrés du centre de gestion des licences en volume (VLSC) vers le portail d’administration des abonnements Visual Studio sans modifications. Les administrateurs ignoraient peut-être que des utilisateurs utilisaient des comptes personnels pour accéder aux avantages de leurs abonnements. Avant les migrations des abonnés Visual Studio, qui se sont terminées en 2016, deux actions étaient nécessaires pour pouvoir utiliser un abonnement de Visual Studio :
1. L’administrateur « attribuait » l’abonnement à un abonné spécifique, à l’aide de son adresse e-mail professionnelle ou scolaire.
2. L’abonné « activait » l’abonnement.

Au cours du processus d’activation de l’abonné, un compte Microsoft (MSA) était nécessaire pour se connecter. Si l’abonné ne cherchait pas à définir son compte professionnel ou scolaire (par exemple, tasha@contoso.com) en tant que compte MSA, il pouvait créer un compte MSA ou en utiliser un existant. C’est la raison pour laquelle son « adresse e-mail de connexion » était différente de son « adresse e-mail attribuée ».

> [!NOTE]
> L’expérience d’abonné moderne sur [https://my.visualstudio.com](https://my.visualstudio.com?wt.mc_id=o~msft~docs) les types d’identité Work/School et Microsoft Account (MSA).

## <a name="solution"></a>Solution
Pour corriger le problème, il suffit de sélectionner le bouton **e-mails Connect** et le système tentera de faire correspondre les comptes avec les MSAs aux utilisateurs existants dans l’annuaire actif Azure de votre organisation (Azure AD) en fonction de l’appariement du prénom et du nom de famille. S’il y a une erreur, vous pouvez supprimer n’importe quel match en cliquant sur le **X** à droite du match.  

> [!div class="mx-imgBorder"]
> ![Connectez le bouton e-mails](_img/connect-emails/connect-emails-button.png)

Vous pouvez également utiliser **l’annuaire de recherche** pour corriger les erreurs ou remplir les informations manquantes de votre AD Azure. Si tous les matchs semblent corrects, vous pouvez choisir de "Sélectionner tous les abonnés correspondants", plutôt que de les sélectionner un à la fois.  

> [!div class="mx-imgBorder"]
> ![Connectez emails Fly-out](_img/connect-emails/connect-emails-flyout.png)

Cliquez ensuite sur "continuer" qui vous mènera à un écran décrivant les modifications à effectuer. Si vous êtes d’accord, cliquez sur "enregistrer" et les modifications seront apportées. Votre abonné recevra également un message l’informant du changement la prochaine fois qu’il se connecte à son abonnement.   

> [!div class="mx-imgBorder"]
> ![Connectez la confirmation des e-mails](_img/connect-emails/connect-emails-confirm.png) 

> [!NOTE]
> Lorsque vous modifiez le signe dans l’adresse e-mail, cela https://my.visualstudio.comne met à jour que l’e-mail utilisé par l’abonné pour se connecter à leur abonnement sur . Si l’abonné a déjà activé des avantages tels qu’Azure ou Pluralsight à l’aide de l’autre adresse e-mail, il devra continuer à utiliser ces adresses e-mail pour y accéder. Pour tout nouvel avantage auxquels ils ont accès, ils doivent utiliser la nouvelle adresse e-mail. 

## <a name="see-also"></a>Voir aussi
- [Documentation Visual Studio](https://docs.microsoft.com/visualstudio/)
- [Documentation Azure DevOps](https://docs.microsoft.com/azure/devops/)
- [Documentation Azure](https://docs.microsoft.com/azure/)
- [Documentation Microsoft 365](https://docs.microsoft.com/microsoft-365/)

##  <a name="next-steps"></a>Étapes suivantes
- Si vous avez mis à jour les adresses e-mail des abonnés, vous pouvez informer ces derniers que leurs informations de connexion ont été modifiées.  Ils recevront également un e-mail contenant les informations mises à jour.
- Il peut être utile de [filtrer la liste des abonnés](search-license.md) de votre organisation pour rechercher les adresses e-mail de connexion qui peuvent nécessiter une modification.  
