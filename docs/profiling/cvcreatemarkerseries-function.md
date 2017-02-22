---
title: "CvCreateMarkerSeries, fonction | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "cvmarkers/CvCreateMarkerSeriesA"
  - "cvmarkers/CvCreateMarkerSeriesW"
helpviewer_keywords: 
  - "CvCreateMarkerSeriesA (méthode)"
  - "CvCreateMarkerSeriesW (méthode)"
ms.assetid: e280530b-137a-43a7-8643-aa514ab86ed7
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# CvCreateMarkerSeries, fonction
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Crée des séries de marqueur pour un fournisseur donné.  
  
## Syntaxe  
  
```  
_Check_return_ HRESULT CvCreateMarkerSeriesW(  
    _In_ PCV_PROVIDER  pProvider,  
    _In_ LPCWSTR pSeriesName,  
    _Out_ PCV_MARKERSERIES* ppMarkerSeries);  
  
_Check_return_ HRESULT CvCreateMarkerSeriesA(  
    _In_ PCV_PROVIDER  pProvider,  
    _In_ LPCSTR pSeriesName,  
    _Out_ PCV_MARKERSERIES* ppMarkerSeries);  
```  
  
#### Paramètres  
 `pProvider`  
 Objet fournisseur déjà initialisé par CvInitProvider.  Ne peut pas être NULL.  
  
 `pSeriesName`  
 Nom de série d'un marqueur.  Ne peut pas être NULL mais une chaîne vide est autorisée.  
  
 `ppMarkerSeries`  
 Adresse d'une variable de sortie qui stockera le contexte du marqueur des séries.  Ne peut pas être NULL.  
  
## Valeur de retour  
 S\_OK lorsque la série de marqueur est correctement créée ou un code d'erreur dans le cas où il y a une erreur.  Utiliser la macros SUCCEEDED\/FAILED pour vérifier la condition d'erreur.  
  
## Configuration requise  
 **en\-tête :** cvmarkers.h  
  
 **Unicode :** CvCreateMarkerSeriesW  
  
 **ANSI :** CvCreateMarkerSeriesA  
  
## Voir aussi  
 [Référence de bibliothèque C\+\+](../profiling/cpp-library-reference.md)