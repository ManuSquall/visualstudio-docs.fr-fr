---
title: Attribuer des licences à des groupes d’utilisateurs pour des abonnements Visual Studio | Microsoft Docs
author: evanwindom
ms.author: lank
manager: lank
ms.date: 03/02/2020
ms.topic: conceptual
description: Découvrez comment les administrateurs peuvent attribuer des licences à plusieurs abonnés à l’aide de la fonctionnalité d’ajout en bloc ou de groupes de Microsoft Azure Active Directory
ms.openlocfilehash: c8ea294f0e4b2b4deae18e2f5644bf08fff0dfc2
ms.sourcegitcommit: 3154387056160bf4c36ac8717a7fdc0cd9faf3f9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/06/2020
ms.locfileid: "78410407"
---
# <a name="assign-subscriptions-to-multiple-users"></a>Attribuer des abonnements à plusieurs utilisateurs
Le portail d’administration des abonnements vous permet d’ajouter des utilisateurs un à la fois ou dans des grands groupes.  Pour ajouter des utilisateurs individuels, consultez [Ajouter des utilisateurs uniques](assign-license.md).

Pour ajouter des groupes d’utilisateurs importants, vous pouvez utiliser la fonctionnalité d’ajout en bloc ou, si votre organisation utilise Microsoft Azure Active Directory (Azure AD), vous pouvez utiliser des groupes de Azure AD. Cet article explique le processus pour les deux options. 

## <a name="use-bulk-add-to-assign-subscriptions"></a>Utiliser l’ajout en bloc pour affecter des abonnements
1. Connectez-vous au portail d’administration des abonnements Visual Studio à l’adresse https://manage.visualstudio.com.

2. Pour ajouter plusieurs abonnés à la fois, accédez à l’onglet **gérer les abonnés** . Choisissez l’onglet **Ajouter** , puis choisissez **Ajouter en bloc** dans la liste déroulante.  

2. L’ajout en bloc utilise un modèle Microsoft Excel pour télécharger les informations de l’abonné. Dans la boîte de dialogue permettant de charger plusieurs abonnés, cliquez sur **Télécharger** pour télécharger le modèle.
   > [!div class="mx-imgBorder"]
   > ![Télécharger le modèle Excel pour charger plusieurs abonnés](media/download-template-upload-subscribers.png)
   >
   > [!NOTE]
   > Téléchargez toujours la dernière version du modèle. L’utilisation d’une version antérieure peut faire échouer le chargement en bloc.

3. Dans la feuille de calcul Excel, renseignez les champs avec les informations relatives aux utilisateurs auxquels vous souhaitez attribuer des abonnements. (La*référence* est un champ facultatif.) Enregistrez le fichier localement une fois que vous avez terminé.

   Pour faciliter le chargement, respectez les bonnes pratiques suivantes :

    - Vérifiez que les champs de formulaire ne contiennent pas de virgules.
    - Supprimez les espaces avant et après les champs de formulaire.
    - Assurez-vous que les noms d’utilisateur ne contiennent pas d’espace superflu dans les noms ou prénoms composés (par exemple, si une personne porte le prénom composé « Maggie May », il doit être entré sous la forme « MaggieMay », car le système ne supprime pas l’espace superflu).
    - Assurez-vous que tous les champs obligatoires sont remplis. 
    - Vérifiez la colonne **message d’erreur** .  Si des erreurs sont répertoriées, résolvez-les avant de tenter de charger le fichier. 

4. Revenez au portail d’administration des abonnements Visual Studio. Dans la boîte de dialogue permettant de **charger plusieurs abonnés**, cliquez sur **Parcourir**.
   > [!div class="mx-imgBorder"]
   > ![Accéder à votre modèle enregistré pour charger plusieurs abonnés](media/bulk-add-browse-saved-template.png)

5. Accédez au fichier Excel que vous avez enregistré, puis cliquez sur **OK**.
   > [!div class="mx-imgBorder"]
   > ![Charger le modèle Excel pour charger plusieurs abonnés](media/bulk-upload-subscribers.png)

    Une boîte de dialogue de progression du chargement s’affiche.

    Si le modèle contient des erreurs, le chargement échoue et les erreurs rencontrées s’affichent pour vous aider à corriger le modèle. Réessayez ensuite le chargement en bloc.
   > [!div class="mx-imgBorder"]
   > ![Message d’erreur si le chargement de plusieurs abonnés échoue](media/bulk-add-template-failed.png)

    Quand le chargement est réussi, vous voyez s’afficher la liste des abonnés et un message de confirmation.
   > [!div class="mx-imgBorder"]
   > ![Message de confirmation si le chargement de plusieurs abonnés réussit](media/bulk-add-template-success.png)

