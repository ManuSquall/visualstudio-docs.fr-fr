---
title: "Erreur MSBuild MSB8031 | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "MSB8031"
ms.assetid: ebfaca51-fd91-4b04-8194-b4fdededd5fe
caps.latest.revision: 4
caps.handback.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Erreur MSBuild MSB8031
MSB8031  
  
 Pour utiliser l'encodage MBCS dans les projets MFC, vous devez télécharger et installer une bibliothèque supplémentaire.  
  
 Les versions MBCS des DLL MFC ne sont pas incluses dans Visual Studio, mais elles sont disponibles dans le composant complémentaire DLL MFC MBCS, que vous pouvez télécharger si vous êtes un client de Visual Studio.  Si vous n'installez pas le composant complémentaire et si vous tentez de générer un projet MFC qui utilise le jeu de caractères MBCS, l'éditeur de liens ne trouvera pas les DLL et la génération échouera.  
  
### Pour corriger cette erreur  
  
1.  [Téléchargez le composant additionnel MBCS DLL MFC](http://go.microsoft.com/fwlink/?LinkId=299009) à partir du Centre de téléchargement MSDN, ou si cela est plus pratique, convertissez votre projet en jeu de caractères Unicode.  
  
## Voir aussi  
 [MFC MBCS DLL, complément](/visual-cpp/mfc/mfc-mbcs-dll-add-on)