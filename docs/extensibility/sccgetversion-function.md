---
description: Cette fonction obtient le numéro de version de l’API de plug-in de contrôle de code source pris en charge par le plug-in de contrôle de code source.
title: SccGetVersion fonction) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccGetVersion
helpviewer_keywords:
- SccGetVersion function
ms.assetid: a6e786bf-744e-4272-9e21-0be44d23b1a1
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: a71d3374ffd65e0e7b9a7b2e654885d84e370a9d
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102220597"
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
|HIWORD|Version principale|
|LOWORD|Version secondaire|

## <a name="remarks"></a>Notes
 Par exemple, si un plug-in de contrôle de code source prend en charge la version 1,3 de l’API de plug-in de contrôle de code source, cette fonction retourne 0x0103.

## <a name="see-also"></a>Voir aussi
- [Fonctions d’API du plug-in de contrôle de code source](../extensibility/source-control-plug-in-api-functions.md)