## <a name="use-azure-active-directory-groups-to-assign-subscriptions"></a>Utiliser des groupes de Azure Active Directory pour affecter des abonnements 
Grâce à cette fonctionnalité, il est facile de rester au-dessus de vos affectations d’abonnement. Vous pouvez ajouter Azure Active Directory groupes de sécurité dans le portail d’administration des abonnements, ce qui garantit que tous les individus du groupe se voient attribuer un abonnement. Et pour faciliter la tâche, lorsque les individus sortent de votre organisation et sont supprimés de Azure Active Directory, leur accès aux abonnements est également supprimé. 

> [!IMPORTANT]
> Les limitations suivantes s’appliquent à l’utilisation de groupes de Azure AD pour l’ajout d’abonnés :
> - Les groupes doivent contenir au moins un membre.  Les groupes vides ne sont pas pris en charge.
> - Les groupes doivent avoir moins de 1 000 utilisateurs 
> - Tous les utilisateurs doivent se trouver au niveau supérieur du groupe.  Les groupes imbriqués ne sont pas pris en charge
> - Seuls les accords approuvés sont pris en charge
> - Tous les membres du groupe doivent avoir une adresse de messagerie associée à leur compte Azure AD


1. Connectez-vous au portail d’administration des abonnements Visual Studio à l’adresse [https://manage.visualstudio.com](https://manage.visualstudio.com).

2. Pour ajouter plusieurs abonnés à la fois, accédez à l’onglet **gérer les abonnés** .

3. Choisissez l’onglet **Ajouter** , puis sélectionnez **Azure Active Directory groupe** dans la liste déroulante.  

   > [!div class="mx-imgBorder"]
   > ![choisissez ajout en bloc à l’aide d’Azure AD](_img/assign-license-bulk/bulk-add-aad.png)


4. Commencez par entrer le nom du groupe de Azure AD que vous souhaitez ajouter dans le champ de formulaire. Cela permet de rechercher les groupes de Azure AD disponibles au sein de votre organisation. 

5. Lorsque vous sélectionnez le groupe, le champ est automatiquement renseigné avec le nom du groupe. Vous avez la possibilité d’afficher les utilisateurs de ce groupe avant de les ajouter. Ensuite, vous pouvez choisir le niveau d’abonnement, les droits de téléchargement et les préférences de communication pour le groupe. Si vous le souhaitez, vous pouvez ajouter des détails dans le champ de référence. 

   > [!div class="mx-imgBorder"]
   > ![choisissez ajout en bloc à l’aide d’Azure AD](_img/assign-license-bulk/bulk-add-aad-details.png)

6. Cliquez sur **Ajouter** , puis sur **confirmer**. 

7. Pour afficher le groupe ajouté, faites défiler la liste des utilisateurs vers le bas.  

8. Sélectionnez **afficher les abonnés** pour afficher les membres du groupe. Vous pouvez afficher des détails sur les abonnés dans le groupe, mais vous ne pouvez pas apporter de modifications aux abonnés ou aux abonnements auxquels ils sont affectés.    

## <a name="frequently-asked-questions"></a>Forum aux questions
### <a name="q-can-i-choose-multiple-subscription-levels-to-be-assigned-within-an-azure-ad-group"></a>Q : puis-je choisir plusieurs niveaux d’abonnement à affecter au sein d’un groupe de Azure AD ? 
R : non--tous les membres du groupe reçoivent le même abonnement. 

### <a name="q-can-i-edit-subscriber-details-of-individuals-added-in-an-azure-ad-group"></a>Q : puis-je modifier les détails de l’abonné des personnes ajoutées à un groupe de Azure AD ?  
R : non--pour modifier les informations d’un abonné individuel, vous devez les supprimer du groupe de sécurité Azure AD et leur attribuer un abonnement individuellement.  

### <a name="q-i-added-someone-to-my-azure-ad-security-group-but-i-dont-see-them-added-in-the-subscriptions-administration-portal-and-they-dont-have-a-subscription-why-not"></a>Q : J’ai ajouté une personne à mon Azure AD groupe de sécurité, mais je ne l’ai pas ajoutée dans le portail d’administration des abonnements et il n’y a pas d’abonnement. Pourquoi ?  
R : selon la façon dont votre organisation a configuré Azure AD, vous pouvez constater des retards jusqu’à 24 heures avant l’ajout de l’utilisateur. S’il s’agit d’une durée supérieure à 24 heures, [Contactez le support technique](https://visualstudio.microsoft.com/support/support-overview-vs).  


## <a name="see-also"></a>Voir aussi
- [Documentation de Visual Studio](https://docs.microsoft.com/visualstudio/)
- [Documentation Azure DevOps](https://docs.microsoft.com/azure/devops/)
- [Documentation Azure](https://docs.microsoft.com/azure/)
- [Documentation Microsoft 365](https://docs.microsoft.com/microsoft-365/)

## <a name="next-steps"></a>Étapes suivantes
- Vous n’avez qu’un ou deux abonnés à ajouter ?  Consultez [Ajouter des utilisateurs uniques](assign-license.md)
- Vous avez besoin d’aide ? Contactez le [Support technique sur l’administration et les abonnements Visual Studio](https://visualstudio.microsoft.com/support/support-overview-vs).

