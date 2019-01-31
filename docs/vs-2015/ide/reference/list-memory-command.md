---
title: Afficher la mémoire, commande | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
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
manager: jillfra
ms.openlocfilehash: 057099c2ce1c4832c48d2eeac8774a36c5fad7b5
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54804293"
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
 Optionnel. Adresse mémoire à partir de laquelle la mémoire doit être affichée.  
  
## <a name="switches"></a>Commutateurs  
 /ANSI&#124;Unicode  
 Optionnel. Affiche la mémoire sous la forme de caractères ANSI ou Unicode correspondant aux octets de mémoire.  
  
 /Count:`number`  
 Optionnel. Détermine le nombre d’octets de mémoire à afficher, à partir de l’argument `expression`.  
  
 /Format:`formattype`  
 Optionnel. Type du format selon lequel les informations sur la mémoire sont affichées dans la fenêtre **Mémoire** ; le format peut être OneByte, TwoBytes, FourBytes, EightBytes, Float (32 bits) ou Double (64 bits). Si le format OneByte est utilisé, `/Unicode` n’est pas disponible.  
  
 /Hex&#124;Signed&#124;Unsigned  
 Optionnel. Spécifie le format d’affichage des nombres : signé, non signé ou hexadécimal.  
  
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
