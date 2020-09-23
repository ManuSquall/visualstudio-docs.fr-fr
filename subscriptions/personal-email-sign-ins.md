---
title: E-mails personnels affichés dans VLSC
author: evanwindom
ms.author: v-evwin
manager: cabuschl
ms.assetid: 3f4b0528-03f0-4a02-b3c3-a39292a9bbe1
ms.date: 09/22/2020
ms.topic: conceptual
description: Abonnements Visual Studio – Pourquoi les adresses Hotmail ou Gmail de mes abonnés sont-elles affichées ?
ms.openlocfilehash: dc2de6c852f39f789fb07358384ad490d13f137c
ms.sourcegitcommit: 4affcf2830337e6aba84621c3eda5faf5d0d4a01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91022648"
---
# <a name="visual-studio-subscriptions--why-do-i-see-personal-accounts-for-my-subscribers"></a>Abonnements Visual Studio : pourquoi les comptes personnels s’affichent-ils pour mes abonnés ?
Une fois que les sociétés ont migré du centre de gestion des licences en volume (VLSC) vers le nouveau [portail d’administration des abonnements](https://manage.visualstudio.com)Visual Studio, les administrateurs ont été surpris de trouver que l’adresse de messagerie de connexion pour certains abonnés affiche une adresse e-mail personnelle comme Hotmail ou Outlook.  

## <a name="cause"></a>Cause
Ceci est dû à des processus de connexion qui ont été associés à l’expérience héritée pour les abonnés MSDN. Les utilisateurs ont été migrés du centre de gestion des licences en volume (VLSC) vers le portail d’administration des abonnements Visual Studio sans modifications. Les administrateurs ignoraient peut-être que des utilisateurs utilisaient des comptes personnels pour accéder aux avantages de leurs abonnements. Avant les migrations des abonnés Visual Studio, qui se sont terminées en 2016, deux actions étaient nécessaires pour pouvoir utiliser un abonnement de Visual Studio :
1. L’administrateur « attribuait » l’abonnement à un abonné spécifique, à l’aide de son adresse e-mail professionnelle ou scolaire.
2. L’abonné « activait » l’abonnement.

Au cours du processus d’activation de l’abonné, un compte Microsoft (MSA) était nécessaire pour se connecter. Si l’abonné ne cherchait pas à définir son compte professionnel ou scolaire (par exemple, tasha@contoso.com) en tant que compte MSA, il pouvait créer un compte MSA ou en utiliser un existant. C’est la raison pour laquelle son « adresse e-mail de connexion » était différente de son « adresse e-mail attribuée ».

> [!NOTE]
> L’expérience de l’abonné moderne sur [https://my.visualstudio.com](https://my.visualstudio.com?wt.mc_id=o~msft~docs) prend en charge les types d’identité professionnel/scolaire et compte Microsoft (MSA).

## <a name="solution"></a>Solution
Pour résoudre le problème, il vous suffit de sélectionner le bouton **Connect emails (connecter les e-mails** ) pour que le système tente de faire correspondre les comptes avec MSAS aux utilisateurs existants dans le Azure Active Directory de votre organisation (Azure AD), en fonction de la correspondance du prénom et du nom. En cas d’erreur, vous pouvez supprimer toute correspondance en cliquant sur le **X** à droite de la correspondance.  

Regardez cette vidéo ou poursuivez votre lecture pour savoir comment résoudre ce problème. 

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4th6B]

> [!div class="mx-imgBorder"]
> ![Bouton connecter des E-mails](_img/connect-emails/connect-emails-button.png "Cliquez sur connecter les E-mails pour faire correspondre vos utilisateurs avec des comptes Microsoft à votre Azure Active Directory")

Vous pouvez également utiliser le **Répertoire de recherche** pour corriger les erreurs ou renseigner les informations manquantes de votre Azure ad. Si toutes les correspondances semblent correctes, vous pouvez choisir le bouton **identité actuelle** pour sélectionner toutes les entrées correspondantes au lieu de les sélectionner une à la fois.  

> [!div class="mx-imgBorder"]
> ![Connexion des E-mails à la volée](_img/connect-emails/connect-emails-flyout.png "Sélectionnez les abonnés que vous souhaitez faire correspondre à leurs identités Azure AD, puis cliquez sur continuer.")

Ensuite, cliquez sur **Continuer** pour accéder à la liste des modifications à effectuer. Si vous acceptez, cliquez sur **Enregistrer** pour effectuer les modifications. Votre abonné recevra également un message les informant de la modification la prochaine fois qu’il se connectera à son abonnement.  Notez que seuls les deux abonnés qui ont été mis en correspondance dans la Azure Active Directory apparaissent dans cette liste.  Dans notre exemple, étant donné que Frederick n’a pas d’adresse correspondante dans le Azure AD, son compte Microsoft (MSA) n’a pas été mis en correspondance avec un compte professionnel. 

> [!div class="mx-imgBorder"]
> ![Confirmation de connexion des E-mails](_img/connect-emails/connect-emails-confirm.png "Cliquez sur continuer pour implémenter les modifications proposées, puis cliquez sur Enregistrer.") 

> [!NOTE]
> Lorsque vous modifiez l’adresse de messagerie de connexion, vous ne pouvez mettre à jour que l’e-mail utilisé par l’abonné pour se connecter à son abonnement https://my.visualstudio.com . Si l’abonné a déjà activé des avantages tels qu’Azure ou Pluralsight à l’aide de l’autre adresse de messagerie, il doit continuer à utiliser ces adresses de messagerie pour y accéder. Pour les nouveaux avantages auxquels ils accèdent, ils doivent utiliser la nouvelle adresse de messagerie. 

## <a name="see-also"></a>Voir aussi
- [Documentation de Visual Studio](/visualstudio/)
- [Documentation Azure DevOps](/azure/devops/)
- [Documentation Azure](/azure/)
- [Documentation Microsoft 365](/microsoft-365/)

##  <a name="next-steps"></a>Étapes suivantes
- Si vous avez mis à jour les adresses e-mail des abonnés, vous pouvez informer ces derniers que leurs informations de connexion ont été modifiées.  Ils recevront également un e-mail contenant les informations mises à jour.
- Il peut être utile de [filtrer la liste des abonnés](search-license.md) de votre organisation pour rechercher les adresses e-mail de connexion qui peuvent nécessiter une modification.