---
title: Afficher la mémoire, commande
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- debug.listmemory
helpviewer_keywords:
- Debug.ListMemory command
- ListMemory command
- list memory command
ms.assetid: a84de361-a6a6-4f6d-96aa-a0d4a424371e
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c500b1b516c2b1ab1bc66b7970fccc4ec7a85baa
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75568709"
---
# <a name="list-memory-command"></a>Afficher la mémoire, commande
Affiche le contenu de la plage de mémoire spécifiée.

## <a name="syntax"></a>Syntaxe

```cmd
Debug.ListMemory [/ANSI|Unicode] [/Count:number] [/Format:formattype]
[/Hex|Signed|Unsigned] [expression]
```

## <a name="arguments"></a>Arguments
`expression`

facultatif. Adresse mémoire à partir de laquelle la mémoire doit être affichée.

## <a name="switches"></a>Commutateurs
/ANSI&#124;Unicode

facultatif. Affiche la mémoire sous la forme de caractères ANSI ou Unicode correspondant aux octets de mémoire.

/Count:`number`

facultatif. Détermine le nombre d’octets de mémoire à afficher, à partir de l’argument `expression`.

/Format:`formattype`

facultatif. Type du format selon lequel les informations sur la mémoire sont affichées dans la fenêtre **Mémoire** ; le format peut être OneByte, TwoBytes, FourBytes, EightBytes, Float (32 bits) ou Double (64 bits). Si le format OneByte est utilisé, `/Unicode` n’est pas disponible.

/Hex&#124;Signed&#124;Unsigned

facultatif. Spécifie le format d’affichage des nombres : signé, non signé ou hexadécimal.

## <a name="remarks"></a>Notes 
Au lieu d’écrire une commande **Debug.ListMemory** complète avec tous ses commutateurs, vous pouvez appeler la commande à l’aide d’alias préparamétrés avec certains commutateurs prédéfinis à des valeurs spécifiées. Par exemple, au lieu d’entrer :

```cmd
>Debug.ListMemory /Format:float /Count:30 /Unicode
```

vous pouvez écrire :

```cmd
>df /Count:30 /Unicode
```

Voici une liste des alias disponibles pour la commande **Debug.ListMemory** :

|Alias|Commande et commutateurs|
|-----------| - |
|**D**|Debug.ListMemory|
|**da**|Debug.ListMemory /Ansi|
|**Db**|Debug.ListMemory /Format:OneByte|
|**Dc**|Debug.ListMemory /Format:FourBytes /Ansi|
|**jj**|Debug.ListMemory /Format:FourBytes|
|**Df**|Debug.ListMemory /Format:Float|
|**Dq**|Debug.ListMemory /Format:EightBytes|
|**du**|Debug.ListMemory /Unicode|

## <a name="example"></a> Exemple

```cmd
>Debug.ListMemory /Format:float /Count:30 /Unicode
```

## <a name="see-also"></a>Voir aussi

- [Afficher la pile d’appels, commande](../../ide/reference/list-call-stack-command.md)
- [Répertorier les threads, commande](../../ide/reference/list-threads-command.md)
- [Commandes de studio visuel](../../ide/reference/visual-studio-commands.md)
- [Commande, fenêtre](../../ide/reference/command-window.md)
- [Boîte de recherche/commande](../../ide/find-command-box.md)
- [Alias de commande de studio visuel](../../ide/reference/visual-studio-command-aliases.md)
