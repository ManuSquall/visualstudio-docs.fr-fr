---
title: CvReleaseMarkerSeries, fonction | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- cvmarkers/CvReleaseMarkerSeries
helpviewer_keywords:
- CvReleaseMarkerSeries method
ms.assetid: 3b4711ee-e534-411d-9128-f69cd7932a48
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d100b7ff37ea5a3cd224fd420f14e4cb23061903
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/21/2019
ms.locfileid: "56630195"
---
# <a name="cvreleasemarkerseries-function"></a>CvReleaseMarkerSeries, fonction
Libère la série de marqueurs. N’utilisez pas l’objet de série de marqueurs après sa libération, car cela peut entraîner le blocage de l’application. Si la libération de la série de marqueurs échoue, une fuite de mémoire se produit.

## <a name="syntax"></a>Syntaxe

```C
HRESULT CvReleaseMarkerSeries(
   _In_reads_bytes_(16) PCV_MARKERSERIES pMarkerSeries
);
```

#### <a name="parameters"></a>Paramètres
 `pMarkerSeries` Adresse de variable objet de fournisseur. L’adresse ne peut pas être Null et la variable peut avoir n’importe quelle valeur.

## <a name="return-value"></a>Valeur de retour
 S_OK lorsque la série de marqueurs est correctement libérée, ou code d’erreur en cas d’erreur. Utilisez les macros SUCCEEDED/FAILED pour vérifier la condition d’erreur.

## <a name="requirements"></a>Spécifications
 **En-tête :** *cvmarkers.h*

## <a name="see-also"></a>Voir aussi
- [Informations de référence sur la bibliothèque C++](../profiling/cpp-library-reference.md)