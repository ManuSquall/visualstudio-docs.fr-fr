---
title: UnInit | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 4cd4fc0b-974a-4e61-9ea8-0aaa1a0c52ea
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 48c4e76105c024f9f414a884c2e3cabde716db86
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2019
ms.locfileid: "55019107"
---
# <a name="uninit"></a>UnInit
Finalise le fichier journal de graphisme, il ferme et libère les ressources qui ont été utilisés pendant que l’application a été enregistre activement les informations graphiques.  
  
## <a name="syntax"></a>Syntaxe  
  
```C++  
void UnInit();  
```  
  
## <a name="remarks"></a>Notes  
 `UnInit` est appelée automatiquement lorsqu’une instance de la `VsgDbg` classe est détruite. Si le `VsgDbg` instance a été pas activement l’enregistrement des informations graphiques, cela n’a aucun effet.  
  
 Après `UnInit` a été appelée sur une instance de la `VsgDbg` classe, un graphique nouveau fichier journal peut être créé en appelant `Init` et finalisation en appelant `UnInit`. Vous pouvez répéter cette opération autant de fois que vous souhaitez utiliser le même `VsgDbg` instance pour créer des graphiques indépendants plusieurs fichiers journaux.  
  
## <a name="see-also"></a>Voir aussi  
 [Init](init.md)