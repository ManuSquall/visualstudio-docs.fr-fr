---
title: Attribuer des licences à des groupes d’utilisateurs pour des abonnements Visual Studio | Microsoft Docs
author: evanwindom
ms.author: v-evwin
manager: cabuschl
ms.assetid: c2853359-18fd-4be4-97a6-02230c862f92
ms.date: 03/21/2021
ms.topic: how-to
description: Découvrez comment les administrateurs peuvent attribuer des licences à plusieurs abonnés à l’aide de la fonctionnalité d’ajout en bloc ou de groupes de Microsoft Azure Active Directory
ms.openlocfilehash: 389eb3a578b0b025995c0cd60613d5bcce2e1a9f
ms.sourcegitcommit: dd2fc6e03a789c044f8438096b8f112e4dba5557
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/06/2021
ms.locfileid: "108640997"
---
# <a name="assign-subscriptions-to-multiple-users"></a>Attribuer des abonnements à plusieurs utilisateurs
Le portail d’administration des abonnements vous permet d’ajouter des utilisateurs un à la fois ou dans des grands groupes.  Pour ajouter des utilisateurs individuels, consultez [Ajouter des utilisateurs uniques](assign-license.md).

Pour ajouter des groupes d’utilisateurs importants, vous pouvez utiliser la fonctionnalité d’ajout en bloc ou, si votre organisation utilise Microsoft Azure Active Directory (Azure AD), vous pouvez utiliser des groupes de Azure AD. Cet article explique le processus pour les deux options.  Regardez cette vidéo ou lisez la suite pour en savoir plus sur la fonctionnalité d’ajout en bloc. 

<br>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4vxNq]

## <a name="use-bulk-add-to-assign-subscriptions"></a>Utiliser l’ajout en bloc pour affecter des abonnements
1. Connectez-vous au portail d’administration des abonnements Visual Studio à l’adresse <https://manage.visualstudio.com> .

1. Pour ajouter plusieurs abonnés à la fois, accédez à l’onglet **gérer les abonnés** . Choisissez l’onglet **Ajouter** , puis choisissez **Ajouter en bloc** dans la liste déroulante.  

1. L’ajout en bloc utilise un modèle Microsoft Excel pour télécharger les informations de l’abonné. Dans la boîte de dialogue Télécharger plusieurs abonnés, sélectionnez **Télécharger** pour télécharger le modèle.
   > [!div class="mx-imgBorder"]
   > ![Télécharger le modèle Excel pour charger plusieurs abonnés](media/download-template-upload-subscribers.png "Téléchargez le modèle Excel vide pour commencer le processus d’attribution en bloc.")
   >
   > [!NOTE]
   > Téléchargez toujours la dernière version du modèle. L’utilisation d’une version antérieure peut faire échouer le chargement en bloc.

1. Dans la feuille de calcul Excel, renseignez les champs avec les informations relatives aux utilisateurs auxquels vous souhaitez attribuer des abonnements. (La *référence* est un champ facultatif.) Enregistrez le fichier localement une fois que vous avez terminé.

    > [!NOTE]
    > L’un des champs du modèle permet aux administrateurs d’activer ou de désactiver la capacité des abonnés à télécharger des logiciels.  La désactivation des téléchargements désactive également leur accès aux clés de produit.

   Pour faciliter le chargement, respectez les bonnes pratiques suivantes :

    - Vérifiez que les champs de formulaire ne contiennent pas de virgules.
    - Supprimez les espaces avant et après les champs de formulaire.
    - Assurez-vous que les noms d’utilisateur ne contiennent pas d’espace superflu dans les noms ou prénoms composés (par exemple, si une personne porte le prénom composé « Maggie May », il doit être entré sous la forme « MaggieMay », car le système ne supprime pas l’espace superflu).
    - Assurez-vous que tous les champs obligatoires sont remplis. 
    - Vérifiez la colonne **message d’erreur** .  Si des erreurs sont répertoriées, résolvez-les avant de tenter de charger le fichier. 

1. Revenez au portail d’administration des abonnements Visual Studio. Dans la boîte de dialogue **Télécharger plusieurs abonnés** , sélectionnez **Parcourir**.
   > [!div class="mx-imgBorder"]
   > ![Accéder à votre modèle enregistré pour charger plusieurs abonnés](media/bulk-add-browse-saved-template.png "Vous pouvez accéder à l’emplacement du fichier ou le glisser-déplacer dans cette boîte de dialogue.")

