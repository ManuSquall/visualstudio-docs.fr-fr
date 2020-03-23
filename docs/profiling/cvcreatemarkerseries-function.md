---
title: CvCreateMarkerSeries, fonction | Microsoft Docs
ms.date: 11/04/2016
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: eb3ef4d928aaac57f39a48e5be212c1148ef58eb
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/18/2020
ms.locfileid: "62552679"
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
 `pProvider` Objet fournisseur initialisé par CvInitProvider. Ne peut pas avoir la valeur NULL.

 `pSeriesName` Nom de la série de marqueurs. Ne peut pas être Null, mais une chaîne vide est acceptée.

 `ppMarkerSeries` Adresse d’une variable de sortie qui doit stocker le contexte de la série de marqueurs. Ne peut pas avoir la valeur NULL.

## <a name="return-value"></a>Valeur retournée
 S_OK lorsque la série de marqueurs est correctement créée, ou code d’erreur en cas d’erreur. Utilisez les macros SUCCEEDED/FAILED pour vérifier la condition d’erreur.

## <a name="requirements"></a>Spécifications
 **En-tête :** *cvmarkers.h*

 **Unicode** : CvCreateMarkerSeriesW

 **ANSI** : CvCreateMarkerSeriesA

## <a name="see-also"></a>Voir aussi
- [Référence de la bibliothèque de CMD](../profiling/cpp-library-reference.md)