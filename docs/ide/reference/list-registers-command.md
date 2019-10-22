---
title: Afficher les registres, commande
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- debug.listregisters
helpviewer_keywords:
- list registers command
- Debug.ListRegisters command
- ListRegisters command
ms.assetid: 19a9d789-f6c9-46b3-b1f6-4934fc33e055
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b8a5ad6c57ed25d251ff7ce0e51093f5b542ed54
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72610502"
---
# <a name="list-registers-command"></a>Afficher les registres, commande
Affiche la valeur des registres sélectionnés et vous permet de modifier la liste de registres à afficher.

## <a name="syntax"></a>Syntaxe

```cmd
Debug.ListRegisters [/Display [{register|registerGroup}...]] [/List]
[/Watch [{register|registerGroup}...]]
[/Unwatch [{register|registerGroup}...]]
```

## <a name="switches"></a>Commutateurs
/Display [{`register`&#124;`registerGroup`}...]

Affiche les valeurs du `register` ou `registerGroup` spécifié. Si aucun `register` ni `registerGroup` n’est spécifié, la liste par défaut de registres est affichée. Si aucun commutateur n’est spécifié, le comportement est le même. Exemple :

`Debug.ListRegisters /Display eax`

est équivalent à

`Debug.ListRegisters eax`

/List

Affiche tous les groupes de registres dans la liste.

/Watch [{`register`&#124;`registerGroup`}...]

Ajoute une ou plusieurs valeurs de `register` ou `registerGroup` dans la liste.

/Unwatch [{`register`&#124;`registerGroup`}...]

Supprime une ou plusieurs valeurs de `register` ou `registerGroup` de la liste.

## <a name="remarks"></a>Notes
L’alias `r` peut être utilisé à la place de `Debug.ListRegisters`.

## <a name="example"></a>Exemple
Cet exemple utilise l’alias `Debug.ListRegisters` `r` pour afficher les valeurs du groupe de registres `Flags`.

```cmd
r /Display Flags
```

## <a name="see-also"></a>Voir aussi

- [Commandes Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Concepts de base du débogage : fenêtre Registres](../../debugger/debugging-basics-registers-window.md)
- [Guide pratique pour utiliser la fenêtre Registres](../../debugger/how-to-use-the-registers-window.md)