---
title: "CvIsEnabled, fonction | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "cvmarkers/CvIsEnabledEx"
  - "cvmarkers/CvIsEnabled"
helpviewer_keywords: 
  - "CvIsEnabled (méthode)"
  - "CvIsEnabledEx (méthode)"
ms.assetid: 2e4fea6d-758d-4150-8744-6102a1d58c1c
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# CvIsEnabled, fonction
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Détermine si une session a activé le fournisseur ETW spécifié.  
  
## Syntaxe  
  
```  
HRESULT CvIsEnabled(  
   _In_ PCV_PROVIDER pProvider  
);  
HRESULT CvIsEnabledEx(  
   _In_ PCV_PROVIDER pProvider,  
   _In_ CV_IMPORTANCE level,  
   _In_ int category  
);  
```  
  
#### Paramètres  
 `category`  
 Catégorie.  
  
 `level`  
 Niveau d'importance.  
  
 `pProvider`  
 Objet fournisseur valide.  Ne peut pas être NULL.  
  
## Valeur de retour  
 S\_OK si le fournisseur est actuellement activé.  S\_FALSE si le fournisseur est actuellement désactivé.  Code d'erreur au cas où il y a eu des erreurs.  Utilisez la macro FAILED pour vérifier la condition d'erreur puis pour vérifier le S\_OK\/S\_FALSE.  
  
## Configuration requise  
 **En\-tête :** cvmarkers.h  
  
## Voir aussi  
 [Référence de bibliothèque C\+\+](../profiling/cpp-library-reference.md)