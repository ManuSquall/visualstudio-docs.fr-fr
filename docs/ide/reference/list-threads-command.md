---
title: Afficher les threads, commande
description: En savoir plus sur la commande list threads et sur la façon dont elle affiche une liste des threads dans le programme en cours.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- debug.listthreads
helpviewer_keywords:
- ListThreads command
- list threads command
- Debug.ListThreads command
ms.assetid: 34b665c0-d46f-4c1a-a066-b678eba5ac54
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: f3abcd7182c8bb5b94b2f35a9463f845cc6bb5bd
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99919387"
---
# <a name="list-threads-command"></a>Afficher les threads, commande
Affiche une liste des threads du programme en cours.

## <a name="syntax"></a>Syntaxe

```
Debug.ListThreads [index]
```

## <a name="arguments"></a>Arguments
`index`

Facultatif. Sélectionne un thread par son index pour en faire le thread actuel.

## <a name="remarks"></a>Remarques
Une fois spécifié, l’argument `index` marque le thread indiqué comme étant le thread actuel. Un astérisque (*) est affiché dans la liste en regard du thread actuel.

## <a name="example"></a>Exemple

```
>Debug.ListThreads
```

## <a name="see-also"></a>Voir aussi

- [Afficher la pile des appels, commande](../../ide/reference/list-call-stack-command.md)
- [List code machine, commande](../../ide/reference/list-disassembly-command.md)
- [Commandes Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Fenêtre commande](../../ide/reference/command-window.md)
- [Zone Rechercher/commande](../../ide/find-command-box.md)
- [Alias de commandes Visual Studio](../../ide/reference/visual-studio-command-aliases.md)
