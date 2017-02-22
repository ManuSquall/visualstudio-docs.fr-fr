---
title: "Inscrire des extensions du&#160;.NET Framework | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Ajouter des références, boîte de dialogue, inscrire des extensions du .NET Framework"
  - "MSBuild, inscrire des extensions du .NET Framework"
  - "extensions du .NET Framework, inscrire"
ms.assetid: deee6f53-ea87-4b88-a120-bea589822e03
caps.latest.revision: 5
caps.handback.revision: 5
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Inscrire des extensions du&#160;.NET Framework
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Vous pouvez développer un assembly qui étend une version spécifique du .NET Framework.  Pour permettre à l'assembly de s'afficher dans la boîte de dialogue **Ajouter des références** de Visual Studio, vous devez ajouter le dossier qui le contient à la base de registres.  
  
 Par exemple, supposez que la société Trey Research ait développé une bibliothèque qui étend le .NET Framework 4 et souhaite que les assemblys de bibliothèque s'affichent dans la boîte de dialogue **Ajouter des références** lorsqu'un projet cible le .NET Framework 4.  Supposez également que les assemblys sont des assemblys 32 bits s'exécutant sur un ordinateur 32 bits ou des assemblys 64 bits s'exécutant sur un ordinateur 64 bits, et qu'ils seront installés dans le dossier C:\\TreyResearch\\Extensions4\\.  
  
 Inscrivez ce dossier à l'aide de cette clé : HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\.NETFramework\\v4.0.21006\\AssemblyFoldersEx\\TreyResearch\\.  La valeur par défaut de cette clé doit être : C:\\TreyResearch\\Extensions4.  
  
> [!NOTE]
>  Le numéro de build de la version du .NET Framework peut être différent.  
  
 Pour inscrire un assembly 32 bits sur un ordinateur 64 bits, utilisez le nœud Wow6432, par exemple : HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Wow6432Node\\Microsoft\\.NETFramework\\v4.0.21006\\AssemblyFoldersEx\\TreyResearch\\.  
  
## Voir aussi  
 [Intégration Visual Studio](../msbuild/visual-studio-integration-msbuild.md)