---
title: Utilisation des compte Microsoft connectés et des identités de Azure Active Directory | Microsoft Docs
author: evanwindom
ms.author: v-evwin
manager: lank
ms.assetid: 50ce0445-ef1a-4e92-b9d0-aebb2155a111
ms.date: 03/11/2020
ms.topic: conceptual
robots: noindex, nofollow
description: En savoir plus sur l’utilisation des comptes Azure Active Directory et des identités Microsoft connectés
ms.openlocfilehash: f7b2cad08eb94b15e35015db7e8ac3fe084a00ea
ms.sourcegitcommit: 78face15e71c305a2146358df51f8f1fefe3388f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87805607"
---
# <a name="how-to-use-connected-identities-in-visual-studio-subscriptions"></a>Comment utiliser les identités connectées dans les abonnements Visual Studio
Si vous recevez un abonnement Visual Studio par le biais de votre entreprise ou établissement scolaire et que vous utilisez votre compte Microsoft (MSA) pour vous connecter, votre administrateur d’abonnements peut connecter votre MSA à votre identité dans le Azure Active Directory de votre organisation (Azure AD).  Cela modifiera la façon dont vous accédez à certains des avantages inclus dans votre abonnement. 

## <a name="overview-of-connected-ids"></a>Vue d’ensemble des ID connectés
Les organisations évoluent de plus en plus vers les identités basées sur les Azure AD pour offrir une sécurité et une prise en charge améliorées pour la gestion automatisée des abonnements.  Si votre abonnement utilise un MSA comme une @outlook.com autre adresse de messagerie personnelle, votre administrateur peut modifier votre courrier électronique de connexion à votre identité Azure ad.  Cela modifiera la façon de se connecter au portail de l’abonné à l’adresse, https://my.visualstudio.com mais peut ne pas modifier la façon dont vous accédez à tous vos avantages.  

Si votre administrateur connecte vos identités MSA et Azure AD, vous recevez un message électronique vous informant que vous pouvez commencer à accéder à votre abonnement Visual Studio avec votre identité Azure AD au lieu de votre MSA. 

## <a name="how-to-access-benefits-using-azure-ad-identities"></a>Comment accéder aux avantages à l’aide des identités Azure AD
Une fois que votre administrateur a connecté votre MSA à votre identité Azure AD, vous devez vous connecter au portail de l’abonné auprès de https://my.visualstudio.com avec votre identité Azure AD pour accéder aux avantages qui s’appuient sur Azure ad.  notamment :
- Environnement IDE de Visual Studio
- Azure DevOps
- Crédit individuel Azure DevTest

## <a name="how-to-access-benefits-using-your-msa"></a>Comment accéder aux avantages à l’aide de votre MSA
Pour la plupart des avantages offerts par les abonnements Visual Studio tels que Pluralsight, LinkedIn, CloudPilot et d’autres, vous créez en fait des comptes d’utilisateur sur les sites Web des partenaires.  Pour ces comptes, vous devez continuer à utiliser l’identité que vous avez utilisée lors de la création du compte.  Par exemple, si vous avez activé votre avantage Pluralsight à l’aide de votre MSA, vous devez continuer à utiliser votre MSA lors de la formation à Pluralsight, quelle que soit l’identité que vous utilisez pour vous connecter au portail de l’abonné.  

## <a name="use-an-alternate-identity-to-access-your-subscription"></a>Utiliser une autre identité pour accéder à votre abonnement
L’ajout d’un compte secondaire à votre abonnement Visual Studio vous permet d’accéder aux avantages de cet abonnement, par exemple Azure DevOps et Azure, avec une autre identité que celle à laquelle l’abonnement est affecté. Dans le passé, cette fonctionnalité était disponible uniquement si votre abonnement VS (Visual Studio) était affecté à un compte MSA (compte Microsoft). Nous avons étendu cette fonctionnalité aux comptes professionnels ou scolaires dans Azure AD (Azure Active Directory).  Pour plus d’informations sur l’utilisation de comptes secondaires, consultez notre article sur les [autres identités](vs-alternate-identity.md) . 

## <a name="frequently-asked-questions"></a>Forum aux questions
### <a name="q-how-can-i-contact-my-admin-about-this"></a>Q : Comment puis-je contacter mon administrateur à ce sujet ?
R : pour plus d’informations sur la façon de contacter votre administrateur, consultez notre article [contacter votre administrateur d’abonnements](contact-my-admin.md) .  

### <a name="q-im-an-admin--how-do-i-use-this"></a>Q : je suis administrateur.  Comment faire l’utiliser ?
R : l’implémentation d’identités connectées est simple.  Pour plus d’informations, lisez [cet article](personal-email-sign-ins.md). 

## <a name="see-also"></a>Voir aussi
- [Documentation de Visual Studio](https://docs.microsoft.com/visualstudio/)
- [Documentation Azure DevOps](https://docs.microsoft.com/azure/devops/)
- [Documentation Azure](https://docs.microsoft.com/azure/)
- [Documentation Microsoft 365](https://docs.microsoft.com/microsoft-365/)

## <a name="next-steps"></a>Étapes suivantes
Une fois que votre administrateur a connecté vos comptes Azure AD et MSA, nous vous recommandons de vérifier que vous pouvez vous connecter au [portail des abonnements](https://my.visualstudio.com?wt.mc_id=o~msft~docs) et accéder aux avantages tels qu’Azure DevOps, Visual Studio et votre crédit individuel Azure DevTest. 
