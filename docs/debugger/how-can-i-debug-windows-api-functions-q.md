---
title: "Comment puis-je d&#233;boguer des fonctions API Windows&#160;? | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.api"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "C++"
helpviewer_keywords: 
  - "API, débogage"
  - "déboguer (C++), fonctions API Windows"
  - "symboles NT et débogage de fonctions de l'API Windows"
  - "fonctions API Windows, débogage"
  - "API Windows, déboguer les fonctions API"
ms.assetid: 7c126f57-62ab-4d94-9805-632d696ba1f0
caps.latest.revision: 20
caps.handback.revision: 20
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Comment puis-je d&#233;boguer des fonctions API Windows&#160;?
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Si vous voulez déboguer une fonction API Windows qui a chargé les symboles NT, vous devez effectuer les opérations suivantes.  
  
### Pour définir un point d'arrêt sur une fonction API Windows qui a chargé des symboles NT  
  
-   Entrez le nom de la fonction ainsi que le nom du fichier DLL dans lequel la fonction réside.  Dans du code 32 bits, utilisez la forme décorée du nom de la fonction.  Pour définir un point d'arrêt sur **MessageBeep**, par exemple, vous devez entrer ce qui suit :  
  
    ```  
    {,,USER32.DLL}_MessageBeep@4  
    ```  
  
     Pour obtenir le nom décoré, consultez [Viewing Decorated Names](http://msdn.microsoft.com/fr-fr/f79e2717-a4db-4d12-a689-69830cce2be0).  
  
## Voir aussi  
 [Forum Aux Questions sur le débogage du code natif](../debugger/debugging-native-code-faqs.md)   
 [Débogage du code natif](../debugger/debugging-native-code.md)