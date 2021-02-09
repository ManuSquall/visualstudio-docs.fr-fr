---
title: Afficher les modules, commande
description: En savoir plus sur la commande list modules et sur la manière dont elle répertorie les modules pour le processus en cours.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- debug.listmodules
helpviewer_keywords:
- Debug.ListModules command
- ListModules command
- list modules command
ms.assetid: 3cb73774-6ac0-43b2-b781-75ed47175bfd
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 4a38a5423568528d267fd92894b8b06b4e5667c5
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99852061"
---
# <a name="list-modules-command"></a>Afficher les modules, commande
Répertorie les modules pour le processus en cours.

## <a name="syntax"></a>Syntaxe

```
Debug.ListModules [/Address:yes|no] [/Name:yes|no] [/Order:yes|no]
[/Path:yes|no] [/Process:yes|no] [/SymbolFile:yes|no]
[/SymbolStatus:yes|no] [/Timestamp:yes|no] [/Version:yes|no]
```

#### <a name="parameters"></a>Paramètres
/Address:`yes|no`

Facultatif. Spécifie s’il faut afficher les adresses mémoire des modules. La valeur par défaut est `yes`.

/Name:`yes|no`

Facultatif. Spécifie s’il faut afficher les noms des modules. La valeur par défaut est `yes`.

/Order:`yes|no`

Facultatif. Spécifie s’il faut afficher l’ordre des modules. La valeur par défaut est `no`.

/Path:`yes|no`

Facultatif. Spécifie s’il faut afficher les chemins des modules. La valeur par défaut est `yes`.

/Process:`yes|no`

Facultatif. Spécifie s’il faut afficher les processus des modules. La valeur par défaut est `no`.

/SymbolFile:`yes|no`

Facultatif. Spécifie s’il faut afficher les fichiers de symboles des modules. La valeur par défaut est `no`.

/SymbolStatus:`yes|no`

Facultatif. Spécifie s’il faut afficher les états des symboles des modules. La valeur par défaut est `yes`.

/Timestamp:`yes|no`

Facultatif. Spécifie s’il faut afficher les horodatages des modules. La valeur par défaut est `no`.

/Version:`yes|no`

Facultatif. Spécifie s’il faut afficher les versions des modules. La valeur par défaut est `no`.

## <a name="example"></a>Exemple
Cet exemple répertorie les noms, les adresses et les horodatages des modules pour le processus actuel.

```
Debug.ListModules /Address:yes /Name:yes /Order:no /Path:no /Process:no /SymbolFile:no /SymbolStatus:no /Timestamp:yes /Version:no
```

## <a name="see-also"></a>Voir aussi

- [Commandes Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Fenêtre commande](../../ide/reference/command-window.md)
- [Comment : utiliser la fenêtre Modules](../../debugger/how-to-use-the-modules-window.md)
