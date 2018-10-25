---
title: Afficher la mémoire, commande
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- debug.listmemory
helpviewer_keywords:
- Debug.ListMemory command
- ListMemory command
- list memory command
ms.assetid: a84de361-a6a6-4f6d-96aa-a0d4a424371e
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 57d6c8c7821df8bd22723900ebd011c110a1857f
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49815180"
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

 Facultative. Adresse mémoire à partir de laquelle la mémoire doit être affichée.

## <a name="switches"></a>Commutateurs
 /ANSI&#124;Unicode

 Facultative. Affiche la mémoire sous la forme de caractères ANSI ou Unicode correspondant aux octets de mémoire.

 /Count:`number`

 Facultative. Détermine le nombre d’octets de mémoire à afficher, à partir de l’argument `expression`.

 /Format:`formattype`

 Facultative. Type du format selon lequel les informations sur la mémoire sont affichées dans la fenêtre **Mémoire** ; le format peut être OneByte, TwoBytes, FourBytes, EightBytes, Float (32 bits) ou Double (64 bits). Si le format OneByte est utilisé, `/Unicode` n’est pas disponible.

 /Hex&#124;Signed&#124;Unsigned

 Facultative. Spécifie le format d’affichage des nombres : signé, non signé ou hexadécimal.

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
|**d**|Debug.ListMemory|
|**da**|Debug.ListMemory /Ansi|
|**db**|Debug.ListMemory /Format:OneByte|
|**dc**|Debug.ListMemory /Format:FourBytes /Ansi|
|**dd**|Debug.ListMemory /Format:FourBytes|
|**df**|Debug.ListMemory /Format:Float|
|**dq**|Debug.ListMemory /Format:EightBytes|
|**du**|Debug.ListMemory /Unicode|

## <a name="example"></a>Exemple

```cmd
>Debug.ListMemory /Format:float /Count:30 /Unicode
```

## <a name="see-also"></a>Voir aussi

- [Afficher la pile des appels, commande](../../ide/reference/list-call-stack-command.md)
- [Répertorier les threads, commande](../../ide/reference/list-threads-command.md)
- [Commandes Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Commande, fenêtre](../../ide/reference/command-window.md)
- [Rechercher/Commande, zone](../../ide/find-command-box.md)
- [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)