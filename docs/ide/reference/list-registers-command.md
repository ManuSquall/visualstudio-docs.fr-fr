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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: fb1a2361534f167a0b88b3f1b5b38c005915243d
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2019
ms.locfileid: "55934469"
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

 Affiche les valeurs du `register` ou `registerGroup` spécifié. Si aucun `register` ni `registerGroup` n’est spécifié, la liste par défaut de registres est affichée. Si aucun commutateur n’est spécifié, le comportement est le même. Par exemple :

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
- [Principes de base pour le débogage : la fenêtre Registres](../../debugger/debugging-basics-registers-window.md)
- [Guide pratique pour utiliser la fenêtre Registres](../../debugger/how-to-use-the-registers-window.md)