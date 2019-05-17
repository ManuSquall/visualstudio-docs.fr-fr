---
title: Afficher le code machine, commande
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- debug.listdisassembly
helpviewer_keywords:
- Debug.ListDisassembly command
- list disassembly command
ms.assetid: eb363e35-e86a-4121-966f-991210c27e2a
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 71a1be7841cb25cebafe951419006bb8b635093c
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62970159"
---
# <a name="list-disassembly-command"></a>Afficher le code machine, commande
Commence le processus de débogage et permet de spécifier comment les erreurs sont gérées.

## <a name="syntax"></a>Syntaxe

```cmd
Debug.ListDisassembly [/count:number] [/endaddress:expression]
[/codebytes:yes|no] [/source:yes|no] [/symbolnames:yes|no]
[/linenumbers:yes|no]
```

## <a name="switches"></a>Commutateurs
 Chaque commutateur peut être appelé à l’aide de sa forme complète ou abrégée.

 /count: `number` [ou] /c: `number` [ou] /length: `number` [ou] /l: `number`

 Optionnel. Nombre d’instructions à afficher. La valeur par défaut est 8.

 /endaddress: `expression` [ou] /e: `expression`

 Optionnel. Adresse à laquelle le code machine doit s’arrêter.

 /codebytes:`yes`&#124;`no` [ou] /bytes:`yes`&#124;`no` [ou] /b:`yes`&#124;`no`

 Optionnel. Spécifie si les octets de code doivent être affichés. La valeur par défaut est `no`.

 /source:`yes`&#124;`no` [ou] /s:`yes`&#124;`no`

 Optionnel. Spécifie si le code source doit être affiché. La valeur par défaut est `no`.

 /symbolnames:`yes`&#124;`no` [ou] /names:`yes`&#124;`no` [ou] /n:`yes`&#124;`no`

 Optionnel. Spécifie si les noms de symbole doivent être affichés. La valeur par défaut est `yes`.

 [/linenumbers:`yes`&#124;`no`]

 Optionnel. Active l’affichage des numéros de ligne associés au code source. Le commutateur /source doit avoir la valeur `yes` pour utiliser le commutateur /linenumbers.

## <a name="example"></a>Exemple

```cmd
>Debug.ListDisassembly
```

## <a name="see-also"></a>Voir aussi

- [Afficher la pile des appels, commande](../../ide/reference/list-call-stack-command.md)
- [Répertorier les threads, commande](../../ide/reference/list-threads-command.md)
- [Commandes Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Commande, fenêtre](../../ide/reference/command-window.md)
- [Rechercher/Commande, zone](../../ide/find-command-box.md)
- [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)