---
title: "Définir la base, commande | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: debug.setradix
helpviewer_keywords:
- Set Radix command
- Debug.SetRadix command
ms.assetid: 6ffd1554-7530-4da4-b5f5-e276a5034f3b
caps.latest.revision: "11"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 060221e5abe0ff9082a04f8b75561a7e4dec9f64
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="set-radix-command"></a>Définir la base, commande
Définit ou retourne la base numérique utilisée pour afficher les valeurs entières.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
Debug.SetRadix [10 | 16 | hex | dec]  
```  
  
## <a name="arguments"></a>Arguments  
 `10` ou `16` ou `hex` ou `dec`  
 Facultatif. Indique un nombre décimal (10 ou dec) ou hexadécimal (16 ou hex). Si l’argument est omis, la valeur actuelle de la base est retournée.  
  
## <a name="example"></a>Exemple  
 Cet exemple configure l’environnement pour afficher les valeurs entières au format hexadécimal.  
  
```  
>Debug.SetRadix hex  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Commandes Visual Studio](../../ide/reference/visual-studio-commands.md)   
 [Fenêtre Commande](../../ide/reference/command-window.md)   
 [Zone Rechercher/Commande](../../ide/find-command-box.md)   
 [Alias de commande Visual Studio](../../ide/reference/visual-studio-command-aliases.md)