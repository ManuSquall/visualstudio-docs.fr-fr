---
title: CvWriteAlert, fonction | Microsoft Docs
description: Consultez les informations de référence pour la fonction SDK du visualiseur concurrentiel Cvwritealert, (bibliothèque C).
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- cvmarkers/CvWriteAlertVA
- cvmarkers/CvWriteAlertVW
- cvmarkers/CvWriteAlertA
- cvmarkers/CvWriteAlertW
helpviewer_keywords:
- CvWriteAlertVW method
- CvWriteAlertA method
- CvWriteAlertVA method
- CvWriteAlertW method
ms.assetid: 937aa9d6-278a-4df3-bef7-151441df16d5
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: eb2cc6f7408fc5d9af0215dbccf166477876ac23
ms.sourcegitcommit: d13f7050c873b6284911d1f4acf07cfd29360183
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/22/2021
ms.locfileid: "98686439"
---
# <a name="cvwritealert-function"></a>CvWriteAlert, fonction
Écrit une alerte dans le fichier de trace du visualiseur concurrentiel.

## <a name="syntax"></a>Syntaxe

```C
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

#### <a name="parameters"></a>Paramètres
 `argList` Liste d’arguments.

 `pMarkerSeries` Contexte valide de la série de marqueurs. Ne peut pas avoir la valeur NULL.

 `pMessage` Chaîne de format de message. Ne peut pas avoir la valeur NULL.

## <a name="return-value"></a>Valeur retournée
 S_OK lorsque le message est correctement écrit. Code d’erreur en cas d’erreur. Utilisez les macros SUCCEEDED/FAILED pour vérifier la condition d’erreur.

## <a name="requirements"></a>Spécifications
 **En-tête :** *cvmarkers.h*

 **Unicode** : CvWriteAlertW, CvWriteAlertVW

 **ANSI** : CvWriteAlertA, CvWriteAlertVA

## <a name="see-also"></a>Voir aussi
- [Informations de référence sur la bibliothèque C++](../profiling/cpp-library-reference.md)