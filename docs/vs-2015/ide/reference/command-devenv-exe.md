---
title: -Command (devenv.exe) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- Devenv, /command switch
- /command Devenv switch
ms.assetid: 13c20cd6-f09d-400a-8b7b-ecc266a32cef
caps.latest.revision: 14
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 9083d14c82eb2d283431e28d03bbbf96c14258cc
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72660854"
---
# <a name="command-devenvexe"></a>/Command (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Exécute la commande spécifiée après le lancement de l’environnement de développement intégré (IDE) [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].

## <a name="syntax"></a>Syntaxe

```
devenv /command CommandName
```

## <a name="arguments"></a>Arguments
 `CommandName` Obligatoire. Nom complet d’une commande [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] ou de son alias, entouré de guillemets doubles. Pour plus d’informations sur la syntaxe des commandes et des alias, consultez [Commandes Visual Studio](../../ide/reference/visual-studio-commands.md).

## <a name="remarks"></a>Remarques
 Une fois le démarrage terminé, l’IDE exécute la commande nommée. Si vous utilisez ce commutateur, l’IDE n’affiche pas la page de démarrage de [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] lors du démarrage.

 Si un complément expose une commande, vous pouvez utiliser ce commutateur pour lancer le complément à partir de la ligne de commande. Pour plus d’informations, consultez [Comment : contrôler des compléments avec le Gestionnaire de compléments](https://msdn.microsoft.com/library/4f60444a-cb48-4cdb-8df4-941f6419aeeb).

## <a name="example"></a>Exemples
 Cet exemple lance [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] et exécute automatiquement la macro Open Favorite Files.

```
devenv /command "Macros.MyMacros.Module1.OpenFavoriteFiles"
```

## <a name="see-also"></a>Voir aussi
 [Commutateurs de ligne de commande devenv commutateurs](../../ide/reference/devenv-command-line-switches.md) de [commande Visual Studio](../../ide/reference/visual-studio-command-aliases.md)
