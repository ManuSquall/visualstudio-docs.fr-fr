---
title: Interface IActiveScriptProfilerControl3 | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 64bc860a-54d4-475a-80f6-2f9dba6448ee
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: bebe351608b3136ac00a059bffab3535141e7fca
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/16/2019
ms.locfileid: "54344718"
---
# <a name="iactivescriptprofilercontrol3-interface"></a>IActiveScriptProfilerControl3, interface
Fournit une méthode pour énumérer les objets du tas de garbage collection associés à un moteur de script.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
interface IActiveScriptProfilerControl3 : IActiveScriptProfilerControl2  
```  
  
## <a name="methods"></a>Méthodes  
 [Méthode IActiveScriptProfilerControl3::EnumHeap](../../winscript/reference/iactivescriptprofilercontrol3-enumheap-method.md)  
 Retourne une interface ([iactivescriptprofilerheapenum, Interface](../../winscript/reference/iactivescriptprofilerheapenum-interface.md)) qui peut être utilisé pour itérer sur les objets du tas de garbage collection dans le contexte du moteur de script associé.