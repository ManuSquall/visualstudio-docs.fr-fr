---
title: -Log (devenv.exe) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Devenv, /Log switch
- Log switch [devenv.exe]
- /Log Devenv switch
ms.assetid: ae23c4ae-2376-4fe3-b8d2-81d34e61c8ba
caps.latest.revision: "8"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: cf5ab0e1949716005d12d51d06b0d915344833aa
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="log-devenvexe"></a>/Log (devenv.exe)
Enregistre toute l'activité dans le fichier journal de résolution des problèmes. Ce fichier apparaît une fois que vous avez appelé `devenv /log` au moins une fois. Par défaut, le fichier journal est :  
  
 *%APPDATA%*\Microsoft\VisualStudio\\*Version*\ActivityLog.xml  
  
 où *Version* est la version de Visual Studio. Toutefois, vous pouvez spécifier un autre chemin d’accès et/ou nom de fichier.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
Devenv /log Path\NameOfLogFile  
```  
  
## <a name="remarks"></a>Remarques  
 Ce commutateur doit apparaître à la fin de la ligne de commande, après tous les autres commutateurs.  
  
 Le journal est rédigé pour toutes les instances de Visual Studio que vous avez appelées avec le commutateur /log. Il ne consigne pas les instances de Visual Studio que vous avez appelées sans ce commutateur.  
  
## <a name="see-also"></a>Voir aussi  
 [Commutateurs de la ligne de commande Devenv](../../ide/reference/devenv-command-line-switches.md)