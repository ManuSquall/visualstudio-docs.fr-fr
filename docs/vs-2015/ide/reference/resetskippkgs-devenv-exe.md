---
title: -ResetSkipPkgs (devenv.exe) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- /ResetSkipPkgs Devenv switch
- Devenv, /ResetSkipPkgs switch
- ResetSkipPkgs switch
ms.assetid: 7ece64f9-cfa4-4b34-b0d9-1c338b9557b3
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 207ceb92d84c2186aeec49c205d8d32f4d7aa969
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72665571"
---
# <a name="resetskippkgs-devenvexe"></a>/ResetSkipPkgs (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Efface toutes les options pour ignorer le chargement ajouté aux packages VS par les utilisateurs qui souhaitent éviter de charger les packages VS à problème, puis démarre [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].

## <a name="syntax"></a>Syntaxe

```
Devenv /ResetSkipPkgs
```

## <a name="remarks"></a>Remarques
 La présence d’une balise SkipLoading désactive le chargement d’un package VS. L’effacement de la balise réactive le chargement du package VS.

## <a name="example"></a>Exemples
 L’exemple suivant efface toutes les balises SkipLoading.

```
Devenv.exe /ResetSkipPkgs
```

## <a name="see-also"></a>Voir aussi
 [Commutateurs de la ligne de commande Devenv](../../ide/reference/devenv-command-line-switches.md)
