---
title: Espion, commande | Microsoft Docs
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
- debug.watch
helpviewer_keywords:
- Watch command
- Debug.Watch command
ms.assetid: aa02e647-d9f5-4905-a651-52a8df595795
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 9b1d5a1a1ffac1c67b5a3a1e1ad4a860c6b2ad4f
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49214355"
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
  
## <a name="remarks"></a>Notes  
 La valeur d’`index` doit être un entier. Les valeurs valides sont 1, 2, 3 ou 4.  
  
## <a name="example"></a>Exemple  
  
```  
>Debug.Watch1  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Fenêtres Variables locales et Automatique](../../debugger/autos-and-locals-windows.md)   
 [Comment : modifier une valeur dans une fenêtre de Variable](http://msdn.microsoft.com/library/36f464ab-c900-4c0b-9ab3-557b3d9cdab5)   
 [Comment : utiliser la boîte de dialogue Espion express](http://msdn.microsoft.com/library/ffaee1dd-e5ce-4ef2-9401-d28329398867)   
 [Commandes Visual Studio](../../ide/reference/visual-studio-commands.md)   
 [Fenêtre Commande](../../ide/reference/command-window.md)   
 [Zone Rechercher/Commande](../../ide/find-command-box.md)   
 [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)



