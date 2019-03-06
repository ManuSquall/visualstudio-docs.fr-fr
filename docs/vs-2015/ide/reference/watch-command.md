---
title: Espion, commande | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- debug.watch
helpviewer_keywords:
- Watch command
- Debug.Watch command
ms.assetid: aa02e647-d9f5-4905-a651-52a8df595795
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: b1a04dce73dbf2551b51f2395b3512e62daf3766
ms.sourcegitcommit: a83c60bb00bf95e6bea037f0e1b9696c64deda3c
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 02/19/2019
ms.locfileid: "54788188"
---
# <a name="watch-command"></a>Espion, commande
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
Crée et ouvre une instance spécifiée d’une fenêtre **Espion** . Vous pouvez utiliser une fenêtre **Espion** pour calculer les valeurs des variables, des expressions et des registres, modifier ces valeurs et enregistrer les résultats.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
Debug.Watch[index]  
```  
  
## <a name="arguments"></a>Arguments  
 `index`  
 Obligatoire. Numéro d’instance de la fenêtre Espion.  
  
## <a name="remarks"></a>Remarques  
 La valeur d’`index` doit être un entier. Les valeurs valides sont 1, 2, 3 ou 4.  
  
## <a name="example"></a>Exemple  
  
```  
>Debug.Watch1  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Fenêtres Variables locales et Automatique](../../debugger/autos-and-locals-windows.md)   
 [Guide pratique pour modifier une valeur dans une fenêtre de variable](http://msdn.microsoft.com/library/36f464ab-c900-4c0b-9ab3-557b3d9cdab5)   
 [Guide pratique pour utiliser la boîte de dialogue Espion express](http://msdn.microsoft.com/library/ffaee1dd-e5ce-4ef2-9401-d28329398867)   
 [Commandes Visual Studio](../../ide/reference/visual-studio-commands.md)   
 [Fenêtre Commande](../../ide/reference/command-window.md)   
 [Zone Rechercher/Commande](../../ide/find-command-box.md)   
 [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)
