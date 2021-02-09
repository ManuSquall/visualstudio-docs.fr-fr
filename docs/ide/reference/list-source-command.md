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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 4efd5ab0ddd94b17fa6a683366707d635f844bb6
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99919429"
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

Facultatif. Spécifie le nombre de lignes à afficher.

/Current

Facultatif. Affiche la ligne active.

/File:`filename`

Facultatif. Chemin du fichier à afficher. Si aucun nom de fichier n’est spécifié, la commande affiche le code source de la ligne de l’instruction actuelle.

/Line:`number`

Facultatif. Affiche un numéro de ligne spécifique.

/ShowLineNumbers:`yes|no`

Facultatif. Spécifie s’il faut afficher les numéros de ligne.

## <a name="example"></a>Exemple
Cet exemple affiche le code source à partir de la ligne 4 du fichier Form1.vb, avec les numéros de ligne.

```
Debug.ListSource /File:"C:\Visual Studio Projects\Form1.vb" /Line:4 /ShowLineNumbers:yes
```

## <a name="see-also"></a>Voir aussi

- [Commandes Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Fenêtre commande](../../ide/reference/command-window.md)