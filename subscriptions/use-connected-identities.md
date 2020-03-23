---
title: Comment utiliser les identités de compte Microsoft connectées et Azure Active Directory Microsoft Docs
author: evanwindom
ms.author: lank
manager: lank
ms.date: 03/11/2020
ms.topic: conceptual
robots: noindex, nofollow
description: Découvrez comment travailler avec des comptes Microsoft connectés et des identités Azure Active Directory
ms.openlocfilehash: 3dcb41a26f27e5135962edf7ff933de40ccefe5e
ms.sourcegitcommit: f8e3715c64255b476520bfa9267ceaf766bde3b0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/21/2020
ms.locfileid: "79508977"
---
# <a name="how-to-use-connected-identities-in-visual-studio-subscriptions"></a>Comment utiliser les identités connectées dans les abonnements Visual Studio
Si vous recevez un abonnement Visual Studio par le biais de votre travail ou de votre école, et que vous utilisez votre compte Microsoft (MSA) pour vous connecter, votre administrateur d’abonnements peut connecter votre MSA à votre identité dans l’annuaire actif Azure de votre organisation (Azure AD).  Cela changera la façon dont vous accédez à certains des avantages inclus dans votre abonnement. 

## <a name="overview-of-connected-ids"></a>Aperçu des DIU connectés
Les organisations s’installent de plus en plus vers les identités azuréennes pour améliorer la sécurité et le soutien à la gestion automatisée des abonnements.  Si votre abonnement utilise un @outlook.com MSA tel qu’une adresse e-mail personnelle ou une autre, votre administrateur peut modifier votre e-mail de connexion à votre identité Azure AD.  Cela changera la façon de vous https://my.visualstudio.com connecter au portail d’abonnés, mais peut ne pas changer la façon dont vous accédez à tous vos avantages.  

Si votre administrateur connecte vos identités MSA et Azure AD, vous recevrez un e-mail vous informant de commencer à accéder à votre abonnement Visual Studio avec votre identité Azure AD au lieu de votre MSA. 

## <a name="how-to-access-benefits-using-azure-ad-identities"></a>Comment accéder aux avantages en utilisant les identités Azure AD
Une fois que votre administrateur a connecté votre MSA à votre identité Azure https://my.visualstudio.com AD, vous devrez vous connecter au portail d’abonnés avec votre identité Azure AD pour accéder aux avantages qui dépendent d’Azure AD.  notamment :
- IDE Visual Studio
- Azure DevOps
- Crédit individuel Azure DevTest

## <a name="how-to-access-benefits-using-your-msa"></a>Comment accéder aux prestations à l’aide de votre MSA
Pour de nombreux avantages offerts dans les abonnements Visual Studio tels que Pluralsight, LinkedIn, CloudPilot et d’autres, vous créez en fait des comptes d’utilisateurs sur les sites Web des partenaires.  Pour ces comptes, vous devez continuer à utiliser l’identité que vous avez utilisée lorsque vous avez créé le compte.  Par exemple, si vous avez activé votre prestation Pluralsight à l’aide de votre MSA, vous devez continuer à utiliser votre MSA lors de la formation Pluralsight, quelle que soit l’identité que vous utilisez pour vous connecter au portail d’abonnés.  

## <a name="use-an-alternate-identity-to-access-your-subscription"></a>Utilisez une autre identité pour accéder à votre abonnement
L’ajout d’un compte secondaire à votre abonnement Visual Studio vous permet d’accéder aux avantages de cet abonnement, par exemple Azure DevOps et Azure, avec une autre identité que celle à laquelle l’abonnement est affecté. Dans le passé, cette fonctionnalité était disponible uniquement si votre abonnement VS (Visual Studio) était affecté à un compte MSA (compte Microsoft). Nous avons étendu cette fonctionnalité aux comptes professionnels ou scolaires dans Azure AD (Azure Active Directory).  Pour plus d’informations sur l’utilisation de comptes alternatifs, consultez notre article [Sur les identités alternatives.](vs-alternate-identity.md) 

## <a name="frequently-asked-questions"></a>Forum aux questions
### <a name="q-how-can-i-contact-my-admin-about-this"></a>Q: Comment puis-je contacter mon administrateur à ce sujet?
R : Veuillez consulter [l’article de votre administrateur d’abonnements Pour](contact-my-admin.md) obtenir des informations sur le contact avec votre administrateur.  

## <a name="see-also"></a>Voir aussi
- [Documentation Visual Studio](https://docs.microsoft.com/visualstudio/)
- [Documentation Azure DevOps](https://docs.microsoft.com/azure/devops/)
- [Documentation Azure](https://docs.microsoft.com/azure/)
- [Documentation Microsoft 365](https://docs.microsoft.com/microsoft-365/)

## <a name="next-steps"></a>Étapes suivantes
Une fois que votre administrateur connecte vos comptes Azure AD et MSA, nous vous recommandons de vérifier que vous pouvez vous connecter avec succès au [portail d’abonnement](https://my.visualstudio.com?wt.mc_id=o~msft~docs) et accéder à des avantages comme Azure DevOps, Visual Studio et votre crédit individuel Azure DevTest. 