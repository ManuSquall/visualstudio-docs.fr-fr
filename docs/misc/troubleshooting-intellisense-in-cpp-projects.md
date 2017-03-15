---
title: "D&#233;pannage d&#39;IntelliSense dans les projets C++ | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "fichiers .ncb"
  - "IntelliSense, dépannage (échec dans des projets C++)"
  - "fichiers ncb"
  - "dépanner IntelliSense"
  - "dépanner Visual C++, IntelliSense"
ms.assetid: 72e4eb39-66d3-403d-8da7-00ed288a1899
caps.latest.revision: 20
caps.handback.revision: 20
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# D&#233;pannage d&#39;IntelliSense dans les projets C++
IntelliSense peut cesser de fonctionner dans certaines conditions.  Procédez comme suit pour tenter de déterminer la raison pour laquelle IntelliSense ne fonctionne pas pour vos projets C\+\+.  
  
### Pour analyser l'échec d'IntelliSense dans les projets C\+\+  
  
1.  Vérifiez que le projet Visual C\+\+ ne contient pas d'erreurs de compilation.  
  
    1.  Si le projet est un projet Makefile, consultez [Comment : activer IntelliSense pour des projets Makefile](../Topic/How%20to:%20Enable%20IntelliSense%20for%20Makefile%20Projects.md).  
  
2.  Assurez\-vous que stdafx.h figure dans le chemin d'accès Include.  Pour plus d'informations sur les chemins d'accès Include dans les projets Visual C\+\+, consultez [\#include, directive](/visual-cpp/preprocessor/hash-include-directive-c-cpp) et [\/I \(Autres répertoires Include\)](/visual-cpp/build/reference/i-additional-include-directories).  
  
## Limites d'IntelliSense  
 IntelliSense ne fonctionne pas dans les projets C\+\+ dans les circonstances suivantes :  
  
-   Le curseur est dans un commentaire de code.  
  
-   Vous écrivez un littéral de chaîne.  
  
-   Une erreur de syntaxe apparaît au\-dessus du curseur.  
  
-   La solution consiste à utiliser la syntaxe du C\+\+ managé ou la précédente syntaxe des extensions managées pour C\+\+.  
  
-   IntelliSense n'est pas complètement pris en charge lorsque vous référencez plusieurs fois un fichier d'en\-tête à l'aide de la directive `#include` et que la signification de ce fichier d'en\-tête varie en raison de différents états de macro définis via la directive `#define`.  En d'autres termes, lorsque vous incluez plusieurs fois un fichier d'en\-tête et que l'utilisation de l'en\-tête varie selon les différents états de macro, IntelliSense ne fonctionne pas toujours.  
  
## Voir aussi  
 [Troubleshooting IntelliSense](http://msdn.microsoft.com/fr-fr/c1b3adb9-0d48-4770-a51e-392ed818c484)   
 [Comment : organiser des fichiers de sortie de projet pour les générations](../Topic/How%20to:%20Organize%20Project%20Output%20Files%20for%20Builds.md)