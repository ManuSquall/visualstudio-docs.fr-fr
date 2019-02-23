---
title: Fonction SccGetVersion | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccGetVersion
helpviewer_keywords:
- SccGetVersion function
ms.assetid: a6e786bf-744e-4272-9e21-0be44d23b1a1
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7e2b3818aaa5097313d9150b365544267768507f
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/22/2019
ms.locfileid: "56708938"
---
# <a name="sccgetversion-function"></a>Fonction SccGetVersion
Cette fonction obtient le numéro de version de l’API de plug-in de contrôle de Source pris en charge par le plug-in de contrôle de code source.

## <a name="syntax"></a>Syntaxe

```cpp
LONG SccGetVersion(void);
```

#### <a name="parameters"></a>Paramètres
 Aucun.

## <a name="return-value"></a>Valeur de retour
 Un `LONG` type de données qui contient le numéro de version de l’API de plug-in de contrôle de Source pris en charge :

|WORD|Description|
|----------|-----------------|
|HIWORD|Version principale|
|LOWORD|Version mineure|

## <a name="remarks"></a>Notes
 Par exemple, si un plug-in de contrôle de code source prend en charge la version 1.3 de l’API de plug-in de contrôle de Source, cette fonction retournait 0x0103.

## <a name="see-also"></a>Voir aussi
- [Fonctions d’API du plug-in de contrôle de code source](../extensibility/source-control-plug-in-api-functions.md)