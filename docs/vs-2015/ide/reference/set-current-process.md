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
ms.openlocfilehash: be451ee1a0b4361e44c8be96713872ca0ee3bd76
ms.sourcegitcommit: a83c60bb00bf95e6bea037f0e1b9696c64deda3c
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 02/19/2019
ms.locfileid: "54768846"
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
  
## <a name="example"></a>Exemple  
  
```  
>Debug.SetCurrentProcess 1  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Commandes Visual Studio](../../ide/reference/visual-studio-commands.md)   
 [Fenêtre Commande](../../ide/reference/command-window.md)   
 [Alias de commande Visual Studio](../../ide/reference/visual-studio-command-aliases.md)
