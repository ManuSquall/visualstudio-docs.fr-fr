---
title: -Setup (devenv.exe) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- setup Devenv switch
- /setup Devenv switch
- Devenv, /setup switch
ms.assetid: 87608b7f-a156-400c-80f5-fc823f843e61
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: a923d1f3532548ebc6ed651a0739e0e5792f7967
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72663531"
---
# <a name="setup-devenvexe"></a>/Setup (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Force [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] à fusionner les métadonnées des ressources qui décrivent les menus, les barres d’outils et les groupes de commandes de tous les packages Visual Studio disponibles.

## <a name="syntax"></a>Syntaxe

```
devenv /setup
```

## <a name="remarks"></a>Remarques
 Ce commutateur ne prend aucun argument. La commande `devenv /setup` est généralement utilisée comme dernière étape du processus d’installation. L’utilisation du commutateur `/setup` ne démarre pas [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].

 Vous devez exécuter `devenv` en tant qu’administrateur pour pouvoir utiliser les commutateurs [/setup (devenv.exe)](../../ide/reference/setup-devenv-exe.md) et [/InstallVSTemplates (devenv.exe)](../../ide/reference/installvstemplates-devenv-exe.md) .

## <a name="example"></a>Exemples
 Cet exemple montre la dernière étape de l’installation d’une version de [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] qui inclut des packages Visual Studio.

```
devenv /setup
```

## <a name="see-also"></a>Voir aussi
 [Commutateurs de la ligne de commande Devenv](../../ide/reference/devenv-command-line-switches.md)
