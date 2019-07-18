---
title: Définir le processus actuel | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- Debug.SetCurrentProcess command
- Set Current Process command
ms.assetid: 1e016ebd-aadd-411f-a606-03bf69d3f8aa
caps.latest.revision: 13
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: ed19c5b95351f8e9c34255a915fc6a446800f761
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68163347"
---
# <a name="set-current-process"></a>Définir le processus actuel
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Définit le processus spécifié comme processus actif dans le débogueur.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
Debug.SetCurrentProcess index  
```  
  
## <a name="arguments"></a>Arguments  
 `index`  
 Obligatoire. Index du processus.  
  
## <a name="remarks"></a>Remarques  
 Pendant le débogage, vous pouvez attacher plusieurs processus à la fois, mais seul l’un d’entre eux est actif dans le débogueur à un moment donné. Vous pouvez utiliser la commande `SetCurrentProcess` pour définir le processus actif.  
  
## <a name="example"></a>Exemples  
  
```  
>Debug.SetCurrentProcess 1  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Commandes Visual Studio](../../ide/reference/visual-studio-commands.md)   
 [Fenêtre Commande](../../ide/reference/command-window.md)   
 [Alias de commande Visual Studio](../../ide/reference/visual-studio-command-aliases.md)
