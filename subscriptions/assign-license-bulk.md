---
title: Attribuer des licences à des groupes d’utilisateurs pour des abonnements Visual Studio | Microsoft Docs
author: evanwindom
ms.author: lank
manager: lank
ms.assetid: c2853359-18fd-4be4-97a6-02230c862f92
ms.date: 03/02/2020
ms.topic: conceptual
description: Découvrez comment les administrateurs peuvent attribuer des licences à plusieurs abonnés en utilisant soit la fonctionnalité d’ajout en vrac, soit les groupes Microsoft Azure Active Directory
ms.openlocfilehash: 3a4a6c400a17d52cdd67391a45ba088cdbb7af01
ms.sourcegitcommit: f8e3715c64255b476520bfa9267ceaf766bde3b0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/21/2020
ms.locfileid: "79988489"
---
# <a name="assign-subscriptions-to-multiple-users"></a>Attribuer des abonnements à plusieurs utilisateurs
Le portail d’administration des abonnements vous permet d’ajouter des utilisateurs un à la fois ou dans des grands groupes.  Pour ajouter des utilisateurs individuels, consultez [Ajouter des utilisateurs uniques](assign-license.md).

Pour ajouter de grands groupes d’utilisateurs, vous pouvez utiliser la fonctionnalité d’ajout en vrac, ou si votre organisation utilise Microsoft Azure Active Directory (Azure AD), vous pouvez utiliser les groupes Azure AD. Cet article expliquera le processus pour les deux options. 

## <a name="use-bulk-add-to-assign-subscriptions"></a>Utiliser Bulk add pour attribuer des abonnements
1. Connectez-vous au portail d’administration des abonnements Visual Studio à https://manage.visualstudio.com.

2. Pour ajouter plusieurs abonnés en même temps, naviguez vers l’onglet Gérer les **abonnés.** Choisissez l’onglet **Ajouter,** puis choisissez **Bulk ajouter** dans le drop-down.  

2. Bulk add utilise un modèle Microsoft Excel pour télécharger des informations d’abonné. Dans la boîte de dialogue permettant de charger plusieurs abonnés, cliquez sur **Télécharger** pour télécharger le modèle.
   > [!div class="mx-imgBorder"]
   > ![Télécharger le modèle Excel pour charger plusieurs abonnés](media/download-template-upload-subscribers.png)
   >
   > [!NOTE]
   > Téléchargez toujours la dernière version du modèle. L’utilisation d’une version antérieure peut faire échouer le chargement en bloc.

3. Dans la feuille de calcul Excel, renseignez les champs avec les informations relatives aux utilisateurs auxquels vous souhaitez attribuer des abonnements. (*La référence* est un champ optionnel.) Enregistrez le fichier localement après avoir terminé.

   Pour faciliter le chargement, respectez les bonnes pratiques suivantes :

    - Vérifiez que les champs de formulaire ne contiennent pas de virgules.
    - Supprimez les espaces avant et après les champs de formulaire.
    - Assurez-vous que les noms d’utilisateur ne contiennent pas d’espace superflu dans les noms ou prénoms composés (par exemple, si une personne porte le prénom composé « Maggie May », il doit être entré sous la forme « MaggieMay », car le système ne supprime pas l’espace superflu).
    - Assurez-vous que tous les champs requis sont terminés. 
    - Consultez la colonne de **message d’erreur.**  Si des erreurs sont énumérées, résolvez-les avant de tenter de télécharger le fichier. 

4. Revenez au portail d’administration des abonnements Visual Studio. Dans la boîte de dialogue permettant de **charger plusieurs abonnés**, cliquez sur **Parcourir**.
   > [!div class="mx-imgBorder"]
   > ![Accéder à votre modèle enregistré pour charger plusieurs abonnés](media/bulk-add-browse-saved-template.png)

5. Accédez au fichier Excel que vous avez enregistré, puis cliquez sur **OK**.
   > [!div class="mx-imgBorder"]
   > ![Charger le modèle Excel pour charger plusieurs abonnés](media/bulk-upload-subscribers.png)

    Une boîte de dialogue de progression du chargement s’affiche.

    Si le modèle contient des erreurs, le chargement échoue et les erreurs rencontrées s’affichent pour vous aider à corriger le modèle. Réessayez ensuite le chargement en bloc.
   > [!div class="mx-imgBorder"]
   > ![Message d’erreur si le chargement de plusieurs abonnés échoue](_img/assign-license-bulk/bulk-add-upload-failure.png)

   Si vous rencontrez un échec suivez ces étapes :
   1. Ouvrez le fichier Excel que vous avez créé, corrigez les problèmes et enregistrez le fichier.
   0. Retournez au portail d’administration et choisissez **Ajouter**.
   0. Sélectionnez **Ajout en vrac**.
   0. Puisque vous avez déjà le fichier Excel enregistré, vous n’avez pas besoin de télécharger le modèle.  Cliquez **sur Parcourir,** localiser le fichier que vous venez d’économiser, et cliquez sur **Open**.
   0. Cliquez sur **OK**.


    Quand le chargement est réussi, vous voyez s’afficher la liste des abonnés et un message de confirmation.
   > [!div class="mx-imgBorder"]
   > ![Message de confirmation si le chargement de plusieurs abonnés réussit](_img/assign-license-bulk/bulk-add-upload-success.png)

