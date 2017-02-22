---
title: "Groupes, les Menus et les commandes d&#233;finies par l’IDE | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "commandes, définies par l’environnement"
  - "fichiers .vsct, constantes définies par l’environnement"
  - "groupes de commandes, définies par l’environnement"
ms.assetid: 86b3af13-7163-48c6-986b-7beeedbc26cc
caps.latest.revision: 27
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 27
---
# Groupes, les Menus et les commandes d&#233;finies par l’IDE
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Nombreux menus, les commandes et les groupes de commandes sont déjà définies pour une utilisation par le [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE. Ces commandes sont également disponibles lorsque vous étendez [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
## Rechercher les commandes définies par l’environnement  
 Les commandes d’environnement sont définies dans un jeu de quatre fichiers .vsct :  
  
-   SharedCmdDef.vsct  
  
-   SharedCmdPlace.vsct  
  
-   ShellCmdDef.vsct  
  
-   ShellCmdPlace.vsct  
  
 Ces fichiers se trouvent dans *\< chemin d’installation de Visual Studio SDK \>*\\VisualStudioIntegration\\Common\\Inc\\. Ces fichiers fournissent les définitions et les GUID des menus et des groupes que vous pouvez utiliser dans le fichier de configuration \(.vsct\) de table de commande de votre VSPackage en tant que conteneurs pour vos propres menus, les groupes et commandes.  
  
## Dans cette section  
 [GUID et ID de Menus de Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-menus.md)  
 Fournit les valeurs GUID et l’ID de menus dans la barre de menus de Visual Studio et les groupes qu’elles contiennent.  
  
 [GUID et ID des barres d'outils de Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-toolbars.md)  
 Fournit les valeurs GUID et l’ID de barres d’outils dans l’IDE de Visual Studio et les groupes qu’elles contiennent.  
  
 [GUID et ID de commandes de Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-commands.md)  
 Fournit les valeurs GUID et l’ID de commandes définies par l’IDE Visual Studio.  
  
## Voir aussi  
 [Table de commandes de Visual Studio \(. Fichiers VSCT\)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)   
 [Commandes définies par l'IDE pour l'extension des systèmes de projet](../../extensibility/internals/ide-defined-commands-for-extending-project-systems.md)   
 [Comment ajouter des éléments d'Interface utilisateur dans les packages VS](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)