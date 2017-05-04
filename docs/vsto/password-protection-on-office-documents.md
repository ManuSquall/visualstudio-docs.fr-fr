---
title: "Protection par mot de passe des documents Office | Microsoft Docs"
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
  - "mots de passe (développement Office dans Visual Studio), protections de documents"
  - "autorisations (développement Office dans Visual Studio)"
  - "classeurs (développement Office dans Visual Studio), autorisations restreintes"
ms.assetid: 9cee99c8-73c6-4f89-9d5e-7912c876ff96
caps.latest.revision: 21
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 20
---
# Protection par mot de passe des documents Office
  Il est possible de définir un mot de passe dans vos documents Microsoft Office Word et vos classeurs Microsoft Office Excel pour qu'ils ne puissent pas être ouverts par quelqu'un qui ignore le mot de passe.  Cette option est appelée **Mot de passe pour la lecture**.  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 Vous pouvez créer des projets au niveau du document qui utilisent des documents et des classeurs existants dans lesquels l'option **Mot de passe pour la lecture** est activée.  Les documents Word et Excel dont l'option **Mot de passe pour la lecture** est activée ont un comportement différent dans Visual Studio.  
  
 Pour plus d'informations sur l'activation de l'option **Mot de passe pour la lecture**, consultez l'Aide de Word ou Excel.  
  
## Comportement d'Excel et de Word  
 Chaque fois que vous ouvrez un classeur Excel dans Visual Studio dont l'option **Mot de passe pour la lecture** est activée, Excel vous invite à entrer le mot de passe.  Lorsque vous générez votre solution, vous serez invité à retaper le mot de passe car le document est ouvert lors de la génération.  
  
 La première fois que vous ouvrez un document Word dans Visual Studio dont l'option **Mot de passe pour la lecture** est activée, Word vous invite à entrer le mot de passe.  Après avoir entré le mot de passe correct, l'option **Mot de passe pour la lecture** est supprimée du document qui s'ouvrira désormais sans mot de passe.  Si vous souhaitez que le document dans votre solution s'ouvre à l'aide d'un mot de passe, vous devez activer l'option **Mot de passe pour la lecture** après la génération finale et avant le déploiement de la solution.  
  
## Voir aussi  
 [Protection des documents dans les solutions au niveau du document](../vsto/document-protection-in-document-level-solutions.md)   
 [Vue d'ensemble de la gestion des droits relatifs à l'information et des extensions de code managé](../vsto/information-rights-management-and-managed-code-extensions-overview.md)   
 [Comment : permettre au code de s'exécuter derrière des documents dotés d'autorisations restreintes](../vsto/how-to-permit-code-to-run-behind-documents-with-restricted-permissions.md)   
 [Conception et création de solutions Office](../vsto/designing-and-creating-office-solutions.md)  
  
  