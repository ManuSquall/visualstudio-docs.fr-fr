---
title: Accorder un niveau de confiance à des solutions Office
description: Pour accorder un niveau de confiance à des solutions Office, vous pouvez modifier la stratégie de sécurité de chaque ordinateur cible afin de faire confiance à l’assembly de solution, au manifeste de déploiement et au document.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: f0b81c034ed0f8934da378dc214191d3be1f4506
ms.sourcegitcommit: ce85cff795df29e2bd773b4346cd718dccda5337
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/08/2020
ms.locfileid: "96848324"
---
# <a name="grant-trust-to-office-solutions"></a>Accorder un niveau de confiance à des solutions Office
  Accorder un niveau de confiance à des solutions Office consiste à modifier la stratégie de sécurité de chaque ordinateur cible pour approuver l’assembly de solution, le manifeste d’application, le manifeste de déploiement et le document. L’approbation peut être accordée à la solution Office par vous ou par l’utilisateur final.

 Vous pouvez accorder une confiance totale à la solution Office en signant les manifestes d’application et de déploiement.

 Les utilisateurs finaux peuvent accorder une confiance à la solution Office en faisant une décision d’approbation dans l' [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] invite d’approbation.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

## <a name="trust-the-solution-by-signing-the-application-and-deployment-manifests"></a><a name="Signing"></a> Faire confiance à la solution en signant les manifestes d’application et de déploiement
 Tous les manifestes d’application et de déploiement pour les solutions Office doivent être signés avec un certificat qui identifie le serveur de publication. Les certificats fournissent une base pour prendre des décisions d’approbation.

 Un certificat temporaire est créé pour vous et vous avez accordé une approbation au moment de la génération afin que la solution s’exécute pendant le débogage. Si vous publiez une solution signée avec un certificat temporaire, l’utilisateur final est invité à prendre une décision d’approbation.

 Si vous signez la solution avec un certificat approuvé et connu, la solution est automatiquement installée sans inviter l’utilisateur final à prendre une décision d’approbation. Pour plus d’informations sur la façon d’obtenir un certificat pour la signature, consultez [ClickOnce et Authenticode](../deployment/clickonce-and-authenticode.md). Après l’obtention d’un certificat, le certificat doit être approuvé explicitement en l’ajoutant à la liste des éditeurs approuvés. Pour plus d’informations, consultez [Comment : ajouter un éditeur approuvé à un ordinateur client pour les applications ClickOnce](../deployment/how-to-add-a-trusted-publisher-to-a-client-computer-for-clickonce-applications.md).

 Si un développeur signe la solution avec un certificat temporaire, un administrateur peut signer à nouveau la personnalisation avec un certificat connu et approuvé à l’aide de l’Outil Manifest Generation and Editing (*mage.exe*), qui est l’un des outils de l’infrastructure Microsoft .net. Pour plus d’informations sur la signature des solutions, consultez [Comment : signer des solutions Office](../vsto/how-to-sign-office-solutions.md) et [Comment : signer des manifestes d’application et de déploiement](../ide/how-to-sign-application-and-deployment-manifests.md).

## <a name="trust-the-solution-by-using-the-clickonce-trust-prompt"></a><a name="TrustPrompt"></a>Approuver la solution à l’aide de l’invite d’approbation ClickOnce
 [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] invite l’utilisateur final à prendre la décision en matière d’approbation s’il n’existe aucune stratégie au niveau de l’organisation qui approuve le certificat de la solution. Si l’utilisateur final accorde un niveau de confiance à la solution, une entrée de liste d’inclusion est créée et contient une URL et une clé publique pour stocker cette décision d’approbation. Quand une personnalisation approuvée est exécutée ultérieurement, l’utilisateur final n’est plus invité à le faire.

 Les administrateurs peuvent désactiver l' [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] invite d’approbation ou exiger que l’invite s’affiche uniquement pour les solutions qui sont signées avec un certificat Authenticode. Pour plus d’informations sur la modification de ces paramètres pour les zones MyComputer, LocalIntranet, Internet, TrustedSites et UntrustedSites, consultez Guide pratique [pour configurer le comportement de l’invite d’approbation ClickOnce](../deployment/how-to-configure-the-clickonce-trust-prompt-behavior.md).

## <a name="see-also"></a>Voir aussi

- [Sécuriser les solutions Office](../vsto/securing-office-solutions.md)
- [Accorder un niveau de confiance à des documents](../vsto/granting-trust-to-documents.md)
- [Résoudre les problèmes de sécurité des solutions Office](../vsto/troubleshooting-office-solution-security.md)
- [Considérations de sécurité spécifiques pour les solutions Office](../vsto/specific-security-considerations-for-office-solutions.md)