---
title: Espion, commande | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- debug.watch
helpviewer_keywords:
- Watch command
- Debug.Watch command
ms.assetid: aa02e647-d9f5-4905-a651-52a8df595795
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 18e585064bb50db7a0497c6b96e428a662e953ab
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72604835"
---
# <a name="watch-command"></a>Espion, commande
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Crée et ouvre une instance spécifiée d’une fenêtre **Espion** . Vous pouvez utiliser une fenêtre **Espion** pour calculer les valeurs des variables, des expressions et des registres, modifier ces valeurs et enregistrer les résultats.

## <a name="syntax"></a>Syntaxe

```
Debug.Watch[index]
```

## <a name="arguments"></a>Arguments
 `index` Obligatoire. Numéro d’instance de la fenêtre Espion.

## <a name="remarks"></a>Remarques
 La valeur d’`index` doit être un entier. Les valeurs valides sont 1, 2, 3 ou 4.

## <a name="example"></a>Exemples

```
>Debug.Watch1
```

## <a name="see-also"></a>Voir aussi
 [Automatique et variables Windows](../../debugger/autos-and-locals-windows.md) [procédure : modifier une valeur dans une fenêtre de variables](https://msdn.microsoft.com/library/36f464ab-c900-4c0b-9ab3-557b3d9cdab5) [Comment : utiliser la boîte de dialogue Espion express](https://msdn.microsoft.com/library/ffaee1dd-e5ce-4ef2-9401-d28329398867) [commandes Visual Studio](../../ide/reference/visual-studio-commands.md) [fenêtre commande](../../ide/reference/command-window.md) [Rechercher/zone de commande](../../ide/find-command-box.md) [alias de commandes Visual Studio](../../ide/reference/visual-studio-command-aliases.md)
