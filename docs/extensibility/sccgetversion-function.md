---
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
ms.openlocfilehash: 91daeca1df76f6b624d0eddf9d28222369b2cc4a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99844539"
---
# <a name="sccgetversion-function"></a>Fonction SccGetVersion
Cette fonction obtient le numéro de version de l’API de plug-in de contrôle de code source pris en charge par le plug-in de contrôle de code source.

## <a name="syntax"></a>Syntaxe

```cpp
LONG SccGetVersion(void);
```

#### <a name="parameters"></a>Paramètres
 Aucun.

## <a name="return-value"></a>Valeur de retour
 `LONG`Type de données qui contient le numéro de version de l’API de plug-in de contrôle de code source pris en charge :

|WORD|Description|
|----------|-----------------|
|HIWORD|Version principale|
|LOWORD|Version secondaire|

## <a name="remarks"></a>Remarques
 Par exemple, si un plug-in de contrôle de code source prend en charge la version 1,3 de l’API de plug-in de contrôle de code source, cette fonction retourne 0x0103.

## <a name="see-also"></a>Voir aussi
- [Fonctions d’API du plug-in de contrôle de code source](../extensibility/source-control-plug-in-api-functions.md)
