---
title: -Log (devenv.exe) | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Devenv, /Log switch
- Log switch [devenv.exe]
- /Log Devenv switch
ms.assetid: ae23c4ae-2376-4fe3-b8d2-81d34e61c8ba
caps.latest.revision: 13
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 6e3c8ee5d8c0bc5d68159fe0b40f22dda74f564f
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49292030"
---
# <a name="log-devenvexe"></a>/Log (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
Enregistre toute l'activité dans le fichier journal de résolution des problèmes. Ce fichier apparaît une fois que vous avez appelé `devenv /log` au moins une fois. Par défaut, le fichier journal est :  
  
 *%APPDATA%* \Microsoft\VisualStudio\\*Version*\ActivityLog.xml  
  
 où *Version* est la version de Visual Studio. Toutefois, vous pouvez spécifier un autre chemin d’accès et/ou nom de fichier.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
Devenv /log Path\NameOfLogFile  
```  
  
## <a name="remarks"></a>Notes  
 Ce commutateur doit apparaître à la fin de la ligne de commande, après tous les autres commutateurs.  
  
 Le journal est rédigé pour toutes les instances de Visual Studio que vous avez appelées avec le commutateur /log. Il ne consigne pas les instances de Visual Studio que vous avez appelées sans ce commutateur.  
  
## <a name="see-also"></a>Voir aussi  
 [Commutateurs de la ligne de commande Devenv](../../ide/reference/devenv-command-line-switches.md)



