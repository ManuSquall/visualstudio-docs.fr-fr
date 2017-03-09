---
title: "Utilisez &#39;FilePutObject&#39; &#224; la place de &#39;FilePut&#39; quand l’argument est de type &#39;Object&#39;. | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbrUseFilePutObject"
ms.assetid: d207b9b7-5898-4c13-8b03-9feefac5f726
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Utilisez &#39;FilePutObject&#39; &#224; la place de &#39;FilePut&#39; quand l’argument est de type &#39;Object&#39;.
La méthode `FilePut` comprend un argument de type`Object`.`FilePutObject` doit être utilisé à la place de `FilePut` pour éviter toute ambiguïté.  
  
### Pour corriger cette erreur  
  
-   Remplacez `FilePut` par `FilePutObject`.  
  
-   Effectuez un cast sur le type de l’argument `Object` pour en faire un type plus spécifique.  
  
-   Utilisez les fonctionnalités disponibles dans l’objet `My.Computer.FileSystem`.  
  
## Voir aussi  
 [NOT IN BUILD: FilePutObject \(fonction\)](http://msdn.microsoft.com/fr-fr/a0f52a1c-5ecc-4945-b18c-03147af61d6b)   
 [My.Computer.FileSystem Object](/dotnet/visual-basic/language-reference/objects/my-computer-filesystem-object)   
 [My.Computer.FileSystem.WriteAllBytes, méthode](http://msdn.microsoft.com/fr-fr/b1a24dc1-eac8-4e22-8ffa-cc3bacbaf826)