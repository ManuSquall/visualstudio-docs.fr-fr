---
title: "CvReleaseProvider, fonction | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "cvmarkers/CvReleaseProvider"
helpviewer_keywords: 
  - "CvReleaseProvider (méthode)"
ms.assetid: 8d74379e-295d-452b-bd5f-0769df387d4f
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# CvReleaseProvider, fonction
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Libère le fournisseur de jeton.  Libérer le fournisseur de jeton n'affecte pas la série créée précédemment de jeton de ce fournisseur.  La série de jeton doit être version séparée par l'appel de CvReleaseMarkerSeries.  Échec de libérer les causes de fournisseur une fuite de mémoire.  
  
## Syntaxe  
  
```  
HRESULT CvReleaseProvider(  
   _In_ PCV_PROVIDER pProvider  
);  
```  
  
#### Paramètres  
 `pProvider`  
 Contexte de fournisseur.  Ne peut pas être NULL.  
  
## Valeur de retour  
 S\_OK lorsque le fournisseur est correctement initialisé ou un code d'erreur dans le cas d'une erreur.  Utiliser la macros SUCCEEDED\/FAILED pour vérifier la condition d'erreur.  
  
## Configuration requise  
 **en\-tête :** cvmarkers.h  
  
## Voir aussi  
 [Référence de bibliothèque C\+\+](../profiling/cpp-library-reference.md)