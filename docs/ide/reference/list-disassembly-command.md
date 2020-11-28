---
title: Afficher le code machine, commande
description: En savoir plus sur la commande list code machine et sur la façon dont elle commence le processus de débogage et vous permet de spécifier la manière dont les erreurs sont gérées.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- debug.listdisassembly
helpviewer_keywords:
- Debug.ListDisassembly command
- list disassembly command
ms.assetid: eb363e35-e86a-4121-966f-991210c27e2a
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 15e9016551b178b0a29656e615d029ddaf0ca279
ms.sourcegitcommit: 2244665d5a0e22d12dd976417f2a782e68684705
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2020
ms.locfileid: "96305332"
---
# <a name="list-disassembly-command"></a>Afficher le code machine, commande
Commence le processus de débogage et permet de spécifier comment les erreurs sont gérées.

## <a name="syntax"></a>Syntax

```cmd
Debug.ListDisassembly [/count:number] [/endaddress:expression]
[/codebytes:yes|no] [/source:yes|no] [/symbolnames:yes|no]
[/linenumbers:yes|no]
```

## <a name="switches"></a>Commutateurs
Chaque commutateur peut être appelé à l’aide de sa forme complète ou abrégée.

/count: `number` [ou] /c: `number` [ou] /length: `number` [ou] /l: `number`

facultatif. Nombre d’instructions à afficher. La valeur par défaut est 8.

/endaddress: `expression` [ou] /e: `expression`

facultatif. Adresse à laquelle le code machine doit s’arrêter.

/codebytes:`yes`&#124;`no` [ou] /bytes:`yes`&#124;`no` [ou] /b:`yes`&#124;`no`

facultatif. Spécifie si les octets de code doivent être affichés. La valeur par défaut est `no`.

/source:`yes`&#124;`no` [ou] /s:`yes`&#124;`no`

facultatif. Spécifie si le code source doit être affiché. La valeur par défaut est `no`.

/symbolnames:`yes`&#124;`no` [ou] /names:`yes`&#124;`no` [ou] /n:`yes`&#124;`no`

facultatif. Spécifie si les noms de symbole doivent être affichés. La valeur par défaut est `yes`.

 [/linenumbers:`yes`&#124;`no`]

facultatif. Active l’affichage des numéros de ligne associés au code source. Le commutateur /source doit avoir la valeur `yes` pour utiliser le commutateur /linenumbers.

## <a name="example"></a>Exemple

```cmd
>Debug.ListDisassembly
```

## <a name="see-also"></a>Voir aussi

- [Afficher la pile des appels, commande](../../ide/reference/list-call-stack-command.md)
- [Liste des threads, commande](../../ide/reference/list-threads-command.md)
- [Commandes Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Fenêtre commande](../../ide/reference/command-window.md)
- [Zone Rechercher/commande](../../ide/find-command-box.md)
- [Alias de commandes Visual Studio](../../ide/reference/visual-studio-command-aliases.md)