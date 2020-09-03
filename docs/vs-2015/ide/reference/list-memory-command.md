---
title: Afficher la mémoire, commande | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- debug.listmemory
helpviewer_keywords:
- Debug.ListMemory command
- ListMemory command
- list memory command
ms.assetid: a84de361-a6a6-4f6d-96aa-a0d4a424371e
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 2630402e03d1256f63e542818a9066745206d2c5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72672750"
---
# <a name="list-memory-command"></a>Afficher la mémoire, commande
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Affiche le contenu de la plage de mémoire spécifiée.

## <a name="syntax"></a>Syntaxe

```
Debug.ListMemory [/ANSI|Unicode] [/Count:number] [/Format:formattype]
[/Hex|Signed|Unsigned] [expression]
```

## <a name="arguments"></a>Arguments
 `expression` Facultatif. Adresse mémoire à partir de laquelle la mémoire doit être affichée.

## <a name="switches"></a>Commutateurs
 /ANSI&#124;Unicode facultatif. Affiche la mémoire sous la forme de caractères ANSI ou Unicode correspondant aux octets de mémoire.

 /Count : `number` facultatif. Détermine le nombre d’octets de mémoire à afficher, à partir de l’argument `expression`.

 /Format : `formattype` facultatif. Type du format selon lequel les informations sur la mémoire sont affichées dans la fenêtre **Mémoire** ; le format peut être OneByte, TwoBytes, FourBytes, EightBytes, Float (32 bits) ou Double (64 bits). Si le format OneByte est utilisé, `/Unicode` n’est pas disponible.

 /Hex&#124;signé&#124;non signé facultatif. Spécifie le format d’affichage des nombres : signé, non signé ou hexadécimal.

## <a name="remarks"></a>Notes
 Au lieu d’écrire une commande **Debug.ListMemory** complète avec tous ses commutateurs, vous pouvez appeler la commande à l’aide d’alias préparamétrés avec certains commutateurs prédéfinis à des valeurs spécifiées. Par exemple, au lieu d’entrer :

```
>Debug.ListMemory /Format:float /Count:30 /Unicode
```

 vous pouvez écrire :

```
>df /Count:30 /Unicode
```

 Voici une liste des alias disponibles pour la commande **Debug.ListMemory** :

|Alias|Commande et commutateurs|
|-----------|--------------------------|
|**d**|Debug.ListMemory|
|**da**|Debug.ListMemory /Ansi|
|**bases**|Debug.ListMemory /Format:OneByte|
|**métafichier**|Debug.ListMemory /Format:FourBytes /Ansi|
|**JJ**|Debug.ListMemory /Format:FourBytes|
|**DL**|Debug.ListMemory /Format:Float|
|**DQ**|Debug.ListMemory /Format:EightBytes|
|**du**|Debug.ListMemory /Unicode|

## <a name="example"></a> Exemple

```
>Debug.ListMemory /Format:float /Count:30 /Unicode
```

## <a name="see-also"></a>Voir aussi
 [Liste](../../ide/reference/list-call-stack-command.md) de commandes de la pile des appels liste des [Threads commande](../../ide/reference/list-threads-command.md) [Visual Studio commandes Visual Studio](../../ide/reference/visual-studio-commands.md) [fenêtre commande](../../ide/reference/command-window.md) [Rechercher/zone de commande](../../ide/find-command-box.md) [alias de commandes Visual Studio](../../ide/reference/visual-studio-command-aliases.md)
