---
title: -ResetSkipPkgs (devenv.exe)
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- /ResetSkipPkgs Devenv switch
- Devenv, /ResetSkipPkgs switch
- ResetSkipPkgs switch
ms.assetid: 7ece64f9-cfa4-4b34-b0d9-1c338b9557b3
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 6199bf96bc631cf1018b2cb72a4d3c3cf7c703cc
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2018
---
# <a name="resetskippkgs-devenvexe"></a>/ResetSkipPkgs (devenv.exe)
Efface toutes les options pour ignorer le chargement ajouté aux packages VS par les utilisateurs qui souhaitent éviter de charger les packages VS à problème, puis démarre [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].

## <a name="syntax"></a>Syntaxe

```
Devenv /ResetSkipPkgs
```

## <a name="remarks"></a>Notes
 La présence d’une balise SkipLoading désactive le chargement d’un package VS. L’effacement de la balise réactive le chargement du package VS.

## <a name="example"></a>Exemple
 L’exemple suivant efface toutes les balises SkipLoading.

```
Devenv.exe /ResetSkipPkgs
```

## <a name="see-also"></a>Voir aussi

- [Commutateurs de la ligne de commande Devenv](../../ide/reference/devenv-command-line-switches.md)