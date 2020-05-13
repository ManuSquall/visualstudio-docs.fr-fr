---
title: La connexion à Abonnements Visual Studio peut échouer lors de l’utilisation d’alias | Microsoft Docs
author: evanwindom
ms.author: lank
manager: lank
ms.assetid: 97bf7474-c6c2-49b3-b2c9-f1b2808eed1a
ms.date: 03/02/2020
ms.topic: conceptual
description: La connexion peut échouer si des alias ou des noms conviviaux sont utilisés.
ms.openlocfilehash: 0f5ed4fe67dbd863a7ba4c22f10946cbeb1c36b0
ms.sourcegitcommit: f8e3715c64255b476520bfa9267ceaf766bde3b0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/21/2020
ms.locfileid: "79509055"
---
# <a name="signing-into-visual-studio-subscriptions-may-fail-when-using-aliases"></a>La signature d’abonnements Visual Studio peut échouer lorsque vous utilisez des alias
Selon le type de compte utilisé pour se connecter, les abonnements disponibles peuvent ne pas être correctement affichés lors de la connexion à [https://my.visualstudio.com](https://my.visualstudio.com?wt.mc_id=o~msft~docs). Ce cas peut se produire si l’utilisateur emploie des « alias » ou des « noms conviviaux » au lieu de l’identité de connexion à laquelle l’abonnement est affecté. On parle ici d’utilisation d’alias.

## <a name="what-is-aliasing"></a>Qu’est-ce que l’utilisation d’alias ?
L’utilisation d’alias fait référence aux utilisateurs qui emploient des identités différentes pour se connecter à Windows (ou à leur compte Active Directory) et accéder à leur messagerie électronique.

Ainsi, une entreprise peut avoir un service en ligne Microsoft pour les connexions à l’aide d’adresses d’annuaire (par exemple « JohnD@contoso.com »), mais les utilisateurs accèdent à leurs comptes e-mail à l’aide d’alias ou de noms conviviaux (par exemple « John.Doe@contoso.com »). Assurez-vous que vos utilisateurs utilisent l’adresse e-mail « https://manage.visualstudio.com Connect-in » telle qu’indiquée dans le portail d’administration pour accéder à leurs abonnements. 

## <a name="what-are-the-potential-issues"></a>Quels sont les problèmes potentiels?

Selon le type de compte de l’abonné, il peut rencontrer l’un des deux problèmes. 

### <a name="work-or-school-account-upn-mismatch-issue"></a>Problème d’inadéquation du compte de travail ou d’école UPN 
Un décalage UPN peut être rencontré lorsqu’une entreprise dispose d’un répertoire actif mis en place où l’UserPrincipalName (UPN) n’est pas le même que l’adresse SMTP primaire. 

#### <a name="how-to-detect-if-your-sign-in-address-is-impacted-by-a-upn-mismatch"></a>Comment détecter si votre adresse de connexion est affectée par un décalage UPN 

1. Connectez-vous à https://my.visualstudio.com/subscriptions l’aide de l’adresse de connexion mentionnée dans votre e-mail d’affectation d’abonnement.

2. Vérifiez que l’adresse e-mail de connexion indiquée en haut à droite de la page correspond à l’adresse que vous avez utilisée pour vous connecter.  Si ce n’est pas le cas, votre UPN est dépareillé et vous ne serez pas en mesure de consulter votre abonnement. 

> [!div class="mx-imgBorder"]
> ![Connectez-vous à l’adresse e-mail](_img//aliasing/sign-in-email.png)

#### <a name="how-to-fix-a-upn-mismatch"></a>Comment corriger un décalage UPN

1. Accédez au portail Visual Studio Administration Management[https://manage.visualstudio.com](https://manage.visualstudio.com) 

2. Localiser l’abonné ayant le problème d’inadéquation UPN. (La fonction [Filtre](search-license.md) peut faciliter la recherche d’un abonné.)

3. Modifier l’adresse de l’inscription à l’UPN de l’abonné 

0. Enregistrez les modifications 

0. Informez l’abonné de se déconnecter du portail d’abonnés et d’y accéder à nouveau à l’aide de l’UPN 

### <a name="personal-account-aliasing-issue"></a>Question d’alias de compte personnel

Les comptes d’abonnement personnels peuvent également rencontrer des problèmes si l’adresse e-mail utilisée pour se connecter au portail d’abonnements Visual Studio ne correspond pas à l’adresse e-mail associée à l’abonnement. 

#### <a name="how-to-detect-if-your-personal-subscription-account-is-impacted-by-an-aliasing-issue"></a>Comment détecter si votre compte d’abonnement personnel est affecté par un problème d’alias

1. Connectez-vous à[https://my.visualstudio.com/subscriptions](https://my.visualstudio.com/subscriptions)

0. Vérifiez que l’adresse e-mail de connexion indiquée en haut à droite de la page correspond à l’adresse que vous avez utilisée pour vous connecter.  Si l’adresse e-mail signée n’est pas la même que l’adresse e-mail utilisée pour accéder au site Web, il y a un conflit entre votre compte et l’alias.

#### <a name="how-to-fix-an-alias-issue"></a>Comment résoudre un problème d’alias

La plate-forme Visual Studio donne la priorité au pseudonyme principal pour afficher les détails de l’abonnement. 

1. Allez **gérer comment vous vous connectez à Microsoft**. Connectez-vous à votre compte Microsoft si vous êtes invité. 

2. Sous les pseudonymes de compte, **sélectionnez Faites primaire** à côté de l’adresse e-mail utilisée pour attribuer l’abonnement. 

> [!div class="mx-imgBorder"]
> ![Définissez l’adresse e-mail principale](_img//aliasing/account-aliases.png)

3. Déconnectez-vous du portail d’abonnements Visual Studio (https://my.visualstudio.com) 

4. Connectez-vous à l’aide du compte utilisé pour attribuer l’abonnement qui doit maintenant être configuré comme alias principal. 

## <a name="preventing-aliasing-issues"></a>Prévention des problèmes d’alias

En tant qu’administrateur, il existe deux options pour s’assurer que vos abonnés ont une expérience de connexion réussie sur [https://my.visualstudio.com](https://my.visualstudio.com?wt.mc_id=o~msft~docs).
- La première option (recommandée) est de tirer parti du compte d’annuaire https://my.visualstudio.comen tant que connecteur pour le portail Visual Studio Subscriptions à .  
- La deuxième option (moins sécurisée) consiste à permettre à vos abonnés de se connecter à l’aide d’une adresse e-mail différente de leur adresse e-mail d’annuaire.

Ces deux options sont configurées dans le portail d’administration en remplissant les étapes suivantes :  
1. Connectez-vous à[https://manage.visualstudio.com](https://manage.visualstudio.com) 

0. Si vous modifiez un seul utilisateur, sélectionnez cet utilisateur dans la table et cliquez à droite pour modifier. Cela ouvrira un panneau où vous pouvez modifier l’adresse e-mail de connexion. Effectuez les mises à jour nécessaires dans le champ d’adresses e-mail connectatif. Cliquez sur enregistrer et les modifications entreront en vigueur.  

0. Si vous avez besoin d’apporter ces modifications à une grande quantité d’utilisateurs, vous pouvez utiliser la fonction de modification en vrac. Lisez [l’édition de plusieurs abonnés à l’aide de l’article de modification en vrac](https://docs.microsoft.com/visualstudio/subscriptions/edit-license#edit-multiple-subscribers-using-bulk-edit) pour plus d’informations.

> [!NOTE]
> Pour les changements individuels et en vrac, les abonnés recevront un e-mail avec des instructions que leur adresse e-mail de connexion a changé et ils devront se connecter à l’aide de l’adresse e-mail mise à jour. Il est également important de noter que si l’abonné a déjà activé les avantages sous l’autre adresse d’inscription, il devra continuer à utiliser l’autre adresse d’inscription pour y accéder.  

## <a name="see-also"></a>Voir aussi
- [Documentation Visual Studio](https://docs.microsoft.com/visualstudio/)
- [Documentation Azure DevOps](https://docs.microsoft.com/azure/devops/)
- [Documentation Azure](https://docs.microsoft.com/azure/)
- [Documentation Microsoft 365](https://docs.microsoft.com/microsoft-365/)


## <a name="next-steps"></a>Étapes suivantes
En savoir plus sur la gestion des abonnements Visual Studio.
- [Attribuer des abonnements individuels](assign-license.md)
- [Attribuer plusieurs abonnements](assign-license-bulk.md)
- [Modifier des abonnements](edit-license.md)
- [Déterminer l’utilisation maximale](maximum-usage.md)


