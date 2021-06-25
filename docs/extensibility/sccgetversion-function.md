---
description: Cette fonction obtient le numéro de version de l’API de plug-in de contrôle de code source pris en charge par le plug-in de contrôle de code source.
title: SccGetVersion fonction) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- SccGetVersion
helpviewer_keywords:
- SccGetVersion function
ms.assetid: a6e786bf-744e-4272-9e21-0be44d23b1a1
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: f49d33ebe70390a364d0ae8336e7f69549b6876f
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112901082"
---
# <a name="sccgetversion-function"></a>Fonction SccGetVersion
Cette fonction obtient le numéro de version de l’API de plug-in de contrôle de code source pris en charge par le plug-in de contrôle de code source.

## <a name="syntax"></a>Syntaxe

```cpp
LONG SccGetVersion(void);
```

#### <a name="parameters"></a>Paramètres
 Aucun.

## <a name="return-value"></a>Valeur renvoyée
 `LONG`Type de données qui contient le numéro de version de l’API de plug-in de contrôle de code source pris en charge :

|WORD|Description|
|----------|-----------------|
|HIWORD|Version majeure|
|LOWORD|Version mineure|

## <a name="remarks"></a>Remarques
 Par exemple, si un plug-in de contrôle de code source prend en charge la version 1,3 de l’API de plug-in de contrôle de code source, cette fonction retourne 0x0103.

## <a name="see-also"></a>Voir aussi
- [Fonctions d’API du plug-in de contrôle de code source](../extensibility/source-control-plug-in-api-functions.md)
