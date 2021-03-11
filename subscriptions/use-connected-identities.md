---
title: Utilisation des identités connectées dans les abonnements Visual Studio | Microsoft Docs
author: evanwindom
ms.author: v-evwin
manager: lank
ms.assetid: 50ce0445-ef1a-4e92-b9d0-aebb2155a111
ms.date: 02/19/2021
ms.topic: conceptual
robots: noindex, nofollow
description: En savoir plus sur l’utilisation des comptes Azure Active Directory et des identités Microsoft connectés
ms.openlocfilehash: 9625774cbf5338750034f1f288bd2ada0aa9fc33
ms.sourcegitcommit: f9ed9c4c6c166ef9826feb21dcb9c4d47ed14e1a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/10/2021
ms.locfileid: "102607117"
---
# <a name="how-to-use-connected-identities-in-visual-studio-subscriptions"></a>Comment utiliser les identités connectées dans les abonnements Visual Studio
Si vous recevez un abonnement Visual Studio par le biais de votre entreprise ou établissement scolaire, et que vous utilisez votre compte Microsoft (MSA) pour vous connecter, votre administrateur d’abonnements peut connecter votre MSA à votre identité dans le Azure Active Directory de votre organisation (Azure AD).  Cela modifiera la façon dont vous accédez à certains des avantages inclus dans votre abonnement. 

## <a name="overview-of-connected-ids"></a>Vue d’ensemble des ID connectés
Les organisations évoluent de plus en plus vers les identités basées sur les Azure AD pour offrir une sécurité et une prise en charge améliorées pour la gestion automatisée des abonnements.  Si votre abonnement utilise un MSA comme une @outlook.com autre adresse de messagerie personnelle, votre administrateur peut modifier votre courrier électronique de connexion à votre identité Azure ad.  Cela modifiera la façon de se connecter au portail de l’abonné à l’adresse, https://my.visualstudio.com mais peut ne pas modifier la façon dont vous accédez à tous vos avantages.  

Si votre administrateur connecte vos identités MSA et Azure AD, vous recevez un message électronique vous informant que vous pouvez commencer à accéder à votre abonnement Visual Studio avec votre identité Azure AD au lieu de votre MSA. 

## <a name="how-to-access-benefits-using-azure-ad-identities"></a>Comment accéder aux avantages à l’aide des identités Azure AD
Une fois que votre administrateur a connecté votre MSA à votre identité Azure AD, vous devez vous connecter au portail de l’abonné auprès de https://my.visualstudio.com avec votre identité Azure AD pour accéder aux avantages qui s’appuient sur Azure ad.  À savoir :
- Environnement IDE de Visual Studio
- Azure DevOps
- Crédit individuel Azure DevTest

## <a name="how-to-access-benefits-using-your-msa"></a>Comment accéder aux avantages à l’aide de votre MSA
Pour la plupart des avantages offerts par les abonnements Visual Studio tels que Pluralsight, LinkedIn, CloudPilot et d’autres, vous créez en fait des comptes d’utilisateur sur les sites Web des partenaires.  Pour ces comptes, vous devez continuer à utiliser l’identité que vous avez utilisée lors de la création du compte.  Par exemple, si vous avez activé votre avantage Pluralsight à l’aide de votre MSA, vous devez continuer à utiliser votre MSA lors de la formation à Pluralsight, quelle que soit l’identité que vous utilisez pour vous connecter au portail de l’abonné.  

## <a name="use-an-alternate-identity-to-access-your-subscription"></a>Utiliser une autre identité pour accéder à votre abonnement
L’ajout d’un compte secondaire à votre abonnement Visual Studio vous permet d’accéder aux avantages de cet abonnement, par exemple Azure DevOps et Azure, avec une autre identité que celle à laquelle l’abonnement est affecté. Dans le passé, cette fonctionnalité était disponible uniquement si votre abonnement VS (Visual Studio) était affecté à un compte MSA (compte Microsoft). Nous avons étendu cette fonctionnalité aux comptes professionnels ou scolaires dans Azure AD (Azure Active Directory).  Pour plus d’informations sur l’utilisation de comptes secondaires, consultez notre article sur les [autres identités](vs-alternate-identity.md) . 

## <a name="frequently-asked-questions"></a>Forum aux questions
### <a name="q-how-can-i-contact-my-admin-about-this"></a>Q : Comment puis-je contacter mon administrateur à ce sujet ?
R : pour plus d’informations sur la façon de contacter votre administrateur, consultez notre article [contacter l’administrateur de votre abonnement](contact-my-admin.md) .  

### <a name="q-im-an-admin--how-do-i-use-this"></a>Q : je suis administrateur.  Comment faire l’utiliser ?
R : l’implémentation d’identités connectées est simple.  Pour plus d’informations, lisez [cet article](personal-email-sign-ins.md). 

## <a name="resources"></a>Ressources
- Pour obtenir de l’aide sur les ventes, les abonnements, les comptes et la facturation des abonnements Visual Studio, consultez [prise en charge des abonnements](https://aka.ms/vssubscriberhelp)Visual Studio.

## <a name="see-also"></a>Voir aussi
- [Documentation de Visual Studio](/visualstudio/)
- [Documentation Azure DevOps](/azure/devops/)
- [Documentation Azure](/azure/)
- [Documentation Microsoft 365](/microsoft-365/)

## <a name="next-steps"></a>Étapes suivantes
Une fois que votre administrateur a connecté vos comptes Azure AD et MSA, nous vous recommandons de vérifier que vous pouvez vous connecter au [portail des abonnements](https://my.visualstudio.com?wt.mc_id=o~msft~docs) et accéder aux avantages tels qu’Azure DevOps, Visual Studio et votre crédit individuel Azure DevTest.