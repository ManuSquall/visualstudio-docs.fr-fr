---
title: Accorder votre confiance à des solutions Office
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- security [Office development in Visual Studio], trust
- inclusion lists [Office development in Visual Studio], about inclusion lists
- trust [Office development in Visual Studio], 2007 Office system
- granting trust [Office development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: cfce58ca765e7e3710ecb55a1c84c09f0ee14f52
ms.sourcegitcommit: 1466ac0f49ebf7448ea4507ae3f79acb25d51d3e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/22/2018
---
# <a name="grant-trust-to-office-solutions"></a>Accorder votre confiance à des solutions Office
  Accorder votre confiance au moyen de solutions Office modification de la stratégie de sécurité de chaque ordinateur cible pour approuver l’assembly de solution, le manifeste d’application, le manifeste de déploiement et le document. Approbation peut être accordée à la solution Office par vous ou l’utilisateur final.  
  
 Vous pouvez accorder une confiance totale à la solution Office en signant les manifestes d’application et de déploiement.  
  
 Les utilisateurs finaux peuvent accorder une confiance à la solution Office en effectuant une décision d’approbation dans le [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] invite d’approbation.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
##  <a name="Signing"></a> Approuver la solution en signant les manifestes d’application et de déploiement  
 Manifestes d’application et déploiement pour Office solutions doivent être signées avec un certificat qui identifie le serveur de publication. Les certificats fournissent une base pour les décisions d’approbation.  
  
 Un certificat temporaire est créé pour vous et approuvé au moment de la génération afin que la solution s’exécute pendant que vous le déboguez. Si vous publiez une solution qui est signée avec un certificat temporaire, l’utilisateur final sera invité à prendre une décision d’approbation.  
  
 Si vous vous connectez à la solution avec un certificat connu et approuvé, la solution sera automatiquement installée sans solliciter l’utilisateur final à prendre une décision d’approbation. Pour plus d’informations sur la façon d’obtenir un certificat de signature, consultez [ClickOnce et Authenticode](/visualstudio/deployment/clickonce-and-authenticode). Une fois un certificat obtenu, le certificat doit être approuvé explicitement en l’ajoutant à la liste des éditeurs approuvés. Pour plus d’informations, consultez [Comment : ajouter un éditeur approuvé à un ordinateur client pour les applications ClickOnce](/visualstudio/deployment/how-to-add-a-trusted-publisher-to-a-client-computer-for-clickonce-applications).  
  
 Si un développeur signe la solution avec un certificat temporaire, un administrateur peut signer à nouveau la personnalisation avec un certificat connu et approuvé à l’aide de la Manifest Generation and Editing Tool (*mage.exe*), qui est un de le Outils de Microsoft .NET Framework. Pour plus d’informations sur la signature des solutions, consultez [Comment : les solutions Office de signe](../vsto/how-to-sign-office-solutions.md) et [Comment : signer des manifestes d’application et de déploiement](/visualstudio/ide/how-to-sign-application-and-deployment-manifests).  
  
##  <a name="TrustPrompt"></a>Approuver la solution à l’aide de l’invite d’approbation ClickOnce  
 [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] invite l’utilisateur final à prendre une décision d’approbation s’il n’existe aucune stratégie de l’entreprise qui approuve le certificat de la solution. Si l’utilisateur final approuve la solution, une entrée de liste d’inclusion est créée qui contient une URL et une clé publique pour stocker cette décision d’approbation. Lorsqu’une personnalisation approuvée est exécutée ultérieurement, l’utilisateur final n’est pas invité à nouveau.  
  
 Les administrateurs peuvent désactiver la [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] invite d’approbation ou exiger que l’invite de commandes se produisent uniquement pour les solutions qui sont signées avec un certificat Authenticode. Pour plus d’informations sur la façon de modifier ces paramètres pour les zones MyComputer, LocalIntranet, Internet, TrustedSites et UntrustedSites, consultez [Comment : configurer le comportement d’invite d’approbation ClickOnce](/visualstudio/deployment/how-to-configure-the-clickonce-trust-prompt-behavior).  
  
## <a name="see-also"></a>Voir aussi  
 [Sécurisez les solutions Office](../vsto/securing-office-solutions.md)   
 [Accorder votre confiance à des documents](../vsto/granting-trust-to-documents.md)   
 [Résoudre les problèmes de sécurité des solutions Office](../vsto/troubleshooting-office-solution-security.md)   
 [Considérations de sécurité spécifiques pour les solutions Office](../vsto/specific-security-considerations-for-office-solutions.md)  
  
  