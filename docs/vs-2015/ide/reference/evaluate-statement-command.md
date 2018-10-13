---
title: Évaluer l’instruction, commande | Microsoft Docs
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
- debug.evaluatestatement
helpviewer_keywords:
- Debug.EvaluateStatement command
- Evaluate Statement command
ms.assetid: 032039bc-9477-4f93-9b9d-66d4be0e90f4
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: d3e50b519b162201d741f2460a8e9dbbe675c16e
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49230319"
---
# <a name="evaluate-statement-command"></a>Évaluer l'instruction, commande
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
Évalue et affiche l’instruction donnée.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
Debug.EvaluateStatement text   
```  
  
## <a name="arguments"></a>Arguments  
 `text`  
 Obligatoire. Instruction à évaluer.  
  
## <a name="remarks"></a>Notes  
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
 [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)



