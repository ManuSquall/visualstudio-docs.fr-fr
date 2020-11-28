---
title: Afficher la source, commande
description: En savoir plus sur la commande list source et sur l’affichage des lignes de code source spécifiées.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- Debug.ListSource
helpviewer_keywords:
- Debug.ListSource command
- list source command
- ListSource command
ms.assetid: e45f08d2-f4a3-49c3-9452-aa60508e2f74
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ae2463a3d8dd295fcba9bf264e1ad3fa250169d4
ms.sourcegitcommit: 2244665d5a0e22d12dd976417f2a782e68684705
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2020
ms.locfileid: "96305283"
---
# <a name="list-source-command"></a>Afficher la source, commande
Affiche les lignes de code source spécifiées.

## <a name="syntax"></a>Syntax

```
Debug.ListSource [/Count:number] [/Current] [/File:filename]
[/Line:number] [/ShowLineNumbers:yes|no]
```

## <a name="switches"></a>Commutateurs
/Count:`number`

facultatif. Spécifie le nombre de lignes à afficher.

/Current

facultatif. Affiche la ligne active.

/File:`filename`

facultatif. Chemin du fichier à afficher. Si aucun nom de fichier n’est spécifié, la commande affiche le code source de la ligne de l’instruction actuelle.

/Line:`number`

facultatif. Affiche un numéro de ligne spécifique.

/ShowLineNumbers:`yes|no`

facultatif. Spécifie s’il faut afficher les numéros de ligne.

## <a name="example"></a> Exemple
Cet exemple affiche le code source à partir de la ligne 4 du fichier Form1.vb, avec les numéros de ligne.

```
Debug.ListSource /File:"C:\Visual Studio Projects\Form1.vb" /Line:4 /ShowLineNumbers:yes
```

## <a name="see-also"></a>Voir aussi

- [Commandes Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Fenêtre commande](../../ide/reference/command-window.md)