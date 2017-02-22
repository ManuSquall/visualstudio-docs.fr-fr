---
title: "CvWriteAlert, fonction | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "cvmarkers/CvWriteAlertVA"
  - "cvmarkers/CvWriteAlertVW"
  - "cvmarkers/CvWriteAlertA"
  - "cvmarkers/CvWriteAlertW"
helpviewer_keywords: 
  - "CvWriteAlertVW (méthode)"
  - "CvWriteAlertA (méthode)"
  - "CvWriteAlertVA (méthode)"
  - "CvWriteAlertW (méthode)"
ms.assetid: 937aa9d6-278a-4df3-bef7-151441df16d5
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# CvWriteAlert, fonction
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Écrit une alerte dans le fichier de suivi du visualiseur concurrentiel.  
  
## Syntaxe  
  
```  
HRESULT CvWriteAlertW(  
    _In_reads_bytes_(16) PCV_MARKERSERIES pMarkerSeries,  
    _In_ PCWSTR pMessage,  
    ...  
    );  
  
HRESULT CvWriteAlertA(  
    _In_reads_bytes_(16) PCV_MARKERSERIES pMarkerSeries,  
    _In_ PCSTR pMessage,  
    ...  
    );  
  
HRESULT CvWriteAlertVW(  
    _In_reads_bytes_(16) PCV_MARKERSERIES pMarkerSeries,  
    _In_ PCWSTR pMessage,  
    _In_ va_list argList);  
  
HRESULT CvWriteAlertVA(  
    _In_reads_bytes_(16) PCV_MARKERSERIES pMarkerSeries,  
    _In_ PCSTR pMessage,  
    _In_ va_list argList);  
```  
  
#### Paramètres  
 `argList`  
 Liste d'arguments.  
  
 `pMarkerSeries`  
 Contexte de marqueur de série valide  Ne peut pas être NULL.  
  
 `pMessage`  
 Chaîne de format du message.  Ne peut pas être NULL.  
  
## Valeur de retour  
 S\_OK lorsque le message est correctement écrit.  Code d'erreur au cas où il y a des erreurs.  Utiliser la macros SUCCEEDED\/FAILED pour vérifier la condition d'erreur.  
  
## Configuration requise  
 **en\-tête :** cvmarkers.h  
  
 **Unicode :** CvWriteAlertW, CvWriteAlertVW  
  
 **ANSI :** CvWriteAlertA, CvWriteAlertVA  
  
## Voir aussi  
 [Référence de bibliothèque C\+\+](../profiling/cpp-library-reference.md)