---
title: UnInit | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 4cd4fc0b-974a-4e61-9ea8-0aaa1a0c52ea
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 56aa940d65934f7cc72f692f5bdf5e44854d276c
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2018
ms.locfileid: "31471451"
---
# <a name="uninit"></a>UnInit
Finalise le fichier journal de graphisme, ferme et libère les ressources qui ont été utilisés lors de l’application a été enregistre activement les informations graphiques.  
  
## <a name="syntax"></a>Syntaxe  
  
```C++  
void UnInit();  
```  
  
## <a name="remarks"></a>Notes  
 `UnInit` est appelé automatiquement lorsqu’une instance de la `VsgDbg` la destruction de classe. Si le `VsgDbg` instance a été enregistre pas activement les informations graphiques, cela n’a aucun effet.  
  
 Après `UnInit` a été appelée sur une instance de la `VsgDbg` classe, un graphique de nouveau fichier journal peut être créé en appelant `Init` et finalisé en appelant `UnInit`. Vous pouvez répéter cette opération autant de fois que vous souhaitez utiliser le même `VsgDbg` instance pour créer des fichiers journaux de plusieurs graphiques indépendants.  
  
## <a name="see-also"></a>Voir aussi  
 [Init](init.md)