---
title: Afficher la mémoire, commande | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- debug.listmemory
helpviewer_keywords:
- Debug.ListMemory command
- ListMemory command
- list memory command
ms.assetid: a84de361-a6a6-4f6d-96aa-a0d4a424371e
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 25be71041f0ab127037a25a03cff1d6ffe42ac97
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49224495"
---
# <a name="list-memory-command"></a>Afficher la mémoire, commande
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
Affiche le contenu de la plage de mémoire spécifiée.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
Debug.ListMemory [/ANSI|Unicode] [/Count:number] [/Format:formattype]  
[/Hex|Signed|Unsigned] [expression]  
```  
  
## <a name="arguments"></a>Arguments  
 `expression`  
 Facultatif. Adresse mémoire à partir de laquelle la mémoire doit être affichée.  
  
## <a name="switches"></a>Commutateurs  
 /ANSI&#124;Unicode  
 Facultatif. Affiche la mémoire sous la forme de caractères ANSI ou Unicode correspondant aux octets de mémoire.  
  
 /Count:`number`  
 Facultatif. Détermine le nombre d’octets de mémoire à afficher, à partir de l’argument `expression`.  
  
 /Format:`formattype`  
 Facultatif. Type du format selon lequel les informations sur la mémoire sont affichées dans la fenêtre **Mémoire** ; le format peut être OneByte, TwoBytes, FourBytes, EightBytes, Float (32 bits) ou Double (64 bits). Si le format OneByte est utilisé, `/Unicode` n’est pas disponible.  
  
 /Hex&#124;Signed&#124;Unsigned  
 Facultatif. Spécifie le format d’affichage des nombres : signé, non signé ou hexadécimal.  
  
## <a name="remarks"></a>Notes  
 Au lieu d’écrire une commande **Debug.ListMemory** complète avec tous ses commutateurs, vous pouvez appeler la commande à l’aide d’alias préparamétrés avec certains commutateurs prédéfinis à des valeurs spécifiées. Par exemple, au lieu d’entrer :  
  
```  
>Debug.ListMemory /Format:float /Count:30 /Unicode  
```  
  
 vous pouvez écrire :  
  
```  
>df /Count:30 /Unicode  
```  
  
 Voici une liste des alias disponibles pour la commande **Debug.ListMemory** :  
  
|Alias|Commande et commutateurs|  
|-----------|--------------------------|  
|**d**|Debug.ListMemory|  
|**da**|Debug.ListMemory /Ansi|  
|**db**|Debug.ListMemory /Format:OneByte|  
|**dc**|Debug.ListMemory /Format:FourBytes /Ansi|  
|**dd**|Debug.ListMemory /Format:FourBytes|  
|**df**|Debug.ListMemory /Format:Float|  
|**dq**|Debug.ListMemory /Format:EightBytes|  
|**du**|Debug.ListMemory /Unicode|  
  
## <a name="example"></a>Exemple  
  
```  
>Debug.ListMemory /Format:float /Count:30 /Unicode  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Afficher la pile d’appels, commande](../../ide/reference/list-call-stack-command.md)   
 [Afficher les threads, commande](../../ide/reference/list-threads-command.md)   
 [Commandes Visual Studio](../../ide/reference/visual-studio-commands.md)   
 [Fenêtre Commande](../../ide/reference/command-window.md)   
 [Zone Rechercher/Commande](../../ide/find-command-box.md)   
 [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)




