---
title: Afficher les registres, commande | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- debug.listregisters
helpviewer_keywords:
- list registers command
- Debug.ListRegisters command
- ListRegisters command
ms.assetid: 19a9d789-f6c9-46b3-b1f6-4934fc33e055
caps.latest.revision: 14
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 3476244d3044eb80dbfce3559479421b012cc5fa
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72659496"
---
# <a name="list-registers-command"></a>Afficher les registres, commande
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Affiche la valeur des registres sélectionnés et vous permet de modifier la liste de registres à afficher.

## <a name="syntax"></a>Syntaxe

```
Debug.ListRegisters [/Display [{register|registerGroup}...]] [/List]
[/Watch [{register|registerGroup}...]]
[/Unwatch [{register|registerGroup}...]]
```

## <a name="switches"></a>Commutateurs
 /Display [{ `register`&#124;`registerGroup` }...] Affiche les valeurs du ou spécifié `register` `registerGroup` . Si aucun `register` ni `registerGroup` n’est spécifié, la liste par défaut de registres est affichée. Si aucun commutateur n’est spécifié, le comportement est le même. Par exemple :

 `Debug.ListRegisters /Display eax`

 équivaut à :

 `Debug.ListRegisters eax`

 /List affiche tous les groupes de registres dans la liste.

 /Watch [{ `register`&#124;`registerGroup` }...] Ajoute une ou plusieurs `register` `registerGroup` valeurs ou à la liste.

 /Unwatch [{ `register`&#124;`registerGroup` }...] Supprime une ou plusieurs `register` `registerGroup` valeurs ou de la liste.

## <a name="remarks"></a>Notes
 L’alias `r` peut être utilisé à la place de `Debug.ListRegisters`.

## <a name="example"></a>Exemple
 Cet exemple utilise l’alias `Debug.ListRegisters``r` pour afficher les valeurs du groupe de registres `Flags`.

```
r /Display Flags
```

## <a name="see-also"></a>Voir aussi
 Concepts de base du débogage des [commandes Visual Studio](../../ide/reference/visual-studio-commands.md) [: fenêtre registres](../../debugger/debugging-basics-registers-window.md) [Comment : utiliser la fenêtre registres](../../debugger/how-to-use-the-registers-window.md)
