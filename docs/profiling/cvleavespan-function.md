---
title: "CvLeaveSpan, fonction | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "cvmarkers/CvLeaveSpan"
helpviewer_keywords: 
  - "CvLeaveSpan (méthode)"
ms.assetid: 3bf65fdf-a471-4efd-ac7a-03e701bbae5d
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# CvLeaveSpan, fonction
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Marque la fin de l'étendue.  
  
## Syntaxe  
  
```  
HRESULT CvLeaveSpan(  
   _In_ PCV_SPAN pSpan  
);  
```  
  
#### Paramètres  
 `pSpan`  
 Objet d'étendue retourné par l'appel précédent à CvEnterSpan\*.  Ne peut pas être NULL.  
  
## Valeur de retour  
 S\_OK lorsque le message est correctement écrit.  Code d'erreur au cas où il y a eu des erreurs.  Utiliser les macros SUCCEEDED\/FAILED pour vérifier la condition d'erreur.  
  
## Configuration requise  
 **En\-tête :** cvmarkers.h  
  
## Voir aussi  
 [Référence de bibliothèque C\+\+](../profiling/cpp-library-reference.md)