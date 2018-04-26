---
title: Afficher la source, commande
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 03a5d0699fced4d01d439942081b359454bcf476
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2018
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

 Facultative. Spécifie le nombre de lignes à afficher.

 /Current

 Facultative. Affiche la ligne active.

 /File:`filename`

 Facultative. Chemin du fichier à afficher. Si aucun nom de fichier n’est spécifié, la commande affiche le code source de la ligne de l’instruction actuelle.

 /Line:`number`

 Facultative. Affiche un numéro de ligne spécifique.

 /ShowLineNumbers:`yes|no`

 Facultative. Spécifie s’il faut afficher les numéros de ligne.

## <a name="example"></a>Exemple
 Cet exemple affiche le code source à partir de la ligne 4 du fichier Form1.vb, avec les numéros de ligne.

```
Debug.ListSource /File:"C:\Visual Studio Projects\Form1.vb" /Line:4 /ShowLineNumbers:yes
```

## <a name="see-also"></a>Voir aussi

- [Commandes Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Commande, fenêtre](../../ide/reference/command-window.md)