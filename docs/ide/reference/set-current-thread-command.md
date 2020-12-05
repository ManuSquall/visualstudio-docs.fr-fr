---
title: Définir le thread en cours, commande
description: En savoir plus sur la commande Set current thread et sur la façon dont elle définit le thread spécifié comme le thread actuel.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- debug.setcurrentthread
helpviewer_keywords:
- Set Current Thread command
- Debug.SetCurrentThread command
ms.assetid: 9917ed1d-6c30-4d94-b2f0-69acce74f1b2
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3cedd37ece7bcc0eb79ad52cc426b07f8cb2ca57
ms.sourcegitcommit: 2cf87f79762906ccaa133a7645aa4c77a0bed7da
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2020
ms.locfileid: "96616562"
---
# <a name="set-current-thread-command"></a>Définir le thread en cours, commande
Définit le thread spécifié comme thread actuel.

## <a name="syntax"></a>Syntaxe

```
Debug.SetCurrentThread index
```

## <a name="arguments"></a>Arguments
`index`

Obligatoire. Sélectionne un thread par son index.

## <a name="example"></a>Exemple

```
>Debug.SetCurrentThread 1
```

## <a name="see-also"></a>Voir aussi

- [Commandes Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Fenêtre commande](../../ide/reference/command-window.md)
- [Zone Rechercher/commande](../../ide/find-command-box.md)
- [Alias de commandes Visual Studio](../../ide/reference/visual-studio-command-aliases.md)