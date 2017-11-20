---
title: UnInit | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4cd4fc0b-974a-4e61-9ea8-0aaa1a0c52ea
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 285cfb5a68055612fc7d77022b8f9d1d61067ded
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="uninit"></a>UnInit
Finalise le fichier journal de graphisme, ferme et libère les ressources qui ont été utilisés lors de l’application a été enregistre activement les informations graphiques.  
  
## <a name="syntax"></a>Syntaxe  
  
```C++  
void UnInit();  
```  
  
## <a name="remarks"></a>Remarques  
 `UnInit`est appelé automatiquement lorsqu’une instance de la `VsgDbg` la destruction de classe. Si le `VsgDbg` instance a été enregistre pas activement les informations graphiques, cela n’a aucun effet.  
  
 Après `UnInit` a été appelée sur une instance de la `VsgDbg` classe, un graphique de nouveau fichier journal peut être créé en appelant `Init` et finalisé en appelant `UnInit`. Vous pouvez répéter cette opération autant de fois que vous souhaitez utiliser le même `VsgDbg` instance pour créer des fichiers journaux de plusieurs graphiques indépendants.  
  
## <a name="see-also"></a>Voir aussi  
 [Init](init.md)