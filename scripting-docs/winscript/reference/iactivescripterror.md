---
title: IActiveScriptError | Documents Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords: IActiveScriptError interface
ms.assetid: c8e0288d-38ff-4145-a7e3-f8cdfb72eefe
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a403bf412a0c93a5c435e1a3184202ed68d406ea
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescripterror"></a>IActiveScriptError
Un objet qui implémente cette interface est passé à la [IActiveScriptSite::OnScriptError](../../winscript/reference/iactivescriptsite-onscripterror.md) méthode chaque fois que le moteur de script rencontre une erreur non gérée. L’hôte appelle ensuite les méthodes sur cet objet pour obtenir des informations sur l’erreur qui s’est produite.  
  
## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable  
  
|Méthode|Description|  
|------------|-----------------|  
|[IActiveScriptError::GetExceptionInfo](../../winscript/reference/iactivescripterror-getexceptioninfo.md)|Récupère les informations relatives à une erreur.|  
|[IActiveScriptError::GetSourcePosition](../../winscript/reference/iactivescripterror-getsourceposition.md)|Récupère l’emplacement où une erreur s’est produite dans le code source.|  
|[IActiveScriptError::GetSourceLineText](../../winscript/reference/iactivescripterror-getsourcelinetext.md)|Récupère la ligne dans le fichier source où une erreur s’est produite.|  
  
## <a name="see-also"></a>Voir aussi  
 [Interfaces de script actives](../../winscript/reference/active-script-interfaces.md)