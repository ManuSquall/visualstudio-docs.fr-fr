---
title: "CvInitProvider, fonction | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "cvmarkers/CvInitProvider"
helpviewer_keywords: 
  - "CvInitProvider (méthode)"
ms.assetid: ba1863ad-e35f-4d34-a2f2-5e68957d1915
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# CvInitProvider, fonction
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Initialise le fournisseur de jeton.  Doit être appelé avant tout autre fonction du kit de développement logiciel du visualiseur concurrentiel  
  
## Syntaxe  
  
```  
HRESULT CvInitProvider(  
   _In_ const GUID* pGuid,  
   _Out_ PCV_PROVIDER* ppProvider  
);  
```  
  
#### Paramètres  
 `pGuid`  
 GUID du fournisseur.  Ne peut pas être NULL.  
  
 `ppProvider`  
 Adresse d'une variable de sortie qui stockera le contexte de fournisseur.  Ne peut pas être NULL.  
  
## Valeur de retour  
 S\_OK lorsque le fournisseur est correctement initialisé ou un code d'erreur dans le cas d'une erreur.  Utiliser la macros SUCCEEDED\/FAILED pour vérifier la condition d'erreur.  
  
## Configuration requise  
 **en\-tête :** cvmarkers.h  
  
## Voir aussi  
 [Référence de bibliothèque C\+\+](../profiling/cpp-library-reference.md)