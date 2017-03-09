---
title: "MSBuild Error MSB1011 | Microsoft Docs"
ms.custom: ""
ms.date: "11/23/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "MSBuild.AmbiguousProjectError"
helpviewer_keywords: 
  - "MSB1011"
ms.assetid: f3cb16e5-288c-4dba-941f-a0ed3bf92db7
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild Error MSB1011
**Spécifiez le fichier projet ou solution à utiliser, car ce dossier en contient plusieurs.**  
  
 Si aucun fichier projet ou solution n'est spécifié au niveau de la ligne de commande, [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] recherche dans le répertoire de travail actuel un fichier dont l'extension se termine par « proj » ou « sln » et utilise ce fichier.  Le répertoire de travail en cours contient plusieurs fichiers dont l'extension se termine par "proj" ou "sln".  
  
### Pour corriger cette erreur  
  
1.  Incluez le nom du fichier projet sur la ligne de commande.  Par exemple, au lieu d'entrer `msbuild`, tapez `msbuild myapp.proj`.  
  
## Voir aussi  
 [Command\-Line Reference](../msbuild/msbuild-command-line-reference.md)