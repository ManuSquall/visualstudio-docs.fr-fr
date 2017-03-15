---
title: "CvCreateMarkerSeriesWithCodePageA, fonction | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "cvmakers/CvCreateMarkerSeriesWithCodePageA"
helpviewer_keywords: 
  - "CvCreateMarkerSeriesWithCodePageA (méthode)"
ms.assetid: 3d7ed601-2222-4be9-a557-f217db008753
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# CvCreateMarkerSeriesWithCodePageA, fonction
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Crée une série de marqueur pour un fournisseur donné et une page de code spécifiée.  Cette fonction peut être utilisée pour spécifier la page de code explicitement pour le texte saisi par des fonctions ANSI API de marqueur.  La définition de la page de codes peut être utile au cas où la trace est capturée puis analysée sur des ordinateurs avec des paramètres régionaux\/langages différents.  Par défaut la page de code retournée par la fonction GetACP\(\) est utilisée.  
  
## Syntaxe  
  
```  
HRESULT CvCreateMarkerSeriesWithCodePageA(  
   _In_ PCV_PROVIDER pProvider,  
   _In_ LPCSTR pSeriesName,  
   _In_ UINT nTextCodePage,  
   _Out_ PCV_MARKERSERIES* ppMarkerSeries  
);  
```  
  
#### Paramètres  
 `pProvider`  
 Objet fournisseur déjà initialisé par CvInitProvider.  Ne peut pas être NULL.  
  
 `pSeriesName`  
 Nom de série d'un marqueur.  Ne peut pas être NULL mais une chaîne vide est autorisée.  
  
 `nTextCodePage`  
 Page de code valide.  
  
 `ppMarkerSeries`  
 Adresse d'une variable de sortie qui stockera le contexte du marqueur des séries.  Ne peut pas être NULL.  
  
## Valeur de retour  
 S\_OK lorsque la série de marqueur est correctement créée ou un code d'erreur dans le cas où il y a une erreur.  Utiliser les macros SUCCEEDED\/FAILED pour vérifier la condition d'erreur.  
  
## Configuration requise  
 **En\-tête :** cvmarkers.h  
  
## Voir aussi  
 [Référence de bibliothèque C\+\+](../profiling/cpp-library-reference.md)