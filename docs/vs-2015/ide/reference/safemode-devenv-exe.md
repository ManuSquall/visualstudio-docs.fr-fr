---
title: -SafeMode (devenv.exe) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- /SafeMode Devenv switch
- Devenv, /SafeMode switch
- SafeMode switch
ms.assetid: b191f6a5-8f12-47ec-bcc7-b68149a22aa8
caps.latest.revision: 9
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 28480399238c1c915056d3929f8fd188cfff7eca
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72665510"
---
# <a name="safemode-devenvexe"></a>/SafeMode (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Démarre [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] en mode sans échec, en chargeant uniquement l’environnement et les services par défaut.

## <a name="syntax"></a>Syntaxe

```
devenv /SafeMode
```

## <a name="remarks"></a>Remarques
 Ce commutateur empêche le chargement de tous les packages VS tiers au démarrage de [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)], garantissant ainsi la stabilité de l’exécution.

## <a name="description"></a>Description
 L’exemple suivant démarre [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] en mode sans échec.

## <a name="code"></a>Code

```
Devenv.exe /SafeMode
```

## <a name="see-also"></a>Voir aussi
 [Commutateurs de la ligne de commande Devenv](../../ide/reference/devenv-command-line-switches.md)
