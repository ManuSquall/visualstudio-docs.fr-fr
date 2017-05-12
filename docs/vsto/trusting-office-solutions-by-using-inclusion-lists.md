---
title: "Octroi de niveaux de confiance &#224; des solutions Office &#224; l&#39;aide de listes d&#39;inclusion"
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
  - "autorisations (développement Office dans Visual Studio)"
  - "listes d’inclusion (développement Office dans Visual Studio), à propos des listes d’inclusion"
  - "sécurité (développement Office dans Visual Studio), listes d’inclusion"
  - "listes d'inclusion (développement Office dans Visual Studio)"
ms.assetid: 6dae0128-435b-4fa1-aed9-73e728fdcacf
caps.latest.revision: 44
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 43
---
# Octroi de niveaux de confiance &#224; des solutions Office &#224; l&#39;aide de listes d&#39;inclusion
  Les listes d’inclusion permettent aux utilisateurs d’approuver des solutions Office signées avec un certificat qui identifie l’éditeur. Elles sont propres à l’utilisateur et elles peuvent servir aux personnalisations au niveau du document et aux compléments VSTO.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
 Quand un utilisateur démarre une solution Office qui n’a pas été approuvée pour lui, il est invité à prendre une décision en matière de sécurité avec une invite d’approbation [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]. Si l’utilisateur décide d’approuver la solution, la personnalisation s’exécute et il ne reçoit plus d’invite au prochain démarrage de la solution.  
  
## Liste d’inclusion et Windows Installer  
 L’installation de solutions Office dans le répertoire Program Files à l’aide de Windows Installer requiert des droits d’administrateur. Pour les solutions Office installées dans le répertoire Program Files, Visual Studio Tools pour Office Runtime ne vérifie plus la liste d’inclusion car les solutions Office ont déjà reçu l’autorisation FullTrust.  
  
## Invite d’approbation ClickOnce  
 À l’aide de l’implémentation [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] des solutions Office, les administrateurs peuvent configurer le niveau d’invite d’approbation pour autoriser les invites, désactiver les invites ou exiger un certificat de confiance. Cette configuration s’effectue à l’aide d’une clé de Registre qui contrôle l’accès à la liste d’inclusion.  
  
 Si l’invite est désactivée, seules les solutions qui possèdent un certificat de confiance connu peuvent être installées. Si le niveau d’invite défini est Authenticode requis, la solution doit être signée avec un certificat émis par une autorité connue, mais elle ne requiert pas un certificat lié à une autorité racine approuvée \(un certificat de confiance\). Si l’invite est autorisée, la solution peut être signée avec un certificat dont l’identité est inconnue. Dans ce scénario, la décision d’approbation est soumise à l’utilisateur final et un certificat temporaire suffit pour installer une solution.  
  
 Pour plus d’informations, consultez [Comment : configurer la sécurité de la liste d'inclusion](../vsto/how-to-configure-inclusion-list-security.md) et le tableau 2, intitulé Effets du lancement d’une valeur de clé de Registre de niveau d’invite, dans [Configuration d’éditeurs approuvés ClickOnce](http://go.microsoft.com/fwlink/?LinkId=94774).  
  
## Structure de la liste d’inclusion  
 Une entrée de liste d’inclusion valide comporte deux parties : un chemin vers le manifeste de déploiement et la clé publique utilisée pour signer la solution. Une fois qu’une solution est ajoutée à la liste d’inclusion, elle est considérée comme approuvée. Quand la solution Office s’exécute, l’application Office compare la clé publique figurant dans la liste d’inclusion à la clé de signature figurant dans le manifeste de déploiement pour vérifier que la solution qui est en cours d’exécution est identique à la version d’origine approuvée.  
  
## Voir aussi  
 [Octroi de niveaux de confiance à des solutions Office](../vsto/granting-trust-to-office-solutions.md)   
 [Sécurisation des solutions Office](../vsto/securing-office-solutions.md)  
  
  