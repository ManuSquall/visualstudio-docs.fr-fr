---
title: -SafeMode (devenv.exe)
description: Découvrez comment utiliser le commutateur de ligne de commande de SafeMode pour démarrer Visual Studio en mode sans échec, en chargeant uniquement l’environnement et les services par défaut.
ms.custom: SEO-VS-2020
ms.date: 12/10/2018
ms.topic: reference
helpviewer_keywords:
- /SafeMode Devenv switch
- Devenv, /SafeMode switch
- SafeMode switch
ms.assetid: b191f6a5-8f12-47ec-bcc7-b68149a22aa8
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 1626776ec41bdbdfe5ad2b611516e62ada4f15a3
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99957866"
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
