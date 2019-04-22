---
title: Définir le frame de pile en cours, commande | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- debug.setcurrentstackframe
helpviewer_keywords:
- Set Current Stack Frame command
- Debug.SetCurrentStackFrame command
ms.assetid: 3dcf52c0-6781-4598-bac2-0094dce67c20
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 87d830e492420844de72a2cd34dbea336e365dfd
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 04/17/2019
ms.locfileid: "59660448"
---
# <a name="set-current-stack-frame-command"></a>Définir le frame de pile en cours, commande
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Vous permet de définir un frame de pile spécifique.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
Debug.SetCurrentStackFrame index  
```  
  
## <a name="arguments"></a>Arguments  
 `index`  
 Obligatoire. Sélectionne un frame de pile par son index.  
  
## <a name="example"></a>Exemple  
  
```  
>Debug.SetCurrentStackFrame 1  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Commandes Visual Studio](../../ide/reference/visual-studio-commands.md)   
 [Fenêtre Commande](../../ide/reference/command-window.md)   
 [Zone Rechercher/Commande](../../ide/find-command-box.md)   
 [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)
