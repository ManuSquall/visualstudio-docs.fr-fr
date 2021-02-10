---
title: CvLeaveSpan, fonction | Microsoft Docs
description: Consultez les informations de référence pour la fonction SDK du visualiseur concurrentiel Cvleavespan, (bibliothèque C).
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- cvmarkers/CvLeaveSpan
helpviewer_keywords:
- CvLeaveSpan method
ms.assetid: 3bf65fdf-a471-4efd-ac7a-03e701bbae5d
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: da049fc5cc96e9eaa6830159db8c60f9469e2ac4
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99948255"
---
# <a name="cvleavespan-function"></a>CvLeaveSpan, fonction
Marque la fin de l’intervalle.

## <a name="syntax"></a>Syntaxe

```C
HRESULT CvLeaveSpan(
   _In_ PCV_SPAN pSpan
);
```

#### <a name="parameters"></a>Paramètres
 `pSpan` Objet d’intervalle retourné par un appel précédent à CvEnterSpan*. Ne peut pas avoir la valeur NULL.

## <a name="return-value"></a>Valeur de retour
 S_OK lorsque le message est correctement écrit. Code d’erreur en cas d’erreur. Utilisez les macros SUCCEEDED/FAILED pour vérifier la condition d’erreur.

## <a name="requirements"></a>Configuration requise
 **En-tête :** *cvmarkers.h*

## <a name="see-also"></a>Voir aussi
- [Informations de référence sur la bibliothèque C++](../profiling/cpp-library-reference.md)