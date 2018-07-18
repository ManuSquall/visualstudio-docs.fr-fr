---
title: Définir le frame de pile en cours, commande
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- debug.setcurrentstackframe
helpviewer_keywords:
- Set Current Stack Frame command
- Debug.SetCurrentStackFrame command
ms.assetid: 3dcf52c0-6781-4598-bac2-0094dce67c20
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 95f8c762f16eb4a784ccc2cffb5bfa27d215370e
ms.sourcegitcommit: fe5a72bc4c291500f0bf4d6e0778107eb8c905f5
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33704796"
---
# <a name="set-current-stack-frame-command"></a>Définir le frame de pile en cours, commande
Vous permet de définir un frame de pile spécifique.

## <a name="syntax"></a>Syntaxe

```cmd
Debug.SetCurrentStackFrame index
```

## <a name="arguments"></a>Arguments
 `index`

 Obligatoire. Sélectionne un frame de pile par son index.

## <a name="example"></a>Exemple

```cmd
>Debug.SetCurrentStackFrame 1
```

## <a name="see-also"></a>Voir aussi

- [Commandes Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Commande, fenêtre](../../ide/reference/command-window.md)
- [Rechercher/Commande, zone](../../ide/find-command-box.md)
- [Alias de commandes Visual Studio](../../ide/reference/visual-studio-command-aliases.md)