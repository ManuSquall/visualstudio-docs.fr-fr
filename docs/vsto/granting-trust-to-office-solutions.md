---
title: Accorder votre confiance à des solutions Office
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
ms.openlocfilehash: b07aea10d2b1d55e98239d6dd804a506390f1974
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2019
ms.locfileid: "54871375"
---
# <a name="grant-trust-to-office-solutions"></a>Accorder votre confiance à des solutions Office
  Accorder votre confiance aux moyens de solutions Office modification de la stratégie de sécurité de chaque ordinateur cible pour approuver l’assembly de solution, le manifeste d’application, le manifeste de déploiement et le document. Approbation peut être accordée à la solution Office par vous ou l’utilisateur final.

 Vous pouvez accorder une confiance totale pour la solution Office en signant les manifestes d’application et de déploiement.

 Les utilisateurs finaux peuvent accorder une confiance à la solution Office à prendre une décision d’approbation dans le [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] invite d’approbation.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

##  <a name="Signing"></a> Approuver la solution en signant les manifestes d’application et de déploiement
 Manifestes d’application et déploiement pour Office solutions doivent être signées avec un certificat qui identifie le serveur de publication. Les certificats servent de base pour les décisions d’approbation.

 Un certificat temporaire est créé pour vous et approuvé au moment de la génération afin que la solution s’exécute pendant le débogage, il. Si vous publiez une solution qui est signée avec un certificat temporaire, l’utilisateur final sera invité à prendre une décision d’approbation.

 Si vous vous connectez à la solution avec un certificat connu et approuvé, la solution sera automatiquement installée sans solliciter l’utilisateur final à prendre une décision d’approbation. Pour plus d’informations sur la façon d’obtenir un certificat de signature, consultez [ClickOnce et Authenticode](../deployment/clickonce-and-authenticode.md). Une fois un certificat obtenu, le certificat doit être explicitement approuvé en l’ajoutant à la liste des éditeurs approuvés. Pour plus d'informations, voir [Procédure : Ajouter un éditeur approuvé à un ordinateur client pour les applications ClickOnce](../deployment/how-to-add-a-trusted-publisher-to-a-client-computer-for-clickonce-applications.md).

 Si un développeur connecte à la solution avec un certificat temporaire, un administrateur peut signer à nouveau la personnalisation avec un certificat connu et approuvé à l’aide de la Manifest Generation and Editing Tool (*mage.exe*), qui est une de le Outils de Microsoft .NET Framework. Pour plus d’informations sur la signature des solutions, consultez [Comment : Signer des solutions Office](../vsto/how-to-sign-office-solutions.md) et [Comment : signer des manifestes d’application et de déploiement](../ide/how-to-sign-application-and-deployment-manifests.md).

##  <a name="TrustPrompt"></a>Approuver la solution à l’aide de l’invite d’approbation ClickOnce
 [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] invite l’utilisateur final à prendre la décision d’approbation s’il n’existe aucune stratégie de l’entreprise qui approuve les certificats de la solution. Si l’utilisateur final accorde la confiance à la solution, une entrée de liste d’inclusion est créée qui contient une URL et une clé publique pour stocker cette décision d’approbation. Quand une personnalisation approuvée est exécutée ultérieurement, l’utilisateur final n’est pas invité à nouveau.

 Les administrateurs peuvent désactiver la [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] invite d’approbation ou exiger que l’invite se produisent uniquement pour les solutions qui sont signées avec un certificat Authenticode. Pour plus d’informations sur la façon de modifier ces paramètres pour les zones MyComputer, LocalIntranet, Internet, TrustedSites et UntrustedSites, consultez [Comment : Configurer le comportement de l’invite d’approbation ClickOnce](../deployment/how-to-configure-the-clickonce-trust-prompt-behavior.md).

## <a name="see-also"></a>Voir aussi

- [Sécurisez les solutions Office](../vsto/securing-office-solutions.md)
- [Accorder votre confiance à des documents](../vsto/granting-trust-to-documents.md)
- [Résoudre les problèmes de sécurité des solutions Office](../vsto/troubleshooting-office-solution-security.md)
- [Considérations de sécurité spécifiques pour les solutions Office](../vsto/specific-security-considerations-for-office-solutions.md)