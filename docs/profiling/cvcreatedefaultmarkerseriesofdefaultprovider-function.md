---
title: "CvCreateDefaultMarkerSeriesOfDefaultProvider, fonction | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "cvmarkers/CvCreateDefaultMarkerSeriesOfDefaultProvider"
helpviewer_keywords: 
  - "CvCreateDefaultMarkerSeriesOfDefaultProvider (méthode)"
ms.assetid: 24eb80f8-8fca-4c47-93b5-bb1eb8ffdffd
caps.latest.revision: 2
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 2
---
# CvCreateDefaultMarkerSeriesOfDefaultProvider, fonction
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Crée la série de marqueurs par défaut d'un fournisseur par défaut.  
  
## Syntaxe  
  
```  
HRESULT CvCreateDefaultMarkerSeriesOfDefaultProvider(  
   _Out_ PCV_PROVIDER* ppProvider,  
   _Out_ PCV_MARKERSERIES* ppMarkerSeries  
);  
```  
  
#### Paramètres  
 `ppProvider`  
 Adresse de la variable d'objet fournisseur.  L'adresse ne peut pas être NULL, la variable peut avoir n'importe quelle valeur.  
  
 `ppMarkerSeries`  
 Adresse de la variable objet de série de marqueurs.  L'adresse ne peut pas être NULL, la variable peut avoir n'importe quelle valeur.  
  
## Valeur de retour  
 S\_OK lorsque les séries de fournisseurs et de marqueurs sont correctement créées ou un code d'erreur au cas où il y aurait eu une ou plusieurs erreurs.  Utiliser les macros SUCCEEDED\/FAILED pour vérifier la condition d'erreur.  
  
## Configuration requise  
 **En\-tête :** cvmarkers.h  
  
## Voir aussi  
 [Référence de bibliothèque C\+\+](../profiling/cpp-library-reference.md)