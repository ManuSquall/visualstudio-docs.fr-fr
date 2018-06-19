---
title: JsRuntimeHandle, typedef | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 69e59bfd-9b0e-4710-9aa8-fbd6844171bc
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d3c0344e203c58691048c55ba4080c6c86c1c643
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24568709"
---
# <a name="jsruntimehandle-typedef"></a>JsRuntimeHandle, typedef
Un handle vers un runtime Chakra.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
typedef void *JsRuntimeHandle;  
```  
  
## <a name="remarks"></a>Remarques  
 Chaque runtime Chakra a son propre moteur d'exécution indépendant, son compilateur JIT et son tas récupéré par le garbage collector. Ainsi, chaque runtime est complètement isolé des autres runtimes.  
  
 Les runtimes peuvent être utilisés par tous les threads, mais il ne peut y avoir qu'un seul appel de thread à la fois dans un runtime.  
  
> [!WARNING]
>  Un handle JsRuntimeHandle, au contraire des autres références d'objet dans l'API hébergeant Chakra, n'est pas récupéré par le garbage collector car il contient le tas récupéré par le garbage collector lui-même. Un runtime continue d'exister jusqu'à ce que JsDisposeRuntime soit appelé.  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** jsrt.h  
  
## <a name="see-also"></a>Voir aussi  
 [Référence (JavaScript Runtime)](../chakra-hosting/reference-javascript-runtime.md)