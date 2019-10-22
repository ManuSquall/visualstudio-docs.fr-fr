---
title: Atteindre, commande | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- edit.goto
helpviewer_keywords:
- Debug.Goto command
- Go To command
ms.assetid: 201e1dd2-6701-467d-8cc1-faec2ef20511
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 454b51b6939a78cdaab8d29f51d30910024adbe3
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72661201"
---
# <a name="go-to-command"></a>Atteindre, commande
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Déplace le curseur à la ligne spécifiée.

## <a name="syntax"></a>Syntaxe

```
Edit.GoTo [linenumber]
```

## <a name="arguments"></a>Arguments
 `linenumber` Facultatif. Nombre entier représentant le numéro de la ligne à atteindre.

## <a name="remarks"></a>Remarques
 La numérotation des lignes débute à 1. Si la valeur de `linenumber` est inférieure à 1, la première ligne est affichée. Si la valeur de `linenumber` est supérieure au numéro de la dernière ligne, la dernière ligne est affichée.

 Si aucune valeur n’est spécifiée pour `linenumber`, la boîte de dialogue **Atteindre la ligne** s’affiche.

 L’alias de cette commande est GoToLn.

## <a name="example"></a>Exemples

```
>Edit.GoTo 125
```

## <a name="see-also"></a>Voir aussi
 [Commandes Visual Studio](../../ide/reference/visual-studio-commands.md) [fenêtre commande](../../ide/reference/command-window.md) [Rechercher/zone de commande](../../ide/find-command-box.md) [alias de commandes Visual Studio](../../ide/reference/visual-studio-command-aliases.md)
