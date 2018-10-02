---
title: UnInit | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4cd4fc0b-974a-4e61-9ea8-0aaa1a0c52ea
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4cd66d7329fa4bfc288f3d60879e45cc86ded94e
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47495956"
---
# <a name="uninit"></a>UnInit
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [UnInit](https://docs.microsoft.com/visualstudio/debugger/graphics/uninit).  
  
Finalise le fichier journal de graphisme, il ferme et libère les ressources qui ont été utilisés pendant que l’application a été enregistre activement les informations graphiques.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
void UnInit();  
```  
  
## <a name="remarks"></a>Notes  
 `UnInit` est appelée automatiquement lorsqu’une instance de la `VsgDbg` classe est détruite. Si le `VsgDbg` instance a été pas activement l’enregistrement des informations graphiques, cela n’a aucun effet.  
  
 Après `UnInit` a été appelée sur une instance de la `VsgDbg` classe, un graphique nouveau fichier journal peut être créé en appelant `Init` et finalisation en appelant `UnInit`. Vous pouvez répéter cette opération autant de fois que vous souhaitez utiliser le même `VsgDbg` instance pour créer des graphiques indépendants plusieurs fichiers journaux.  
  
## <a name="see-also"></a>Voir aussi  
 [Init](../debugger/init.md)



