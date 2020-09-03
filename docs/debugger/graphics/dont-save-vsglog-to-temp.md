---
title: DONT_SAVE_VSGLOG_TO_TEMP | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: f27ab0e6-9575-4ca0-9901-37d3e5c3a2f5
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 40f3c3c22de6b4b0ebdbdf2dfc953f4cb1c9b5e6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72736077"
---
# <a name="dont_save_vsglog_to_temp"></a>DONT_SAVE_VSGLOG_TO_TEMP
Définit par sa présence si le fichier journal graphique est enregistré dans le répertoire des fichiers temporaires de l'utilisateur.

## <a name="syntax"></a>Syntaxe

```C++
#define DONT_SAVE_VSGLOG_TO_TEMP
```

## <a name="value"></a>Valeur
 Symbole de préprocesseur dont la présence ou l’absence détermine si le fichier journal de graphisme est enregistré dans le répertoire des fichiers temporaires de l’utilisateur. Si ce symbole est défini, le nom de fichier défini par `VSG_DEFAULT_RUN_FILENAME` est relatif au répertoire actif de l’application capturée, ou est un chemin d’accès absolu ; sinon, le nom de fichier défini par `VSG_DEFAULT_RUN_FILENAME` est relatif au répertoire de fichiers temporaires de l’utilisateur et ne peut pas être un chemin d’accès absolu.

## <a name="remarks"></a>Notes
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
