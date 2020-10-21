---
title: La connexion à Abonnements Visual Studio peut échouer lors de l’utilisation d’alias | Microsoft Docs
author: evanwindom
ms.author: lank
manager: lank
ms.assetid: 97bf7474-c6c2-49b3-b2c9-f1b2808eed1a
ms.date: 10/20/2020
ms.topic: conceptual
description: La connexion peut échouer si des alias ou des noms conviviaux sont utilisés.
ms.openlocfilehash: c5c211cd674e86edc4528e6e2c5e75bd5b02132d
ms.sourcegitcommit: 6b62e09026b6f1446187c905b789645f967a371c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/21/2020
ms.locfileid: "92298184"
---
# <a name="signing-into-visual-studio-subscriptions-may-fail-when-using-aliases"></a>La connexion à des abonnements Visual Studio peut échouer lors de l’utilisation d’alias
Selon le type de compte utilisé pour la connexion, les abonnements disponibles peuvent ne pas s’afficher correctement lors de la connexion à [https://my.visualstudio.com](https://my.visualstudio.com?wt.mc_id=o~msft~docs) . Ce cas peut se produire si l’utilisateur emploie des « alias » ou des « noms conviviaux » au lieu de l’identité de connexion à laquelle l’abonnement est affecté. On parle ici d’utilisation d’alias.

## <a name="what-is-aliasing"></a>Qu’est-ce que l’utilisation d’alias ?
L’utilisation d’alias fait référence aux utilisateurs qui emploient des identités différentes pour se connecter à Windows (ou à leur compte Active Directory) et accéder à leur messagerie électronique.

Ainsi, une entreprise peut avoir un service en ligne Microsoft pour les connexions à l’aide d’adresses d’annuaire (par exemple « JohnD@contoso.com »), mais les utilisateurs accèdent à leurs comptes e-mail à l’aide d’alias ou de noms conviviaux (par exemple « John.Doe@contoso.com »). Assurez-vous que vos utilisateurs utilisent la « adresse E-mail de connexion », comme indiqué dans le portail https://manage.visualstudio.com d’administration de pour accéder à leurs abonnements. 

## <a name="what-are-the-potential-issues"></a>Quels sont les problèmes potentiels ?

En fonction du type de compte de l’abonné, ils peuvent rencontrer l’un des deux problèmes. 

### <a name="work-or-school-account-upn-mismatch-issue"></a>Problème d’incompatibilité UPN du compte professionnel ou scolaire 
Une incompatibilité de nom UPN peut être rencontrée quand une société a une Active Directory configurée où le UserPrincipalName (UPN) n’est pas identique à l’adresse SMTP principale. 

#### <a name="how-to-detect-if-your-sign-in-address-is-impacted-by-a-upn-mismatch"></a>Comment détecter si votre adresse de connexion est affectée par une incompatibilité UPN 

1. Connectez https://my.visualstudio.com/subscriptions -vous à à l’aide de l’adresse de connexion mentionnée dans votre e-mail d’affectation d’abonnement.

2. Cliquez sur votre nom dans le coin supérieur droit de la page.  Votre profil s’ouvre.  Vérifiez que l’adresse e-mail de connexion indiquée dans votre profil correspond à celle que vous avez utilisée pour vous connecter.  Si ce n’est pas le cas, votre nom d’utilisateur principal ne correspond pas et vous ne pourrez pas afficher votre abonnement. 

> [!div class="mx-imgBorder"]
> ![Adresse de messagerie de connexion](_img//aliasing/sign-in-email.png "Assurez-vous que l’adresse de messagerie affichée dans votre profil correspond à celle que vous utilisez pour vous connecter.")

#### <a name="how-to-fix-a-upn-mismatch"></a>Correction d’une incompatibilité UPN

1. Accéder au portail de gestion de l’administration de Visual Studio [https://manage.visualstudio.com](https://manage.visualstudio.com) 

2. Recherchez l’abonné présentant un problème d’incompatibilité de nom d’utilisateur principal. (La fonctionnalité de [filtre](search-license.md) peut faciliter la recherche d’un abonné.)

3. Remplacer l’adresse de messagerie de connexion par l’UPN de l’abonné 

0. Enregistrez les modifications 

0. Informer l’abonné à se déconnecter du portail de l’abonné et à y accéder à nouveau à l’aide de l’UPN 

### <a name="personal-account-aliasing-issue"></a>Problème d’alias de compte personnel

Les comptes d’abonnement personnels peuvent également rencontrer des problèmes si l’adresse de messagerie utilisée pour se connecter au portail des abonnements Visual Studio ne correspond pas à l’adresse de messagerie associée à l’abonnement. 

#### <a name="how-to-detect-if-your-personal-subscription-account-is-impacted-by-an-aliasing-issue"></a>Comment détecter si votre compte d’abonnement personnel est affecté par un problème d’alias

1. Connectez-vous à [https://my.visualstudio.com/subscriptions](https://my.visualstudio.com/subscriptions)

0. Vérifiez que l’adresse e-mail de connexion indiquée en haut à droite de la page correspond à celle que vous avez utilisée pour vous connecter.  Si l’adresse e-mail de connexion n’est pas la même que l’adresse de messagerie utilisée pour accéder au site Web, il y a un conflit entre votre compte et l’alias.

#### <a name="how-to-fix-an-alias-issue"></a>Comment résoudre un problème d’alias

La plateforme Visual Studio donne la priorité à l’alias principal pour afficher les détails de l’abonnement. 

1. Accédez à **gérer la façon dont vous vous connectez à Microsoft**. Connectez-vous à votre compte Microsoft si vous y êtes invité. 

2. Sous alias de comptes, sélectionnez **rendre principal** en regard de l’adresse de messagerie utilisée pour attribuer l’abonnement. 

> [!div class="mx-imgBorder"]
> ![Définir l’adresse de messagerie principale](_img//aliasing/account-aliases.png "Utilisez le lien créer un lien principal pour choisir l’alias principal de vos abonnements.")

3. Déconnectez-vous du portail des abonnements Visual Studio (https://my.visualstudio.com) 

4. Reconnectez-vous à l’aide du compte utilisé pour attribuer l’abonnement qui doit maintenant être configuré en tant qu’alias principal. 

## <a name="preventing-aliasing-issues"></a>Prévention des problèmes d’alias

En tant qu’administrateur, il existe deux options pour garantir que vos abonnés ont une expérience de connexion réussie sur [https://my.visualstudio.com](https://my.visualstudio.com?wt.mc_id=o~msft~docs) .
- La première option (recommandée) consiste à utiliser le compte d’annuaire comme connexion pour le portail des abonnements Visual Studio à l’adresse https://my.visualstudio.com .  
- La deuxième option (moins sécurisée) est de permettre à vos abonnés de se connecter à l’aide d’une adresse de messagerie différente de l’adresse de messagerie de leur annuaire.

Ces deux options sont configurées dans le portail d’administration en procédant comme suit :  
1. Se connecter [https://manage.visualstudio.com](https://manage.visualstudio.com) 

0. Si vous modifiez un seul utilisateur, sélectionnez cet utilisateur dans la table et cliquez avec le bouton droit pour le modifier. Cela ouvre un panneau dans lequel vous pouvez modifier l’adresse e-mail de connexion. Effectuez les mises à jour nécessaires dans le champ adresse de messagerie de connexion. Cliquez sur Enregistrer pour appliquer les modifications.  

0. Si vous devez apporter ces modifications à une grande quantité d’utilisateurs, vous pouvez utiliser la fonctionnalité d’édition en bloc. Pour plus d’informations, consultez l’article [modifier plusieurs abonnés à l’aide de la modification en bloc](./edit-license.md#edit-multiple-subscribers-using-bulk-edit) .

> [!NOTE]
> Pour les modifications individuelles et en bloc, les abonnés reçoivent un message électronique contenant des instructions indiquant que leur adresse e-mail de connexion a changé et qu’ils doivent se connecter à l’aide de l’adresse e-mail mise à jour. Il est également important de noter que si l’abonné a déjà activé les avantages sous l’autre adresse de connexion, il doit continuer à utiliser l’autre adresse de connexion pour y accéder.  

## <a name="see-also"></a>Voir aussi
- [Documentation de Visual Studio](/visualstudio/)
- [Documentation Azure DevOps](/azure/devops/)
- [Documentation Azure](/azure/)
- [Documentation Microsoft 365](/microsoft-365/)


## <a name="next-steps"></a>Étapes suivantes
En savoir plus sur la gestion des abonnements Visual Studio.
- [Affecter des abonnements individuels](assign-license.md)
- [Attribuer plusieurs abonnements](assign-license-bulk.md)
- [Modifier des abonnements](edit-license.md)
- [Déterminer l’utilisation maximale](maximum-usage.md)