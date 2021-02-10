---
title: CvInitProvider, fonction | Microsoft Docs
description: Consultez les informations de référence pour la fonction SDK du visualiseur concurrentiel Cvinitprovider, (bibliothèque C).
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- cvmarkers/CvInitProvider
helpviewer_keywords:
- CvInitProvider method
ms.assetid: ba1863ad-e35f-4d34-a2f2-5e68957d1915
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: f23d3ceadf2ee8d1a0c6b53b395c379caf505179
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99940993"
---
# <a name="cvinitprovider-function"></a>CvInitProvider, fonction
Initialise le fournisseur de marqueurs. Doit être appelée avant toute autre fonction du kit SDK du visualiseur concurrentiel.

## <a name="syntax"></a>Syntaxe

```C
HRESULT CvInitProvider(
   _In_ const GUID* pGuid,
   _Out_ PCV_PROVIDER* ppProvider
);
```

#### <a name="parameters"></a>Paramètres
 `pGuid` GUID du fournisseur. Ne peut pas avoir la valeur NULL.

 `ppProvider` Adresse d’une variable de sortie qui doit stocker le contexte du fournisseur. Ne peut pas avoir la valeur NULL.

## <a name="return-value"></a>Valeur retournée
 S_OK lorsque le fournisseur est correctement initialisé, ou code d’erreur en cas d’erreur. Utilisez les macros SUCCEEDED/FAILED pour vérifier la condition d’erreur.

## <a name="requirements"></a>Configuration requise
 **En-tête :** *cvmarkers.h*

## <a name="see-also"></a>Voir aussi
- [Informations de référence sur la bibliothèque C++](../profiling/cpp-library-reference.md)