1. Accédez au fichier Excel que vous avez enregistré, puis sélectionnez **OK**.
   > [!div class="mx-imgBorder"]
   > ![Charger le modèle Excel pour charger plusieurs abonnés](media/bulk-upload-subscribers.png "Le modèle avec vos données s’affiche ici.  Sélectionnez OK pour commencer le chargement.")

    Une boîte de dialogue de progression du chargement s’affiche.

    Si le modèle contient des erreurs, le chargement échoue et les erreurs rencontrées s’affichent pour vous aider à corriger le modèle. Réessayez ensuite le chargement en bloc.
   > [!div class="mx-imgBorder"]
   > ![Message d’erreur si le chargement de plusieurs abonnés échoue](_img/assign-license-bulk/bulk-add-upload-failure.png "Ce message s’affiche si le fichier que vous avez chargé contient des erreurs.  Résolvez les erreurs et effectuez à nouveau le processus d’ajout en bloc.")

   Si vous rencontrez un échec, procédez comme suit :
   1. Ouvrez le fichier Excel que vous avez créé, corrigez les problèmes, puis enregistrez le fichier.
   0. Revenez au portail d’administration et ignorez le message d’erreur.
   0. Choisissez **Ajouter**.
   0. Sélectionnez **Ajout en bloc**.
   0. Étant donné que vous avez déjà enregistré le fichier Excel, vous n’avez pas besoin de télécharger le modèle.  Sélectionnez **Parcourir**, localisez le fichier que vous venez d’enregistrer, puis sélectionnez **ouvrir**.
   0. Sélectionnez **OK**.


    Quand le chargement est réussi, vous voyez s’afficher la liste des abonnés et un message de confirmation.
   > [!div class="mx-imgBorder"]
   > ![Message de confirmation si le chargement de plusieurs abonnés réussit](_img/assign-license-bulk/bulk-add-upload-success.png "Lorsque le téléchargement se termine correctement, vous recevez un message de confirmation.")

## <a name="use-azure-active-directory-groups-to-assign-subscriptions"></a>Utiliser des groupes de Azure Active Directory pour affecter des abonnements 
Grâce à cette fonctionnalité, il est facile de rester au-dessus de vos affectations d’abonnement. Vous pouvez ajouter Azure Active Directory groupes de sécurité dans le portail d’administration des abonnements, ce qui garantit que tous les individus du groupe se voient attribuer un abonnement. Et pour faciliter la tâche, lorsque les individus sortent de votre organisation et sont supprimés de Azure Active Directory, leur accès aux abonnements est également supprimé. 


> [!IMPORTANT]
>
> Les limitations suivantes s’appliquent à l’utilisation de groupes de Azure AD pour l’ajout d’abonnés :
> - L’administrateur doit être membre du client AAD lors de l’ajout initial d’un groupe au portail d’administration.  Une fois le groupe ajouté, les modifications apportées à l’appartenance aux groupes ne nécessitent pas d’intervention de l’administrateur. 
> - Les groupes doivent contenir au moins un membre.  Les groupes vides ne sont pas pris en charge.
> - Tous les utilisateurs doivent se trouver au niveau supérieur du groupe.  Les groupes imbriqués ne sont pas pris en charge.
> - Seuls les accords approuvés sont pris en charge. (Seuls les accords qui peuvent « surattribuer » des abonnements sont approuvés.)
> - Tous les membres du groupe doivent avoir une adresse de messagerie associée à leur compte Azure AD.
> - Les adresses e-mail distinctes pour les notifications ne sont pas prises en charge pour les abonnements ajoutés à l’aide de groupes de Azure AD.  

Regardez cette vidéo ou lisez la suite pour en savoir plus sur l’ajout d’abonnés à l’aide de la fonctionnalité de groupe de Azure Active Directory. 
<br>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4rvvW]

