---
title: "Octroi de niveaux de confiance &#224; des solutions Office"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "sécurité (développement Office dans Visual Studio), approbation"
  - "listes d’inclusion (développement Office dans Visual Studio), à propos des listes d’inclusion"
  - "approbation (développement Office dans Visual Studio), version 2007 d’Office System"
  - "accorder des niveaux de confiance (développement Office dans Visual Studio)"
ms.assetid: 6c33e614-d367-4556-9e76-0f302ad0f929
caps.latest.revision: 37
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 36
---
# Octroi de niveaux de confiance &#224; des solutions Office
  Octroi de niveaux de confiance à des solutions Office signifie modifier la stratégie de sécurité de chaque ordinateur cible pour approuver l'assembly, le manifeste de l'application, le manifeste de déploiement, et le document de solution.  L'approbation peut être accordée à la solution Office par vous ou l'utilisateur final.  
  
 Vous pouvez accorder la confiance totale à la solution Office en signant l'application et les manifestes de déploiement.  
  
 Les utilisateurs finaux peuvent approuver la solution Office en faisant une décision d'approbation dans l'invite d'approbation d' [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] .  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
##  <a name="Signing"></a> La confiance à la solution lors de la signature de l'application et les manifestes de déploiement  
 Tous les manifestes d'application et de déploiement pour les solutions Office doivent être signés avec un certificat qui identifie l'éditeur.  Les certificats aident les utilisateurs dans leurs décisions d'approbation.  
  
 Un certificat temporaire est créé pour vous et approuvé au moment de la génération. Par conséquent, la solution s'exécutera pendant que vous la déboguerez.  Si vous publiez une solution qui est signée avec un certificat temporaire, l'utilisateur final sera invité à prendre une décision d'approbation.  
  
 Si vous signez la solution avec un certificat connu et approuvé, elle sera installée automatiquement sans que l'utilisateur final soit invité à l'approuver.  Pour plus d'informations sur l'obtention d'un certificat à des fins de signature, consultez [ClickOnce and Authenticode](../deployment/clickonce-and-authenticode.md).  Une fois le certificat obtenu, celui\-ci doit être approuvé explicitement en l'ajoutant à la liste des éditeurs approuvés.  Pour plus d'informations, consultez [How to: Add a Trusted Publisher to a Client Computer for ClickOnce Applications](~/deployment/how-to-add-a-trusted-publisher-to-a-client-computer-for-clickonce-applications.md).  
  
 Si un développeur signe la solution avec un certificat temporaire, un administrateur peut signer à nouveau la personnalisation avec un certificat connu et approuvé à l'aide de l'Outil Manifest Generation and Editing \(mage.exe\), l'un des outils Microsoft .NET Framework.  Pour plus d'informations sur la façon de signer des solutions, consultez [Comment : signer des solutions Office](../vsto/how-to-sign-office-solutions.md) et [Comment : signer des manifestes d'application et de déploiement](~/ide/how-to-sign-application-and-deployment-manifests.md).  
  
##  <a name="TrustPrompt"></a> Confiance de la solution à l'aide de l'invite d'approbation ClickOnce  
 [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] invite l'utilisateur final à prendre une décision d'approbation s'il n'existe aucune stratégie au niveau de l'organisation permettant d'approuver le certificat de la solution.  Si l'utilisateur final approuve la solution, une entrée de liste d'inclusion est créée. Elle contient une URL et une clé publique pour stocker cette décision d'approbation.  Lorsqu'une personnalisation approuvée est exécutée ultérieurement, l'utilisateur final ne reçoit plus d'alerte.  
  
 Les administrateurs peuvent désactiver l'invite d'approbation [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] ou exiger que l'invite n'apparaisse que pour les solutions signées avec un certificat Authenticode.  Pour plus d'informations sur la modification de ces paramètres pour les zones MyComputer, LocalIntranet, Internet, TrustedSites et UntrustedSites, consultez [How to: Configure the ClickOnce Trust Prompt Behavior](~/deployment/how-to-configure-the-clickonce-trust-prompt-behavior.md).  
  
## Voir aussi  
 [Sécurisation des solutions Office](../vsto/securing-office-solutions.md)   
 [Octroi de niveaux de confiance à des documents](../vsto/granting-trust-to-documents.md)   
 [Dépannage de la sécurité des solutions Office](../vsto/troubleshooting-office-solution-security.md)   
 [Considérations spécifiques sur la sécurité pour les solutions Office](../vsto/specific-security-considerations-for-office-solutions.md)  
  
  