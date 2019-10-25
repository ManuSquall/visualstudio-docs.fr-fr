---
title: VSG_DEFAULT_RUN_FILENAME | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: ea549d2f-c857-458c-93c7-bc5a2d11d15d
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 835e2cec19e36418091e094abd2ec76bd6403398
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72734826"
---
# <a name="vsg_default_run_filename"></a>VSG_DEFAULT_RUN_FILENAME
Définit le nom de fichier par défaut du fichier journal graphique.

## <a name="syntax"></a>Syntaxe

```C++
#define VSG_DEFAULT_FILENAME filename
```

#### <a name="parameters"></a>Paramètres
 `filename` le nom de fichier donné par défaut au fichier journal de graphisme lorsque les informations graphiques sont capturées par programme.

## <a name="value"></a>valeur
 Littéral de chaîne qui représente le nom de fichier du fichier journal de graphisme. Par défaut, L "default. vsglog".

```C++
#define VSG_DEFAULT_FILENAME L"default.vsglog"
```

## <a name="remarks"></a>Notes
 Si le symbole de préprocesseur `DONT_SAVE_VSGLOG_TO_TEMP` est défini, le nom de fichier est relatif au répertoire actif de l’application capturée ou est un chemin d’accès absolu ; dans le cas contraire, il est relatif au répertoire des fichiers temporaires de l’utilisateur et ne peut pas être un chemin d’accès absolu.

 Pour modifier le nom de fichier défini, vous devez le redéfinir avant d’inclure `vsgcapture.h` dans votre programme.

## <a name="example"></a>Exemple
 Cet exemple montre comment modifier le nom de fichier par défaut du fichier de capture :

```C++
// Redefine the default capture filename before including vsgcapture.h
#define VSG_DEFAULT_FILENAME L"capture.vsglog"

#include <vsgcapture.h>
```

## <a name="see-also"></a>Voir aussi
- [DONT_SAVE_VSGLOG_TO_TEMP](dont-save-vsglog-to-temp.md)