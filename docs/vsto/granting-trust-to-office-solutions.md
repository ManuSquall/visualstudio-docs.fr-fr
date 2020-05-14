---
title: Subvention de confiance aux solutions Office
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- security [Office development in Visual Studio], trust
- inclusion lists [Office development in Visual Studio], about inclusion lists
- trust [Office development in Visual Studio], 2007 Office system
- granting trust [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: cf7a68d5d3567305e4f70049d76a1c260ddecf25
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/13/2020
ms.locfileid: "79303301"
---
# <a name="grant-trust-to-office-solutions"></a>Subvention de confiance aux solutions Office
  Accorder la confiance aux solutions Office signifie modifier la politique de sécurité de chaque ordinateur cible pour faire confiance à l’assemblage de solutions, au manifeste d’application, au manifeste de déploiement et au document. La confiance peut être accordée à la solution Office par vous ou l’utilisateur final.

 Vous pouvez accorder une pleine confiance à la solution Office en signant les manifestes de demande et de déploiement.

 Les utilisateurs finaux peuvent accorder la confiance à [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] la solution Office en prenant une décision de confiance dans la fiducie rapidement.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

## <a name="trust-the-solution-by-signing-the-application-and-deployment-manifests"></a><a name="Signing"></a>Faites confiance à la solution en signant l’application et le déploiement manifeste
 Toutes les demandes et les manifestes de déploiement pour les solutions Office doivent être signés avec un certificat qui identifie l’éditeur. Les certificats constituent une base pour prendre des décisions en fiducie.

 Un certificat temporaire est créé pour vous et accordé la confiance au moment de la construction de sorte que la solution fonctionnera pendant que vous le déboguer. Si vous publiez une solution signée avec un certificat temporaire, l’utilisateur final sera invité à prendre une décision de fiducie.

 Si vous signez la solution avec un certificat connu et de confiance, la solution sera automatiquement installée sans inciter l’utilisateur final à prendre une décision de confiance. Pour plus d’informations sur la façon d’obtenir un certificat de signature, voir [ClickOnce et Authenticode](../deployment/clickonce-and-authenticode.md). Une fois qu’un certificat est obtenu, le certificat doit être explicitement approuvé en l’ajoutant à la liste des éditeurs de confiance. Pour plus d’informations, voir [Comment : Ajouter un éditeur de confiance à un ordinateur client pour les applications ClickOnce](../deployment/how-to-add-a-trusted-publisher-to-a-client-computer-for-clickonce-applications.md).

 Si un développeur signe la solution avec un certificat temporaire, un administrateur peut re-signer la personnalisation avec un certificat connu et de confiance en utilisant la génération manifeste et l’outil d’édition (*mage.exe*), qui est l’un des outils Microsoft .NET Framework. Pour plus d’informations sur les solutions de signature, voir [Comment : Sign Office solutions](../vsto/how-to-sign-office-solutions.md) et [Comment: Signez l’application et le déploiement manifeste .](../ide/how-to-sign-application-and-deployment-manifests.md)

## <a name="trust-the-solution-by-using-the-clickonce-trust-prompt"></a><a name="TrustPrompt"></a>Faites confiance à la solution en utilisant l’invite ClickOnce trust
 [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]invite l’utilisateur final à prendre la décision de confiance s’il n’existe aucune politique à l’échelle de l’organisation qui fait confiance au certificat de la solution. Si l’utilisateur final accorde la confiance à la solution, une inscription à la liste d’inclusion est créée qui contient une URL et une clé publique pour stocker cette décision de fiducie. Lorsqu’une personnalisation fiable est exécutée plus tard, l’utilisateur final n’est pas invité à nouveau.

 Les administrateurs peuvent [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] désactiver la fiducie prompte ou exiger que l’invite se produise uniquement pour les solutions qui sont signées avec un certificat Authenticode. Pour plus d’informations sur la façon de modifier ces paramètres pour les zones MyComputer, LocalIntranet, Internet, TrustedSites et UntrustedSites, voir [Comment configurer le comportement invite clickOnce trust](../deployment/how-to-configure-the-clickonce-trust-prompt-behavior.md).

## <a name="see-also"></a>Voir aussi

- [Solutions Secure Office](../vsto/securing-office-solutions.md)
- [Subvention de la confiance aux documents](../vsto/granting-trust-to-documents.md)
- [Sécurité de solution De bureau de dépannage](../vsto/troubleshooting-office-solution-security.md)
- [Considérations de sécurité spécifiques pour les solutions Office](../vsto/specific-security-considerations-for-office-solutions.md)