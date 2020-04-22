---
title: Attribuer des GUID spécifiques aux abonnés de Visual Studio . Microsoft Docs
author: evanwindom
ms.author: lank
manager: lank
ms.date: 04/20/2020
ms.topic: conceptual
description: Découvrez comment les administrateurs peuvent souscription spécifique de GUID aux abonnés
ms.openlocfilehash: 722aaedcd6da0224311960d1587d0c2c24eec60f
ms.sourcegitcommit: a7f781d5a089e6aab6b073a07f3d4d2967af8aa6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2020
ms.locfileid: "81760159"
---
# <a name="assign-specific-subscriptions-in-the-visual-studio-subscriptions-administration-portal"></a>Attribuer des abonnements spécifiques dans le portail d’administration des abonnements Visual Studio

Les administrateurs peuvent désormais utiliser le portail d’administration des abonnements Visual Studio pour attribuer des abonnements spécifiques à des abonnés individuels.  Cela peut être utile dans les situations où l’organisation a du personnel temporaire ou des fournisseurs qui ont besoin d’accéder à un abonnement pour une courte période.  Les administrateurs peuvent attribuer un abonnement qui a déjà été partiellement utilisé, laissant leurs nouveaux abonnements pour une utilisation à plus long terme.  

<br>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4t4cl]


## <a name="assign-specific-subscription-guids-to-users"></a>Attribuer des INTERFACEs d’abonnement spécifiques aux utilisateurs

Le processus d’attribution d’abonnements spécifiques à des particuliers consiste à tirer parti de deux processus d’administration existants pour attribuer des identifiants uniques (GUID) spécifiques à des utilisateurs individuels.  Le processus en trois étapes comprend l’exportation d’une liste de vos abonnements et affectations actuels, l’utilisation de cette liste pour identifier les GUID spécifiques que vous souhaitez attribuer, puis l’utilisation du processus d’ajout en vrac pour télécharger les nouvelles affectations.

### <a name="export-your-subscriptions-information"></a>Exportez vos informations d’abonnement

Pour effectuer l’exportation :
1. Connectez-vous au [portail d’administration](https://manage.visualstudio.com).
2. Sélectionnez l’onglet **Exporter** : le fichier est alors téléchargé sur votre machine locale. Le fichier inclut le nom du compte de ce contrat qui contient les abonnements de vos utilisateurs, ainsi que la date de l’exportation.
> [!div class="mx-imgBorder"]
> ![Exporter des abonnés](_img/exporting-subscriptions/exporting-subscriptions.png)

### <a name="identify-the-guids-you-want-to-assign"></a>Identifiez les GUID que vous souhaitez assigner

Si vous avez déjà utilisé l’outil Export, vous remarquerez que de nouveaux champs ont été ajoutés à la feuille de calcul produite.  Ceux-ci vous aideront à déterminer l’état de chaque abonnement et ceux que vous souhaitez affecter aux utilisateurs.  

- **Statut d’abonnement**: Ce champ indiquera soit "attribué" ou "non attribué".  Si un abonnement a un statut de «attribué», il aura également des informations utilisateur qui lui sont associées, tels que le nom, e-mail, etc. 
- **État d’utilisation**: Le statut d’utilisation indiquera soit «nouveau», ce qui signifie qu’il n’a jamais été attribué à un utilisateur, ou «utilisé» qui indique qu’il a été attribué à un utilisateur à un moment donné.  

Vous pouvez utiliser les valeurs dans ces domaines ainsi que d’autres informations dans la feuille de calcul pour déterminer quels abonnements vous souhaitez affecter à des utilisateurs individuels. Vous pouvez appliquer un filtre dans Excel pour aider à réduire la liste par statut, niveau d’abonnement, date d’expiration, etc. 

### <a name="upload-your-new-assignments"></a>Téléchargez vos nouvelles missions

La dernière étape consiste à télécharger le modèle **d’ajout en vrac,** à remplir les informations requises pour les abonnements que vous souhaitez attribuer et à télécharger le modèle.  Pour une description complète de ce processus, s’il vous plaît voir notre [article Ajouter plusieurs utilisateurs.](assign-license-bulk.md)  

> [!IMPORTANT]
> Pour assurer un téléchargement réussi, s’il vous plaît assurez-vous que:
> - Tous les champs indiqués comme requis dans **le** modèle sont complets.
> - Il n’y a pas d’erreurs énumérées dans la colonne **de message d’erreur.**
> - Chaque GUID n’est utilisé qu’une seule fois dans le modèle. 
> - Le niveau d’abonnement dans le modèle correspond à l’abonnement du GUID dans la liste exportée. 
> - Le GUID n’est pas déjà attribué à un autre utilisateur de la liste exportée. 

## <a name="frequently-asked-questions"></a>Forum aux questions
### <a name="qhow-do-i-change-which-subscription-is-currently-assigned-to-an-individual-user"></a>Q : Comment puis-je modifier l’abonnement qui est actuellement attribué à un utilisateur individuel ?
R : Si vous souhaitez modifier le GUID attribué à un utilisateur, vous devez d’abord supprimer l’abonnement de cet utilisateur.  Pour plus d’informations, veuillez consulter notre article [Supprimer les abonnements](delete-license.md) pour plus d’informations.  Après avoir supprimé l’abonnement pour cet utilisateur, utilisez le processus décrit ci-dessus pour exporter la liste et télécharger les nouvelles informations d’abonnement.  

## <a name="see-also"></a>Voir aussi
- [Documentation Visual Studio](/visualstudio/)
- [Documentation Azure DevOps](/azure/devops/)
- [Documentation Azure](/azure/)
- [Documentation Microsoft 365](/microsoft-365/)

## <a name="next-steps"></a>Étapes suivantes
Maintenant que vous avez affecté des abonnements aux utilisateurs, découvrez comment effectuer d’autres tâches d’administration.
- [Attribuer des abonnements individuels](assign-license.md)
- [Attribuer plusieurs abonnements](assign-license-bulk.md)
- [Modifier des abonnements](edit-license.md)
- [Supprimer des abonnements](delete-license.md)
- [Déterminer l’utilisation maximale](maximum-usage.md)


