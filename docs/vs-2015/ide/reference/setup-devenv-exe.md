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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 6e5bbbf3a1a9601a46aa9d3080f0d20583b43d22
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68163309"
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
