---
title: "CvReleaseMarkerSeries, fonction | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "cvmarkers/CvReleaseMarkerSeries"
helpviewer_keywords: 
  - "CvReleaseMarkerSeries (méthode)"
ms.assetid: 3b4711ee-e534-411d-9128-f69cd7932a48
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# CvReleaseMarkerSeries, fonction
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Libère la série de marqueur.  N'utilisez pas l'objet série de marqueurs après l'avoir libéré sinon l'application peut tomber en panne.  L'échec pour libérer la série de marqueurs provoque une fuite de mémoire.  
  
## Syntaxe  
  
```  
HRESULT CvReleaseMarkerSeries(  
   _In_reads_bytes_(16) PCV_MARKERSERIES pMarkerSeries  
);  
```  
  
#### Paramètres  
 `pMarkerSeries`  
 Adresse de la variable d'objet fournisseur.  L'adresse ne peut pas être NULL, la variable peut avoir n'importe quelle valeur.  
  
## Valeur de retour  
 S\_OK lorsque la série de marqueur est correctement libérée ou un code d'erreur dans le cas où il y a une erreur.  Utiliser les macros SUCCEEDED\/FAILED pour vérifier la condition d'erreur.  
  
## Configuration requise  
 **En\-tête :** cvmarkers.h  
  
## Voir aussi  
 [Référence de bibliothèque C\+\+](../profiling/cpp-library-reference.md)