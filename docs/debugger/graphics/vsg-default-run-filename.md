---
description: Définit le nom de fichier par défaut du fichier journal graphique.
title: VSG_DEFAULT_RUN_FILENAME | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: ea549d2f-c857-458c-93c7-bc5a2d11d15d
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 5f6bd07e54fc90bcc99f7462cc087ba01866727c
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102160478"
---
# <a name="vsg_default_run_filename"></a>VSG_DEFAULT_RUN_FILENAME
Définit le nom de fichier par défaut du fichier journal graphique.

## <a name="syntax"></a>Syntaxe

```C++
#define VSG_DEFAULT_FILENAME filename
```

#### <a name="parameters"></a>Paramètres
 `filename` Nom de fichier donné par défaut au fichier journal de graphisme lorsque les informations graphiques sont capturées par programme.

## <a name="value"></a>Valeur
 Littéral de chaîne qui représente le nom de fichier du fichier journal de graphisme. Par défaut, L "default. vsglog".

```C++
#define VSG_DEFAULT_FILENAME L"default.vsglog"
```

## <a name="remarks"></a>Notes
 Si le symbole de préprocesseur `DONT_SAVE_VSGLOG_TO_TEMP` est défini, le nom de fichier est relatif au répertoire actif de l’application capturée ou est un chemin d’accès absolu ; dans le cas contraire, il est relatif au répertoire de fichiers temporaires de l’utilisateur et ne peut pas être un chemin d’accès absolu.

 Pour modifier le nom de fichier défini, vous devez le redéfinir avant `vsgcapture.h` d’inclure dans votre programme.

## <a name="example"></a>Exemple
 Cet exemple montre comment modifier le nom de fichier par défaut du fichier de capture :

```C++
// Redefine the default capture filename before including vsgcapture.h
#define VSG_DEFAULT_FILENAME L"capture.vsglog"

#include <vsgcapture.h>
```

## <a name="see-also"></a>Voir aussi
- [DONT_SAVE_VSGLOG_TO_TEMP](dont-save-vsglog-to-temp.md)
