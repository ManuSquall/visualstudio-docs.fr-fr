---
title: Iactivescriptprofilercontrol3, Interface | Documents Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 64bc860a-54d4-475a-80f6-2f9dba6448ee
caps.latest.revision: "6"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: eed00579acfb09217183a1dd1d858a1e99257a2c
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptprofilercontrol3-interface"></a>IActiveScriptProfilerControl3, interface
Fournit une méthode pour énumérer les objets du tas GC associées à un moteur de script.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
interface IActiveScriptProfilerControl3 : IActiveScriptProfilerControl2  
```  
  
## <a name="methods"></a>Méthodes  
 [Méthode IActiveScriptProfilerControl3::EnumHeap](../../winscript/reference/iactivescriptprofilercontrol3-enumheap-method.md)  
 Retourne une interface ([iactivescriptprofilerheapenum, Interface](../../winscript/reference/iactivescriptprofilerheapenum-interface.md)) qui peut être utilisé pour itérer sur les objets du tas GC dans le contexte du moteur de script associé.