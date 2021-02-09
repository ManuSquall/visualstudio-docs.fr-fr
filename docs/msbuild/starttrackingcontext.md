---
title: StartTrackingContext | Microsoft Docs
description: Découvrez les paramètres, les exigences et la valeur de retour pour MSBuild StartTrackingContext, qui démarre un contexte de suivi.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
apiname:
- StartTrackingContext
apilocation:
- filetracker.dll
apitype: COM
helpviewer_keywords:
- StartTrackingContext
ms.assetid: 720cd295-38e7-4974-86db-b8106b1207ba
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 15121f050fd5af9a5cb36ce15ffc2161076df06d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99929119"
---
# <a name="starttrackingcontext"></a>StartTrackingContext

Démarre un contexte de suivi.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT WINAPI StartTrackingContext(LPCTSTR intermediateDirectory, LPCTSTR taskName);
```

#### <a name="parameters"></a>Paramètres

[in] `intermediateDirectory`

 Répertoire où stocker le journal de suivi.

[in] `taskName`

 Identifie le contexte de suivi. Ce nom est utilisé pour créer le nom du fichier journal.

## <a name="return-value"></a>Valeur retournée

 **HRESULT** avec le bit **Succeeded** défini si le contexte de suivi a été créé.

## <a name="requirements"></a>Configuration requise

 **En-tête :** *FileTracker.h*
