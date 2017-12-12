---
title: "Évaluer l’instruction, commande | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: debug.evaluatestatement
helpviewer_keywords:
- Debug.EvaluateStatement command
- Evaluate Statement command
ms.assetid: 032039bc-9477-4f93-9b9d-66d4be0e90f4
caps.latest.revision: "12"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 46c80a49d0e043d7cdbffbc74698a29e10ab4795
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="evaluate-statement-command"></a>Évaluer l'instruction, commande
Évalue et affiche l’instruction donnée.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
Debug.EvaluateStatement text   
```  
  
## <a name="arguments"></a>Arguments  
 `text`  
 Obligatoire. Instruction à évaluer.  
  
## <a name="remarks"></a>Remarques  
 La fenêtre utilisée pour entrer la commande **EvaluateStatement** détermine si un signe égal (=) est interprété comme un opérateur de comparaison ou comme un opérateur d’assignation.  
  
 Dans la fenêtre **Commande**, un signe égal (=) est interprété comme un opérateur de comparaison. Ainsi, si les valeurs des variables `a` et `b` sont différentes, la commande  
  
```  
>Debug.EvaluateStatement(a=b)  
```  
  
 retourne la valeur `false`.  
  
 Dans la fenêtre **Exécution**, en revanche, un signe égal (=) est interprété comme un opérateur d’assignation. Ainsi, la commande  
  
```  
>Debug.EvaluateStatement(a=b)  
```  
  
 assigne à la variable `a` la valeur de variable `b`.  
  
## <a name="example"></a>Exemple  
  
```  
>Debug.EvaluateStatement(a+b)  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Imprimer, commande](../../ide/reference/print-command.md)   
 [Commandes Visual Studio](../../ide/reference/visual-studio-commands.md)   
 [Fenêtre Commande](../../ide/reference/command-window.md)   
 [Zone Rechercher/Commande](../../ide/find-command-box.md)   
 [Alias de commande Visual Studio](../../ide/reference/visual-studio-command-aliases.md)