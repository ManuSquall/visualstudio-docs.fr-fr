---
title: CvCreateMarkerSeries, fonction | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- cvmarkers/CvCreateMarkerSeriesA
- cvmarkers/CvCreateMarkerSeriesW
helpviewer_keywords:
- CvCreateMarkerSeriesA method
- CvCreateMarkerSeriesW method
ms.assetid: e280530b-137a-43a7-8643-aa514ab86ed7
caps.latest.revision: 8
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 6dc4af6ef3b2ffc89ec0e69a6dd63923f5c55ffe
ms.sourcegitcommit: a83c60bb00bf95e6bea037f0e1b9696c64deda3c
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 02/19/2019
ms.locfileid: "54793956"
---
# <a name="cvcreatemarkerseries-function"></a>CvCreateMarkerSeries, fonction
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Crée des séries de marqueurs pour un fournisseur donné.  
  
## <a name="syntax"></a>Syntaxe  
  
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
  
#### <a name="parameters"></a>Paramètres  
 `pProvider`  
 Objet fournisseur précédemment initialisé par CvInitProvider. Ne peut pas être Null.  
  
 `pSeriesName`  
 Nom de la série de marqueurs. Ne peut pas être Null, mais une chaîne vide est acceptée.  
  
 `ppMarkerSeries`  
 Adresse d’une variable de sortie qui doit stocker le contexte de la série de marqueurs. Ne peut pas être Null.  
  
## <a name="return-value"></a>Valeur de retour  
 S_OK lorsque la série de marqueurs est correctement créée, ou code d’erreur en cas d’erreur. Utilisez les macros SUCCEEDED/FAILED pour vérifier la condition d’erreur.  
  
## <a name="requirements"></a>Spécifications  
 **En-tête** : cvmarkers.h  
  
 **Unicode** : CvCreateMarkerSeriesW  
  
 **ANSI** : CvCreateMarkerSeriesA  
  
## <a name="see-also"></a>Voir aussi  
 [Informations de référence sur la bibliothèque C++](../profiling/cpp-library-reference.md)
