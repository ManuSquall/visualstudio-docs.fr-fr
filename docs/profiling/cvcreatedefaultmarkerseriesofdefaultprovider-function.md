---
title: CvCreateDefaultMarkerSeriesOfDefaultProvider, fonction | Microsoft Docs
description: Consultez les informations de référence pour la fonction SDK du visualiseur concurrentiel Cvcreatedefaultmarkerseriesofdefaultprovider, (bibliothèque C).
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- cvmarkers/CvCreateDefaultMarkerSeriesOfDefaultProvider
helpviewer_keywords:
- CvCreateDefaultMarkerSeriesOfDefaultProvider method
ms.assetid: 24eb80f8-8fca-4c47-93b5-bb1eb8ffdffd
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 32d7730d36f7e99a2557e764c2adb92862515e24
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99941045"
---
# <a name="cvcreatedefaultmarkerseriesofdefaultprovider-function"></a>CvCreateDefaultMarkerSeriesOfDefaultProvider, fonction
Crée des séries de marqueurs par défaut d’un fournisseur par défaut.

## <a name="syntax"></a>Syntaxe

```C
HRESULT CvCreateDefaultMarkerSeriesOfDefaultProvider(
   _Out_ PCV_PROVIDER* ppProvider,
   _Out_ PCV_MARKERSERIES* ppMarkerSeries
);
```

#### <a name="parameters"></a>Paramètres
 `ppProvider` Adresse de variable objet de fournisseur. L’adresse ne peut pas être Null et la variable peut avoir n’importe quelle valeur.

 `ppMarkerSeries` Adresse de variable objet de série de marqueurs. L’adresse ne peut pas être Null et la variable peut avoir n’importe quelle valeur.

## <a name="return-value"></a>Valeur retournée
 S_OK lorsque le fournisseur et la série de marqueurs sont tous deux correctement créés, ou code d’erreur en cas d’erreur. Utilisez les macros SUCCEEDED/FAILED pour vérifier la condition d’erreur.

## <a name="requirements"></a>Configuration requise
 **En-tête :** *cvmarkers.h*

## <a name="see-also"></a>Voir aussi
- [Informations de référence sur la bibliothèque C++](../profiling/cpp-library-reference.md)