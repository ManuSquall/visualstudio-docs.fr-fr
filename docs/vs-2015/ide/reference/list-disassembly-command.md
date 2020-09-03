---
title: Afficher le code machine, commande | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- debug.listdisassembly
helpviewer_keywords:
- Debug.ListDisassembly command
- list disassembly command
ms.assetid: eb363e35-e86a-4121-966f-991210c27e2a
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 8ff5e620d4c53889afe17274364d6f92936025d3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72672738"
---
# <a name="list-disassembly-command"></a>Afficher le code machine, commande
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Commence le processus de débogage et permet de spécifier comment les erreurs sont gérées.

## <a name="syntax"></a>Syntaxe

```
Debug.ListDisassembly [/count:number] [/endaddress:expression]
[/codebytes:yes|no] [/source:yes|no] [/symbolnames:yes|no]
[/linenumbers:yes|no]
```

## <a name="switches"></a>Commutateurs
 Chaque commutateur peut être appelé à l’aide de sa forme complète ou abrégée.

 /Count : `number` [ou]/c : `number` [ou]/length : `number` [ou]/l : `number` facultatif. Nombre d’instructions à afficher. La valeur par défaut est 8.

 /EndAddress : `expression` [ou]/e : `expression` facultatif. Adresse à laquelle le code machine doit s’arrêter.

 /codebytes : `yes`&#124;`no` [ou]/bytes : `yes`&#124;`no` [ou]/b : `yes`&#124;`no` facultatif. Spécifie si les octets de code doivent être affichés. La valeur par défaut est `no`.

 /Source : `yes`&#124;`no` [ou]/s : `yes`&#124;`no` facultatif. Spécifie si le code source doit être affiché. La valeur par défaut est `no`.

 /symbolnames : `yes`&#124;`no` [ou]/names : `yes`&#124;`no` [ou]/n : `yes`&#124;`no` facultatif. Spécifie si les noms de symbole doivent être affichés. La valeur par défaut est `yes`.

 [/linenumbers : `yes`&#124;`no` ] facultatif. Active l’affichage des numéros de ligne associés au code source. Le commutateur /source doit avoir la valeur `yes` pour utiliser le commutateur /linenumbers.

## <a name="example"></a> Exemple

```
>Debug.ListDisassembly
```

## <a name="see-also"></a>Voir aussi
 [Liste](../../ide/reference/list-call-stack-command.md) de commandes de la pile des appels liste des [Threads commande](../../ide/reference/list-threads-command.md) [Visual Studio commandes Visual Studio](../../ide/reference/visual-studio-commands.md) [fenêtre commande](../../ide/reference/command-window.md) [Rechercher/zone de commande](../../ide/find-command-box.md) [alias de commandes Visual Studio](../../ide/reference/visual-studio-command-aliases.md)
