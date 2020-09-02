---
title: UnInit | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 4cd4fc0b-974a-4e61-9ea8-0aaa1a0c52ea
caps.latest.revision: 7
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 0bec86a7f872057b7a0d652df6346e3a1ef2ff8a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68197939"
---
# <a name="uninit"></a>UnInit
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Finalise le fichier journal de graphisme, le ferme et libère les ressources qui ont été utilisées pendant que l’application enregistrait activement des informations graphiques.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
void UnInit();  
```  
  
## <a name="remarks"></a>Notes  
 `UnInit` est appelé automatiquement lorsqu’une instance de la `VsgDbg` classe est détruite. Si l' `VsgDbg` instance n’enregistrait pas activement les informations graphiques, cela n’a aucun effet.  
  
 Une fois que `UnInit` a été appelé sur une instance de la `VsgDbg` classe, un nouveau fichier journal de graphisme peut être créé en appelant `Init` et finalisé en appelant `UnInit` . Vous pouvez répéter cette opération autant de fois que vous le souhaitez pour utiliser la même `VsgDbg` instance afin de créer plusieurs fichiers journaux graphiques indépendants.  
  
## <a name="see-also"></a>Voir aussi  
 [Init](../debugger/init.md)
