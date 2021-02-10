---
title: Définir le frame de pile en cours, commande
description: En savoir plus sur la commande définir le frame de pile actuel et sur la façon dont elle vous permet de définir un frame de pile spécifique.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- debug.setcurrentstackframe
helpviewer_keywords:
- Set Current Stack Frame command
- Debug.SetCurrentStackFrame command
ms.assetid: 3dcf52c0-6781-4598-bac2-0094dce67c20
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: e1c8d0ade87ee7759593c8a465b43439f71d50d4
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99957749"
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
- [Fenêtre commande](../../ide/reference/command-window.md)
- [Zone Rechercher/commande](../../ide/find-command-box.md)
- [Alias de commandes Visual Studio](../../ide/reference/visual-studio-command-aliases.md)