---
title: Assigner des GUID spécifiques à des abonnés Visual Studio | Microsoft Docs
author: evanwindom
ms.author: v-evwin
manager: cabuschl
ms.date: 03/19/2021
ms.topic: conceptual
description: Découvrez comment les administrateurs peuvent avoir un GUID d’abonnement spécifique aux abonnés
ms.openlocfilehash: a0721029186605c6b9a277c9eb95a370a086d7d2
ms.sourcegitcommit: d7d9fb79448b3534923cc95071d1f91eabde88e8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/22/2021
ms.locfileid: "104776648"
---
# <a name="assign-specific-subscriptions-in-the-visual-studio-subscriptions-administration-portal"></a>Affecter des abonnements spécifiques dans le portail d’administration des abonnements Visual Studio

Les administrateurs peuvent désormais utiliser le portail d’administration des abonnements Visual Studio pour affecter des abonnements spécifiques à des abonnés individuels.  Cela peut être utile dans les situations où l’organisation possède un personnel temporaire ou des fournisseurs qui ont besoin d’accéder à un abonnement pendant une brève période.  Les administrateurs peuvent attribuer un abonnement qui a déjà été partiellement utilisé, en laissant leurs nouveaux abonnements pour une utilisation à long terme.  

Regardez la vidéo ou lisez pour savoir comment affecter des GUID d’abonnements spécifiques aux utilisateurs. 

<br>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4t4cl]


## <a name="assign-specific-subscription-guids-to-users"></a>Affecter des GUID d’abonnement spécifiques aux utilisateurs

Le processus d’attribution d’abonnements spécifiques à des personnes implique l’utilisation de deux processus d’administration existants pour assigner des identificateurs globaux uniques (GUID) d’abonnement à des utilisateurs individuels.  Le processus en trois étapes comprend l’exportation d’une liste de vos abonnements et affectations actuels, en utilisant cette liste pour identifier les GUID spécifiques que vous souhaitez affecter, puis en utilisant le processus d’ajout en bloc pour charger les nouvelles attributions.

### <a name="export-your-subscriptions-information"></a>Exporter les informations de vos abonnements

Pour effectuer l’exportation :
1. Connectez-vous au [portail d’administration](https://manage.visualstudio.com).
2. Sélectionnez l’onglet **Exporter** : le fichier est alors téléchargé sur votre machine locale. Le fichier inclut le nom du compte de ce contrat qui contient les abonnements de vos utilisateurs, ainsi que la date de l’exportation.
> [!div class="mx-imgBorder"]
> ![Exporter des abonnés](_img/exporting-subscriptions/exporting-subscriptions.png "Cliquez sur Exporter pour enregistrer la liste des abonnements affectés avec les informations de l’abonné.")

### <a name="identify-the-guids-you-want-to-assign"></a>Identifier les GUID que vous souhaitez affecter

Si vous avez déjà utilisé l’outil d’exportation, vous remarquerez que de nouveaux champs ont été ajoutés à la feuille de calcul produite.  Ceux-ci vous aideront à déterminer l’état de chaque abonnement et ceux que vous souhaitez attribuer aux utilisateurs.  

- **État** de l’abonnement : ce champ indique « affecté » ou « non attribué ».  Si l’état d’un abonnement est « affecté », des informations sur l’utilisateur lui sont également associées, telles que le nom, l’adresse de messagerie, etc. 
- **État d’utilisation**: l’état d’utilisation indique « nouveau », ce qui signifie qu’il n’a jamais été affecté à un utilisateur, ou « utilisé », ce qui signifie qu’il a été affecté à un utilisateur à un moment donné.  

Vous pouvez utiliser les valeurs de ces champs avec d’autres informations dans la feuille de calcul pour déterminer les abonnements que vous souhaitez attribuer à des utilisateurs individuels. Vous pouvez appliquer un filtre dans Excel pour affiner la liste par État, niveau d’abonnement, date d’expiration, etc. 

### <a name="upload-your-new-assignments"></a>Charger vos nouvelles attributions

La dernière étape consiste à télécharger le modèle d' **Ajout en bloc** , à renseigner les informations requises pour les abonnements que vous souhaitez affecter et à télécharger le modèle.  Pour obtenir une description complète de ce processus, consultez l’article [ajouter plusieurs utilisateurs](assign-license-bulk.md) .  

> [!IMPORTANT]
> Pour garantir la réussite du téléchargement, vérifiez les éléments suivants :
> - Vous utilisez le modèle lié dans la boîte de dialogue lorsque vous sélectionnez **Ajout en bloc**.  N’utilisez pas de copie stockée localement du modèle, car il ne contient peut-être pas tous les champs requis.  L’utilisation d’un ancien modèle entraîne l’échec du chargement. 
> - Tous les champs indiqués comme **requis** dans le modèle sont terminés.
> - Aucune erreur n’est répertoriée dans la colonne **message d’erreur** .
> - Chaque GUID n’est utilisé qu’une seule fois dans le modèle. 
> - Le niveau d’abonnement dans le modèle correspond à l’abonnement du GUID dans la liste exportée. 
> - Le GUID n’est pas déjà attribué à un autre utilisateur dans la liste exportée. 

## <a name="frequently-asked-questions"></a>Forum aux questions
### <a name="q-how-do-i-change-which-subscription-is-currently-assigned-to-an-individual-user"></a>Q : Comment faire modifier l’abonnement actuellement attribué à un utilisateur individuel ?
R : Si vous souhaitez modifier le GUID affecté à un utilisateur, vous devez d’abord supprimer l’abonnement de cet utilisateur.  Pour plus d’informations, consultez notre article sur la [suppression des abonnements](delete-license.md) pour plus d’informations.  Après avoir supprimé l’abonnement pour cet utilisateur, utilisez la procédure décrite ci-dessus pour exporter la liste et télécharger les nouvelles informations d’abonnement.  

## <a name="resources"></a>Ressources
- [Prise en charge des abonnements](https://aka.ms/vsadminhelp)

## <a name="see-also"></a>Voir aussi
- [Documentation de Visual Studio](/visualstudio/)
- [Documentation Azure DevOps](/azure/devops/)
- [Documentation Azure](/azure/)
- [Documentation Microsoft 365](/microsoft-365/)

## <a name="next-steps"></a>Étapes suivantes
Maintenant que vous avez attribué des abonnements aux utilisateurs, Découvrez comment effectuer d’autres tâches d’administration.
- [Affecter des abonnements individuels](assign-license.md)
- [Attribuer plusieurs abonnements](assign-license-bulk.md)
- [Modifier des abonnements](edit-license.md)
- [Supprimer des abonnements](delete-license.md)
- [Déterminer l’utilisation maximale](maximum-usage.md)
