---
title: DONT_SAVE_VSGLOG_TO_TEMP | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: f27ab0e6-9575-4ca0-9901-37d3e5c3a2f5
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: f94b287f6ed9d4cda0696252ba32d493879ed5c1
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99880266"
---
# <a name="dont_save_vsglog_to_temp"></a>DONT_SAVE_VSGLOG_TO_TEMP
Définit par sa présence si le fichier journal graphique est enregistré dans le répertoire des fichiers temporaires de l'utilisateur.

## <a name="syntax"></a>Syntaxe

```C++
#define DONT_SAVE_VSGLOG_TO_TEMP
```

## <a name="value"></a>Valeur
 Symbole de préprocesseur dont la présence ou l’absence détermine si le fichier journal de graphisme est enregistré dans le répertoire des fichiers temporaires de l’utilisateur. Si ce symbole est défini, le nom de fichier défini par `VSG_DEFAULT_RUN_FILENAME` est relatif au répertoire actif de l’application capturée, ou est un chemin d’accès absolu ; sinon, le nom de fichier défini par `VSG_DEFAULT_RUN_FILENAME` est relatif au répertoire de fichiers temporaires de l’utilisateur et ne peut pas être un chemin d’accès absolu.

## <a name="remarks"></a>Remarques
 En fonction des privilèges de l’utilisateur, il se peut que le fichier journal de graphisme ne puisse pas être enregistré dans un emplacement arbitraire. Nous vous recommandons d’enregistrer les journaux de graphisme dans le répertoire des fichiers temporaires de l’utilisateur, ou un autre emplacement connu, si vous ne savez pas si l’utilisateur peut écrire l’emplacement que vous choisissez.

 Pour empêcher l’enregistrement du fichier journal de graphisme dans le répertoire de fichiers temporaires, vous devez définir `DONT_SAVE_VSGLOG_TO_TEMP` avant d’inclure `vsgcapture.h` .

## <a name="example"></a>Exemple
 Cet exemple montre comment enregistrer le fichier journal de graphisme dans un chemin d’accès absolu sur l’ordinateur hôte.

```cpp
// Define DONT_SAVE_VSGLOG_TO_TEMP and VSG_DEFAULT_RUN_FILENAME before including vsgcapture.h
#define DONT_SAVE_VSGLOG_TO_TEMP
#define VSG_DEFAULT_RUN_FILENAME L"C:\\Graphics Diagnostics Captures\\default.vsglog"

#include <vsgcapture.h>
```

## <a name="see-also"></a>Voir aussi
- [VSG_DEFAULT_RUN_FILENAME](vsg-default-run-filename.md)