## <a name="use-azure-active-directory-groups-to-assign-subscriptions"></a>Utiliser les groupes d’annuaires Azure Active pour attribuer des abonnements 
L’utilisation de cette fonctionnalité permet de rester facilement au top de vos affectations d’abonnement. Vous pouvez ajouter des groupes de sécurité d’annuaire actif Azure dans le portail d’administration des abonnements qui garantiront que toutes les personnes du groupe se voient attribuer un abonnement. Et pour faciliter les choses, lorsque les individus quittent votre organisation et sont supprimés de l’annuaire actif Azure, leur accès aux abonnements est également supprimé. 


> [!IMPORTANT]
>
> L’utilisation des groupes Azure AD est activée par phases.  Vous ne pouvez pas voir immédiatement la fonctionnalité activée pour votre accord.s).
>
> Les limitations suivantes s’appliquent à l’utilisation des groupes Azure AD pour l’ajout d’abonnés :
> - Les groupes doivent contenir au moins un membre.  Les groupes vides ne sont pas soutenus.
> - Les groupes doivent avoir moins de 1 000 utilisateurs 
> - Tous les utilisateurs doivent être au plus haut niveau du groupe.  Les groupes imbriqués ne sont pas soutenus
> - Seuls les accords de confiance sont soutenus
> - Tous les membres du groupe doivent avoir une adresse e-mail associée à leur compte Azure AD
> - Les adresses e-mail séparées pour les notifications ne sont pas prises en charge pour les abonnements ajoutés à l’aide de groupes Azure AD.  

1. Connectez-vous au portail d’administration des abonnements Visual Studio à [https://manage.visualstudio.com](https://manage.visualstudio.com).

2. Pour ajouter plusieurs abonnés en même temps, naviguez vers l’onglet **Abonnés Gérer.**

3. Choisissez l’onglet **Ajouter,** puis sélectionnez **le groupe Azure Active Directory** dans le drop-down.  

   > [!div class="mx-imgBorder"]
   > ![Choisissez l’ajout en vrac à l’aide d’Azure AD](_img/assign-license-bulk/bulk-add-aad.png)

4. Commencez à entrer le nom du groupe Azure AD que vous souhaitez ajouter dans le champ de formulaire. Cela permettra de rechercher les groupes Azure AD disponibles au sein de votre organisation. 

5. Lorsque vous sélectionnez le groupe, le champ se remplit automatiquement avec le nom de groupe. Vous aurez la possibilité de visualiser les utilisateurs de ce groupe avant de les ajouter. Ensuite, vous pouvez choisir le niveau d’abonnement, les droits de téléchargement et les préférences de communication pour le groupe. Vous pouvez ajouter des détails dans le champ de référence si vous le souhaitez. 

   > [!div class="mx-imgBorder"]
   > ![Choisissez l’ajout en vrac à l’aide d’Azure AD](_img/assign-license-bulk/bulk-add-aad-details.png)

6. Cliquez **sur Ajouter** et ensuite **confirmer**. 

7. Pour voir le groupe ajouté, faites défiler vers le bas de votre liste d’utilisateurs.  

8. Sélectionnez **les abonnés View** pour afficher les membres du groupe. Vous pouvez consulter les détails sur les abonnés du groupe, mais vous ne pouvez pas faire de modifications aux abonnés ou aux abonnements qui leur sont attribués.    

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4rvvW]

## <a name="frequently-asked-questions"></a>Forum aux questions
### <a name="q-can-i-choose-multiple-subscription-levels-to-be-assigned-within-an-azure-ad-group"></a>Q : Puis-je choisir plusieurs niveaux d’abonnement à attribuer au sein d’un groupe Azure AD ? 
R: Non - tout le monde dans le groupe reçoit le même abonnement. 

### <a name="q-can-i-edit-subscriber-details-of-individuals-added-in-an-azure-ad-group"></a>Q: Puis-je modifier les détails d’abonnés des personnes ajoutées dans un groupe Azure AD ?  
R: Non -- Pour modifier les informations d’un abonné individuel, vous devrez les supprimer du groupe de sécurité Azure AD et leur attribuer un abonnement individuellement.  

### <a name="q-i-added-someone-to-my-azure-ad-security-group-but-i-dont-see-them-added-in-the-subscriptions-administration-portal-and-they-dont-have-a-subscription-why-not"></a>Q: J’ai ajouté quelqu’un à mon groupe de sécurité Azure AD, mais je ne les vois pas ajoutés dans le portail d’administration des abonnements, et ils n’ont pas d’abonnement. Pourquoi ?  
R : Selon la configuration de votre organisation Azure AD, vous pouvez voir des retards allant jusqu’à 24 heures avant l’ajout de l’utilisateur. Si cela fait plus de 24 heures, [contactez le support](https://visualstudio.microsoft.com/support/support-overview-vs).  

## <a name="see-also"></a>Voir aussi
- [Documentation Visual Studio](https://docs.microsoft.com/visualstudio/)
- [Documentation Azure DevOps](https://docs.microsoft.com/azure/devops/)
- [Documentation Azure](https://docs.microsoft.com/azure/)
- [Documentation Microsoft 365](https://docs.microsoft.com/microsoft-365/)

## <a name="next-steps"></a>Étapes suivantes
- Vous n’avez qu’un ou deux abonnés à ajouter ?  Consultez [Ajouter des utilisateurs uniques](assign-license.md)
- Vous avez besoin d’aide ? Contactez [Visual Studio Administration et Subscriptions Support](https://visualstudio.microsoft.com/support/support-overview-vs).
