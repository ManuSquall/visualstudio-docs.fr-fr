---
title: "Protection des documents dans les solutions au niveau du document | Microsoft Docs"
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
  - "documents (développement Office dans Visual Studio), autorisations restreintes"
  - "documents Office (développement Office dans Visual Studio), autorisations restreintes"
  - "autorisations (développement Office dans Visual Studio)"
  - "autorisations restreintes (développement Office dans Visual Studio)"
  - "classeurs (développement Office dans Visual Studio), autorisations restreintes"
ms.assetid: a25472ad-03f0-4804-9d19-e5ff71340d49
caps.latest.revision: 36
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 35
---
# Protection des documents dans les solutions au niveau du document
  Microsoft Office Word et Microsoft Office Excel offrent des fonctionnalités de protection pour vos projets au niveau du document.  Ces fonctionnalités empêchent les utilisateurs non autorisés de modifier certaines parties protégées d'un document.  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 À l'aide d'Excel, vous pouvez activer et désactiver la protection pendant que le classeur est ouvert dans le concepteur.  Avec Word, vous pouvez uniquement l'activer en dehors du concepteur.  Au moment de l'exécution, vous pouvez activer ou désactiver la protection par programmation pour Word et Excel.  
  
 Lorsque la protection de document est activée dans un document ouvert dans le concepteur, tous les contrôles sont supprimés de la **boîte à outils** ou deviennent indisponibles, et vous ne pouvez rien faire glisser de la fenêtre **Sources de données** vers le document.  
  
## Document serveur et documents protégés  
 Si un document est protégé, le cache de données n'est pas accessible en dehors du document.  Vous ne pouvez pas utiliser la classe <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> pour extraire ou manipuler des données mises en cache dans un document protégé ni utiliser les autres méthodes de la classe <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.ServerDocument>.  
  
## Protection des documents Word dans le concepteur  
 Si vous ajoutez une protection à un document ou modèle Word alors qu'il est ouvert dans Visual Studio, vous ne pouvez pas activer cette protection dans le concepteur.  Le document est en mode Design tant qu'il est ouvert dans Visual Studio et il doit passer en mode exécution avant que vous ne puissiez activer la protection.  
  
 Cependant, si vous créez un projet qui utilise un document Word existant dont la protection est activée, le document est protégé lors de son utilisation dans le concepteur.  Vous ne pouvez pas modifier les parties protégées du document, mais vous pouvez toujours écrire du code dans l'éditeur de code pour automatiser le document.  Vous ne pouvez pas non plus générer le projet si la protection est activée pendant que le document est ouvert dans Visual Studio.  
  
 Vous pouvez désactiver la protection pendant que le document est ouvert dans le concepteur afin de pouvoir modifier le document et générer le projet.  Vous ne pouvez pas désactiver la protection de la copie dans le concepteur pendant le débogage ; le document qui s'ouvre lors du débogage est une copie distincte de celui qui est ouvert dans le concepteur \(la copie de sortie est stockée dans le répertoire \\bin pour Visual Basic et \\bin\\debug pour C\#\).  
  
 Vous pouvez activer la protection dans la copie du document qui s'ouvre dans le concepteur en fermant le projet dans Visual Studio, en ouvrant la copie du document dans le répertoire du projet et en activant la protection.  
  
## Activation de la protection des documents Word au cours de la génération  
 Visual Studio commence à appliquer la protection des documents et des modèles Word dès le processus de génération, afin que la protection soit activée lorsque le document est ouvert pour le débogage.  Le document est protégé avec un mot de passe vide.  
  
 La protection est activée pendant la génération de sorte que, si l'événement <xref:Microsoft.Office.Tools.Word.Document.Startup> du document contient un code susceptible de provoquer des exceptions ou de modifier le comportement de l'application, ce code puisse être débogué correctement.  Si vous activez la protection après l'ouverture du document, le code d'initialisation ne peut pas être débogué ni testé.  
  
## Définition du mot de passe  
 Visual Studio active automatiquement la protection, mais ne fournit pas de mot de passe par défaut.  Si vous souhaitez que la protection de document utilise un mot de passe, vous devez l'ajouter avant de déployer votre solution.  L'ajout d'un mot de passe vous permet de laisser les utilisateurs autorisés supprimer la protection du document ; sans mot de passe, il est difficile de supprimer la protection.  Pour plus d'informations sur la définition d'un mot de passe, consultez l'aide de l'application Office concernée.  
  
## Voir aussi  
 [Comment : protéger des documents et des parties de documents par programmation](../vsto/how-to-programmatically-protect-documents-and-parts-of-documents.md)   
 [Exemples et procédures pas à pas relatifs au développement Office](../vsto/office-development-samples-and-walkthroughs.md)   
 [Vue d'ensemble de la gestion des droits relatifs à l'information et des extensions de code managé](../vsto/information-rights-management-and-managed-code-extensions-overview.md)   
 [Protection par mot de passe des documents Office](../vsto/password-protection-on-office-documents.md)   
 [Comment : permettre au code de s'exécuter derrière des documents dotés d'autorisations restreintes](../vsto/how-to-permit-code-to-run-behind-documents-with-restricted-permissions.md)   
 [Conception et création de solutions Office](../vsto/designing-and-creating-office-solutions.md)  
  
  