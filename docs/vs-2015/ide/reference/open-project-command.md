---
title: Ouvrir un projet, commande | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- file.openproject
helpviewer_keywords:
- op command
- File.OpenProject command
- Open Project command
ms.assetid: baa85f86-041b-49f4-9ced-0c397dc180e1
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 99596442f3aef9e4cb2d890438d29b96cdf4f083
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72671920"
---
# <a name="open-project-command"></a>Ouvrir un projet, commande
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Ouvre un projet existant.

## <a name="syntax"></a>Syntaxe

```
File.OpenProject filename
```

## <a name="arguments"></a>Arguments
 `filename` Obligatoire. Chemin complet et nom de fichier du projet à ouvrir.

 La syntaxe de l’argument `filename` nécessite que les chemins contenant des espaces utilisent des guillemets.

## <a name="remarks"></a>Remarques
 La saisie semi-automatique tente de deviner le chemin et le nom de fichier à mesure que vous tapez.

 Cette commande n’est pas disponible lors du débogage.

## <a name="example"></a>Exemples
 Cet exemple ouvre le projet [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] Test1.

```
>File.OpenProject "C:\My Projects\Test1\Test1.vbproj"
```

## <a name="see-also"></a>Voir aussi
 [Commandes Visual Studio](../../ide/reference/visual-studio-commands.md) [fenêtre commande](../../ide/reference/command-window.md) [Rechercher/zone de commande](../../ide/find-command-box.md) [alias de commandes Visual Studio](../../ide/reference/visual-studio-command-aliases.md)
