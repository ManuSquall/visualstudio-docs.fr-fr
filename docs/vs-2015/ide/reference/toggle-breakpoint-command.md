---
title: Basculer le point d’arrêt, commande | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- debug.togglebreakpoint
helpviewer_keywords:
- ToggleBreakpoint command
- Debug.ToggleBreakPoint command
- Toggle Breakpoint command
ms.assetid: d50dfadb-ce79-4d5e-9c09-1cfddd57876d
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: c7dd3bd7a4d42b8135aed034464223af53091f87
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47493191"
---
# <a name="toggle-breakpoint-command"></a>Basculer le point d'arrêt, commande
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [basculer le point d’arrêt, commande](https://docs.microsoft.com/visualstudio/ide/reference/toggle-breakpoint-command).  
  
  
Active ou désactive le point d’arrêt, en fonction de son état actuel, à l’emplacement actuel dans le fichier.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
Debug.ToggleBreakpoint [text]  
```  
  
## <a name="arguments"></a>Arguments  
 `text`  
 Facultatif. Si l’argument text est spécifié, la ligne est marquée en tant que point d’arrêt nommé. Sinon, la ligne est marquée en tant que point d’arrêt non nommé, ce qui revient à appuyer sur la touche F9.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant bascule le point d’arrêt actuel.  
  
```  
>Debug.ToggleBreakpoint  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Commandes Visual Studio](../../ide/reference/visual-studio-commands.md)   
 [Fenêtre Commande](../../ide/reference/command-window.md)   
 [Zone Rechercher/Commande](../../ide/find-command-box.md)   
 [Alias de commandes Visual Studio](../../ide/reference/visual-studio-command-aliases.md)



