---
title: "CvWriteFlag, fonction | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "cvmarkers/CvWriteFlagExVA"
  - "cvmarkers/CvWriteFlagExW"
  - "cvmarkers/CvWriteFlagExVW"
  - "cvmarkers/CvWriteFlagExA"
helpviewer_keywords: 
  - "CvWriteFlagExW (méthode)"
  - "CvWriteFlagExVA (méthode)"
  - "CvWriteFlagExA (méthode)"
  - "CvWriteFlagExVW (méthode)"
ms.assetid: ee9da1e2-7b34-4cba-81e2-215d25d32e4d
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# CvWriteFlag, fonction
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Écrit un indicateur dans le fichier de suivi du visualiseur concurrentiel.  
  
## Syntaxe  
  
```  
HRESULT CvWriteFlagExW(  
    _In_reads_bytes_(16) PCV_MARKERSERIES pMarkerSeries,  
    _In_ CV_IMPORTANCE level,  
    _In_ int category,  
    _In_ PCWSTR pMessage,  
    ...  
    );  
  
HRESULT CvWriteFlagExA(  
    _In_reads_bytes_(16) PCV_MARKERSERIES pMarkerSeries,  
    _In_ CV_IMPORTANCE level,  
    _In_ int category,  
    _In_ PCSTR pMessage,  
    ...  
    );  
  
HRESULT CvWriteFlagExVW(  
    _In_reads_bytes_(16) PCV_MARKERSERIES pMarkerSeries,  
    _In_ CV_IMPORTANCE level,  
    _In_ int category,  
    _In_ PCWSTR pMessage,  
    _In_ va_list argList);  
  
HRESULT CvWriteFlagExVA(  
    _In_reads_bytes_(16) PCV_MARKERSERIES pMarkerSeries,  
    _In_ CV_IMPORTANCE level,  
    _In_ int category,  
    _In_ PCSTR pMessage,  
    _In_ va_list argList);  
```  
  
#### Paramètres  
 `argList`  
 Liste d'arguments.  
  
 `category`  
 Catégorie.  
  
 `level`  
 Niveau d'importance.  
  
 `pMarkerSeries`  
 Contexte de marqueur de série valide  Ne peut pas être NULL.  
  
 `pMessage`  
 Chaîne de format du message.  Ne peut pas être NULL.  
  
## Valeur de retour  
 S\_OK lorsque le message est correctement écrit.  Code d'erreur au cas où il y a des erreurs.  Utiliser la macros SUCCEEDED\/FAILED pour vérifier la condition d'erreur.  
  
## Configuration requise  
 **en\-tête :** cvmarkers.h  
  
 **Unicode :** CvWriteFlagExW, CvWriteFlagExVW  
  
 **ANSI :**CvWriteFlagExA, CvWriteFlagExVA  
  
## Voir aussi  
 [Référence de bibliothèque C\+\+](../profiling/cpp-library-reference.md)