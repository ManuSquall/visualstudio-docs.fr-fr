---
title: -Setup (devenv.exe) | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- setup Devenv switch
- /setup Devenv switch
- Devenv, /setup switch
ms.assetid: 87608b7f-a156-400c-80f5-fc823f843e61
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 75b7fb7d812135014a8b868ef7590c99e83c15b5
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47504650"
---
# <a name="setup-devenvexe"></a>/Setup (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [-le programme d’installation (devenv.exe)](https://docs.microsoft.com/visualstudio/ide/reference/setup-devenv-exe).  
  
  
Force [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] à fusionner les métadonnées des ressources qui décrivent les menus, les barres d’outils et les groupes de commandes de tous les packages Visual Studio disponibles.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
devenv /setup  
```  
  
## <a name="remarks"></a>Notes  
 Ce commutateur ne prend aucun argument. La commande `devenv /setup` est généralement utilisée comme dernière étape du processus d’installation. L’utilisation du commutateur `/setup` ne démarre pas [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].  
  
 Vous devez exécuter `devenv` en tant qu’administrateur pour pouvoir utiliser les commutateurs [/setup (devenv.exe)](../../ide/reference/setup-devenv-exe.md) et [/InstallVSTemplates (devenv.exe)](../../ide/reference/installvstemplates-devenv-exe.md) .  
  
## <a name="example"></a>Exemple  
 Cet exemple montre la dernière étape de l’installation d’une version de [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] qui inclut des packages Visual Studio.  
  
```  
devenv /setup  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Commutateurs de la ligne de commande Devenv](../../ide/reference/devenv-command-line-switches.md)



