---
title: Afficher les modules, commande
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1e083a0e1baeefc6807dccb2199cd0e5a9bd883d
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75595499"
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

facultatif. Spécifie s’il faut afficher les adresses mémoire des modules. La valeur par défaut est `yes`.

/Name:`yes|no`

facultatif. Spécifie s’il faut afficher les noms des modules. La valeur par défaut est `yes`.

/Order:`yes|no`

facultatif. Spécifie s’il faut afficher l’ordre des modules. La valeur par défaut est `no`.

/Path:`yes|no`

facultatif. Spécifie s’il faut afficher les chemins des modules. La valeur par défaut est `yes`.

/Process:`yes|no`

facultatif. Spécifie s’il faut afficher les processus des modules. La valeur par défaut est `no`.

/SymbolFile:`yes|no`

facultatif. Spécifie s’il faut afficher les fichiers de symboles des modules. La valeur par défaut est `no`.

/SymbolStatus:`yes|no`

facultatif. Spécifie s’il faut afficher les états des symboles des modules. La valeur par défaut est `yes`.

/Timestamp:`yes|no`

facultatif. Spécifie s’il faut afficher les horodatages des modules. La valeur par défaut est `no`.

/Version:`yes|no`

facultatif. Spécifie s’il faut afficher les versions des modules. La valeur par défaut est `no`.

## <a name="example"></a> Exemple
Cet exemple répertorie les noms, les adresses et les horodatages des modules pour le processus actuel.

```
Debug.ListModules /Address:yes /Name:yes /Order:no /Path:no /Process:no /SymbolFile:no /SymbolStatus:no /Timestamp:yes /Version:no
```

## <a name="see-also"></a>Voir aussi

- [Commandes de studio visuel](../../ide/reference/visual-studio-commands.md)
- [Commande, fenêtre](../../ide/reference/command-window.md)
- [Comment : utiliser la fenêtre Modules](../../debugger/how-to-use-the-modules-window.md)
