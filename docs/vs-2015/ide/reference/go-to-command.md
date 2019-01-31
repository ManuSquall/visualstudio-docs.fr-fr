---
title: Atteindre, commande | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- edit.goto
helpviewer_keywords:
- Debug.Goto command
- Go To command
ms.assetid: 201e1dd2-6701-467d-8cc1-faec2ef20511
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 50f91c4bdb17612d56534290a7b83b7df1d771c9
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54790018"
---
# <a name="go-to-command"></a>Atteindre, commande
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
Déplace le curseur à la ligne spécifiée.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
Edit.GoTo [linenumber]  
```  
  
## <a name="arguments"></a>Arguments  
 `linenumber`  
 Optionnel. Nombre entier représentant le numéro de la ligne à atteindre.  
  
## <a name="remarks"></a>Notes  
 La numérotation des lignes débute à 1. Si la valeur de `linenumber` est inférieure à 1, la première ligne est affichée. Si la valeur de `linenumber` est supérieure au numéro de la dernière ligne, la dernière ligne est affichée.  
  
 Si aucune valeur n’est spécifiée pour `linenumber`, la boîte de dialogue **Atteindre la ligne** s’affiche.  
  
 L’alias de cette commande est GoToLn.  
  
## <a name="example"></a>Exemple  
  
```  
>Edit.GoTo 125  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Commandes Visual Studio](../../ide/reference/visual-studio-commands.md)   
 [Fenêtre Commande](../../ide/reference/command-window.md)   
 [Zone Rechercher/Commande](../../ide/find-command-box.md)   
 [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)
