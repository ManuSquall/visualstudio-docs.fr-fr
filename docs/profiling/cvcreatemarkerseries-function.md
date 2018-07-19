---
title: CvCreateMarkerSeries, fonction | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- cvmarkers/CvCreateMarkerSeriesA
- cvmarkers/CvCreateMarkerSeriesW
helpviewer_keywords:
- CvCreateMarkerSeriesA method
- CvCreateMarkerSeriesW method
ms.assetid: e280530b-137a-43a7-8643-aa514ab86ed7
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 55dd6658aca332937299b2301d8294081bc7d3fd
ms.sourcegitcommit: 58052c29fc61c9a1ca55a64a63a7fdcde34668a4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2018
ms.locfileid: "34750202"
---
# <a name="cvcreatemarkerseries-function"></a>CvCreateMarkerSeries, fonction
Crée des séries de marqueurs pour un fournisseur donné.  
  
## <a name="syntax"></a>Syntaxe  
  
```C  
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
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** *cvmarkers.h*  
  
 **Unicode** : CvCreateMarkerSeriesW  
  
 **ANSI** : CvCreateMarkerSeriesA  
  
## <a name="see-also"></a>Voir aussi  
 [Informations de référence sur la bibliothèque C++](../profiling/cpp-library-reference.md)