---
title: La connexion à Abonnements Visual Studio peut échouer lors de l’utilisation d’alias | Microsoft Docs
author: evanwindom
ms.author: lank
manager: lank
ms.date: 02/14/2020
ms.topic: conceptual
description: La connexion peut échouer si des alias ou des noms conviviaux sont utilisés.
ms.openlocfilehash: dff48852e566522ad01ee07bd46cda72b8e1e249
ms.sourcegitcommit: 68f893f6e472df46f323db34a13a7034dccad25a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/15/2020
ms.locfileid: "77276621"
---
# <a name="signing-in-to-visual-studio-subscriptions-may-fail-when-using-aliases"></a>La connexion à Abonnements Visual Studio peut échouer lors de l’utilisation d’alias
Selon le type de compte utilisé pour la connexion, les abonnements disponibles peuvent ne pas s’afficher correctement lors de la connexion à [https://my.visualstudio.com](https://my.visualstudio.com?wt.mc_id=o~msft~docs). Ce cas peut se produire si l’utilisateur emploie des « alias » ou des « noms conviviaux » au lieu de l’identité de connexion à laquelle l’abonnement est affecté. On parle ici d’utilisation d’alias.

## <a name="what-is-aliasing"></a>Qu’est-ce que l’utilisation d’alias ?
L’utilisation d’alias fait référence aux utilisateurs qui emploient des identités différentes pour se connecter à Windows (ou à leur compte Active Directory) et accéder à leur messagerie électronique.

Ainsi, une entreprise peut avoir un service en ligne Microsoft pour les connexions à l’aide d’adresses d’annuaire (par exemple « olivia@contoso.com »), mais les utilisateurs accèdent à leurs comptes e-mail à l’aide d’alias ou de noms conviviaux (par exemple « OliviaG@contoso.com »). Assurez-vous que vos utilisateurs se connectent à l’aide de l' « adresse de messagerie de connexion », comme indiqué dans le portail d’administration des abonnements Visual Studio à https://manage.visualstudio.com pour accéder à leurs abonnements.

## <a name="as-an-administrator-what-options-do-i-have"></a>En tant qu’administrateur, quelles options ai-je à ma disposition ?

Selon le type de compte de l’abonné, recherchez la solution applicable ci-dessous :

### <a name="work-or-school-account-upn-mismatch-issue"></a>Problème d’incompatibilité UPN du compte professionnel ou scolaire

Une incompatibilité de nom d’utilisateur principal (UPN) peut être rencontrée lorsqu’un compnay a une configuration de lieu de service Active où l’UPN n’est pas le même que l’adresse SMTP principale. 

#### <a name="how-to-detect-if-a-users-sign-in-address-has-a-upn-mismatch"></a>Comment détecter si l’adresse de connexion d’un utilisateur a une incompatibilité UPN

Demander à l’utilisateur d’effectuer les étapes suivantes :

1. Connectez-vous à https://my.visualstudio.com à l’aide de l’adresse de connexion mentionnée dans l’e-mail de l’attribution d’abonnement.  

    > [!NOTE]
    > S’ils n’ont pas de courrier électronique d’affectation d’abonnement, vous pouvez les renvoyer à partir du portail d’administration.  

2. Cliquez sur l’onglet **Abonnements**.
3. Vérifiez que l’adresse de messagerie s’affiche dans l’angle supérieur droit où elle indique « vous êtes connecté en tant que... » est identique à l’adresse de messagerie de connexion dans l’e-mail de l’attribution de l’abonnement.  Si ce n’est pas le cas, ils ne pourront pas accéder aux avantages de leur abonnement. 

   > [!div class="mx-imgBorder"]
   > page abonnements ![](_img/aliasing/aliasing-subscriptions-page.png)

#### <a name="how-to-correct-the-upn-mismatch"></a>Comment corriger l’incompatibilité UPN

1. Accédez au portail de gestion de l’administration de Visual Studio à l’adresse https://manage.visualstudio.com 

2. Recherchez l’utilisateur qui rencontre le problème d’incompatibilité UPN.  La fonctionnalité de [filtre](search-license.md) peut faciliter cette opération si vous avez beaucoup d’abonnements. 

3. Remplacez l’adresse E-mail de connexion par l’UPN de l’utilisateur.

4. Enregistrez les modifications 

5. Demandez à l’utilisateur de se déconnecter du portail de l’abonné, puis de vous reconnecter à l’aide de l’UPN.   

### <a name="personal-account-aliasing-issue"></a>Problème d’alias de compte personnel

Les problèmes d’alias peuvent également affecter les comptes personnels. 

#### <a name="how-to-detect-if-a-personal-account-has-an-aliasing-issue"></a>Comment détecter si un compte personnel présente un problème d’alias

1. Connectez-vous https://my.visualstudio.com.

2. Cliquez sur l’onglet **abonnements** et vérifiez l’adresse à laquelle vous êtes connecté. 

3. Si l’adresse e-mail de connexion n’est pas la même que l’adresse de messagerie utilisée pour accéder au site Web, il y a un conflit entre votre compte et l’alias. 

#### <a name="how-to-fix-a-personal-account-aliasing-issue"></a>Comment résoudre un problème d’alias de compte personnel

La plateforme d’abonnements Visual Studio donne la priorité à l’alias principal pour afficher les détails de l’abonnement.  Pour résoudre le problème, vous devez créer un alias de messagerie différent de votre alias principal pour la connexion. 

1. Accédez à [gérer la façon dont vous vous connectez à Microsoft](https://go.microsoft.com/fwlink/p/?linkid=842796).
2. Connectez-vous à votre compte Microsoft si vous y êtes invité. 
3. Sous alias de comptes, sélectionnez **rendre principal** en regard de l’adresse de messagerie utilisée pour attribuer l’abonnement. 
4. Sous alias de comptes, sélectionnez rendre principal en regard de l’adresse de messagerie utilisée pour attribuer l’abonnement. 
5. Déconnectez-vous du portail des abonnés Visual Studio (https://my.visualstudio.com) 
6. Accédez de nouveau au portail à l’aide du nouvel alias principal. 

### <a name="ensure-a-successful-experience-for-your-users"></a>Garantir une expérience réussie pour vos utilisateurs

En tant qu’administrateur, il existe deux options pour garantir que vos abonnés ont une expérience de connexion réussie sur https://my.visualstudio.com. 

- La première option (recommandée) consiste à utiliser le compte d’annuaire comme adresse de connexion sur https://manage.visualstudio.com.
- La deuxième option, qui est moins sécurisée, la deuxième option (moins sécurisée) est de permettre à vos abonnés de se connecter à l’aide d’une autre adresse e-mail que l’adresse de messagerie de leur annuaire.

Les deux options sont configurées dans le portail d’administration en procédant comme suit :

1. Connectez-vous https://manage.visualstudio.com 

2. Si vous modifiez un seul utilisateur, sélectionnez cet utilisateur dans la table et cliquez avec le bouton droit pour le modifier. Cela ouvre un panneau dans lequel vous pouvez modifier l’adresse e-mail de connexion.  

3. Effectuez les mises à jour nécessaires dans le champ adresse de messagerie de connexion. 

4. Cliquez sur Enregistrer pour appliquer les modifications.  
Si vous devez apporter ces modifications à une grande quantité d’utilisateurs, vous pouvez utiliser la fonctionnalité d’édition en bloc. Pour plus d’informations sur ce processus, consultez la section **modifier plusieurs abonnés à l’aide de la modification en bloc** de notre article [modifier les abonnements]] (edit-License.MD).  

## <a name="next-steps"></a>Étapes suivantes
En savoir plus sur la gestion des abonnements Visual Studio.
- [Affecter des abonnements individuels](assign-license.md)
- [Attribuer plusieurs abonnements](assign-license-bulk.md)
- [Modifier des abonnements](edit-license.md)
- [Supprimer des abonnements](delete-license.md)
- [Déterminer l’utilisation maximale](maximum-usage.md)

## <a name="see-also"></a>Voir aussi
- [Documentation de Visual Studio](/visualstudio/)
- [Documentation Azure DevOps](/azure/devops/)
- [Documentation Azure](/azure/)
- [Documentation Microsoft 365](/microsoft-365/)
