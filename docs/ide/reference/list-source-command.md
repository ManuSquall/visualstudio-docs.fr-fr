---
title: Afficher la source, commande
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- Debug.ListSource
helpviewer_keywords:
- Debug.ListSource command
- list source command
- ListSource command
ms.assetid: e45f08d2-f4a3-49c3-9452-aa60508e2f74
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8dcecdaa206964e6c8a5aebcadc958fe2c1ee1e5
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2019
ms.locfileid: "55953189"
---
# <a name="list-source-command"></a>Afficher la source, commande
Affiche les lignes de code source spécifiées.

## <a name="syntax"></a>Syntaxe

```
Debug.ListSource [/Count:number] [/Current] [/File:filename]
[/Line:number] [/ShowLineNumbers:yes|no]
```

## <a name="switches"></a>Commutateurs
 /Count:`number`

 Optionnel. Spécifie le nombre de lignes à afficher.

 /Current

 Optionnel. Affiche la ligne active.

 /File:`filename`

 Optionnel. Chemin du fichier à afficher. Si aucun nom de fichier n’est spécifié, la commande affiche le code source de la ligne de l’instruction actuelle.

 /Line:`number`

 Optionnel. Affiche un numéro de ligne spécifique.

 /ShowLineNumbers:`yes|no`

 Optionnel. Spécifie s’il faut afficher les numéros de ligne.

## <a name="example"></a>Exemple
 Cet exemple affiche le code source à partir de la ligne 4 du fichier Form1.vb, avec les numéros de ligne.

```
Debug.ListSource /File:"C:\Visual Studio Projects\Form1.vb" /Line:4 /ShowLineNumbers:yes
```

## <a name="see-also"></a>Voir aussi

- [Commandes Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Commande, fenêtre](../../ide/reference/command-window.md)