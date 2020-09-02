---
title: CvIsEnabled, fonction | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- cvmarkers/CvIsEnabledEx
- cvmarkers/CvIsEnabled
helpviewer_keywords:
- CvIsEnabled method
- CvIsEnabledEx method
ms.assetid: 2e4fea6d-758d-4150-8744-6102a1d58c1c
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 53de9ee136c9bd12c732339b4c1c8a223fe1a3ac
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85330058"
---
# <a name="cvisenabled-function"></a>CvIsEnabled, fonction
Détermine si une session a activé le fournisseur ETW spécifié.

## <a name="syntax"></a>Syntaxe

```C
HRESULT CvIsEnabled(
   _In_ PCV_PROVIDER pProvider
);
HRESULT CvIsEnabledEx(
   _In_ PCV_PROVIDER pProvider,
   _In_ CV_IMPORTANCE level,
   _In_ int category
);
```

#### <a name="parameters"></a>Paramètres
 `category` Catégorie.

 `level` Niveau d’importance.

 `pProvider` Objet fournisseur valide. Ne peut pas avoir la valeur NULL.

## <a name="return-value"></a>Valeur retournée
 S_OK si le fournisseur est activé. S_FALSE si le fournisseur est désactivé. Code d’erreur en cas d’erreur. Utilisez la macro FAILED pour vérifier la condition d’erreur, puis recherchez S_OK/S_FALSE.

## <a name="requirements"></a>Spécifications
 **En-tête :** *cvmarkers.h*

## <a name="see-also"></a>Voir aussi
- [Informations de référence sur la bibliothèque C++](../profiling/cpp-library-reference.md)