1. Connectez-vous au portail d’administration des abonnements Visual Studio à l’adresse [https://manage.visualstudio.com](https://manage.visualstudio.com) .

2. Pour ajouter plusieurs abonnés à la fois, accédez à l’onglet **gérer les abonnés** .

3. Choisissez l’onglet **Ajouter** , puis sélectionnez **Azure Active Directory groupe** dans la liste déroulante.  

   > [!div class="mx-imgBorder"]
   > ![Choisir l’ajout en bloc à l’aide de Azure AD](_img/assign-license-bulk/bulk-add-aad.png "Choisissez la fonctionnalité Ajouter en bloc à l’aide de Azure AD pour extraire les abonnés de votre groupe de Azure Active Directory.")

4. Commencez par entrer le nom du groupe de Azure AD que vous souhaitez ajouter dans le champ de formulaire. Cela permet de rechercher les groupes de Azure AD disponibles au sein de votre organisation. 

5. Lorsque vous sélectionnez le groupe, le champ est automatiquement renseigné avec le nom du groupe. Vous avez la possibilité d’afficher les utilisateurs de ce groupe avant de les ajouter. Ensuite, vous pouvez choisir le niveau d’abonnement, les droits de téléchargement et les préférences de communication pour le groupe. Si vous le souhaitez, vous pouvez ajouter des détails dans le champ de référence. 

   > [!div class="mx-imgBorder"]
   > ![Choisir votre groupe de Azure AD](_img/assign-license-bulk/bulk-add-aad-details.png "Choisissez le nom de votre groupe de Azure AD pour ajouter des abonnés à ce groupe.")

6. Sélectionnez **Ajouter** , puis **confirmer**. 

7. Pour afficher le groupe ajouté, faites défiler la liste des utilisateurs vers le bas.  

8. Sélectionnez **afficher les abonnés** pour afficher les membres du groupe. Vous pouvez afficher des détails sur les abonnés dans le groupe, mais vous ne pouvez pas apporter de modifications aux abonnés ou aux abonnements auxquels ils sont affectés.    

> [!NOTE]
> Si vous avez déjà attribué des abonnements individuellement à des utilisateurs qui sont ajoutés par la suite dans le cadre d’un groupe de Azure AD, ils sont ajoutés dans le cadre du groupe et ne sont plus répertoriés individuellement. Toutefois, si l’abonnement individuel est destiné à un niveau d’abonnement différent, il aura deux abonnements.  Exemple : si un utilisateur dispose d’un abonnement Visual Studio Professional individuel et s’il est membre d’un groupe auquel vous affectez des abonnements Visual Studio Enterprise, il disposera des deux.  
>
> Si vous supprimez un abonné d’un groupe de Azure Active Directory auquel des abonnements ont été attribués, la mise à jour peut prendre jusqu’à 24 heures pour être reflétée dans le portail d’administration. 


## <a name="frequently-asked-questions"></a>Forum aux questions
### <a name="q-can-i-choose-multiple-subscription-levels-to-be-assigned-within-an-azure-ad-group"></a>Q : puis-je choisir plusieurs niveaux d’abonnement à affecter au sein d’un groupe de Azure AD ? 
R : non--tous les membres du groupe reçoivent le même abonnement. 

### <a name="q-can-i-edit-subscriber-details-of-individuals-added-in-an-azure-ad-group"></a>Q : puis-je modifier les détails de l’abonné des personnes ajoutées à un groupe de Azure AD ?  
R : non--pour modifier les informations d’un abonné individuel, vous devez les supprimer du groupe de sécurité Azure AD et leur attribuer un abonnement individuellement.  

### <a name="q-why-cant-i-see-the-option-to-use-azure-active-directory-groups-to-add-subscribers"></a>Q : pourquoi ne puis-je pas voir l’option permettant d’utiliser les groupes de Azure Active Directory pour ajouter des abonnés ?
R : la fonctionnalité n’est actuellement disponible que pour les organisations avec des contrats de confiance.  Sélectionnez le bouton **Détails** pour afficher les informations de votre contrat.

   > [!div class="mx-imgBorder"]
   > ![Cliquez sur le bouton Détails](_img/assign-license-bulk/bulk-add-agreement.png "Cliquez sur le bouton Détails pour afficher le type d’accord que vous avez")

### <a name="q-i-added-someone-to-my-azure-ad-security-group-but-i-dont-see-them-added-in-the-subscriptions-administration-portal-and-they-dont-have-a-subscription-why-not"></a>Q : J’ai ajouté une personne à mon Azure AD groupe de sécurité, mais je ne l’ai pas ajoutée dans le portail d’administration des abonnements et il n’y a pas d’abonnement. Pourquoi cela ne fonctionne-t-il pas ?  
R : selon la façon dont votre organisation a configuré Azure AD, vous pouvez constater des retards jusqu’à 24 heures avant l’ajout de l’utilisateur. S’il s’agit d’une durée supérieure à 24 heures, consultez la [prise en charge de l’administration et des abonnements Visual Studio](https://my.visualstudio.com/gethelp).  

## <a name="see-also"></a>Voir aussi
- [Documentation de Visual Studio](/visualstudio/)
- [Documentation Azure DevOps](/azure/devops/)
- [Documentation Azure](/azure/)
- [Documentation Microsoft 365](/microsoft-365/)

## <a name="next-steps"></a>Étapes suivantes
- Vous n’avez qu’un ou deux abonnés à ajouter ?  Consultez [Ajouter des utilisateurs uniques](assign-license.md)
- Vous avez besoin d’aide ? Contactez le support pour les [abonnements](https://aka.ms/vsadminhelp).