---
title: "Scriptprop_hostkeepalive, propriété | Documents Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: bfa199f2-28ba-4320-bc0f-2320fad018bd
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a39ae7100c5567d2b03b7998077b20b1078810aa
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="scriptprophostkeepalive-property"></a>SCRIPTPROP_HOSTKEEPALIVE, propriété
Permet de spécifier si le moteur de script doit être conservé entièrement fonctionnel, s’il existe des références en attente.  
  
 Utilisez [IActiveScriptProperty::SetProperty](../../winscript/reference/iactivescriptproperty-setproperty.md) pour définir cette propriété sur `true`. Si cette propriété est définie sur `true`, le moteur de script est conservé entièrement fonctionnel tant qu’il existe au moins une référence en attente pour le moteur de script ou un `IDispatch` pointeur vers un objet JavaScript créé à l’aide de l’écriture de scripts moteur. Lorsque cette propriété a la valeur `true`, vous ne devez pas explicitement fermer ou réinitialiser le moteur de script à l’aide de la [IActiveScript::Close](../../winscript/reference/iactivescript-close.md) ou [IActiveScript::SetScriptState](../../winscript/reference/iactivescript-setscriptstate.md) méthodes. La version de la dernière référence à un objet de script s’arrête le moteur de script.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
#define SCRIPTPROP_HOSTKEEPALIVE 0x70000004  
```  
  
## <a name="requirements"></a>Spécifications  
 Cette propriété s’affiche uniquement dans la version de activscp.idl qui est installé avec [!INCLUDE[win8](../../javascript/includes/win8-md.md)], avec 2707082 Ko pour Internet Explorer 8 sur [!INCLUDE[win7](../../winscript/reference/includes/win7-md.md)], ou avec 2722913 Ko pour Internet Explorer 9 sur [!INCLUDE[win7](../../winscript/reference/includes/win7-md.md)] ou [!INCLUDE[vista_first](../../winscript/reference/includes/vista-first-md.md)].