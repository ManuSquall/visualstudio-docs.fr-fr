---
title: -SafeMode (devenv.exe)
ms.date: 12/10/2018
ms.topic: reference
helpviewer_keywords:
- /SafeMode Devenv switch
- Devenv, /SafeMode switch
- SafeMode switch
ms.assetid: b191f6a5-8f12-47ec-bcc7-b68149a22aa8
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: abaeded184db78085a9629da0e763b2f76dbd328
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72655512"
---
# <a name="safemode-devenvexe"></a>/SafeMode (devenv.exe)

Lance Visual Studio en mode sans échec, en chargeant uniquement l’environnement et les services par défaut.

## <a name="syntax"></a>Syntaxe

```shell
devenv /SafeMode
```

## <a name="remarks"></a>Notes

Ce commutateur empêche le chargement de tous les packages VS tiers au démarrage de Visual Studio, garantissant ainsi la stabilité de l’exécution.

## <a name="example"></a>Exemple

L’exemple suivant démarre Visual Studio en mode sans échec.

```shell
devenv /safemode
```

## <a name="see-also"></a>Voir aussi

- [Commutateurs de ligne de commande Devenv](../../ide/reference/devenv-command-line-switches.md)