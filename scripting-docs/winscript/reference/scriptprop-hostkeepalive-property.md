---
title: Scriptprop_hostkeepalive, propriété | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: bfa199f2-28ba-4320-bc0f-2320fad018bd
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3724bfcb1ec42617cda4c89269cb0160accafb1a
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/19/2019
ms.locfileid: "58150203"
---
# <a name="scriptprophostkeepalive-property"></a>SCRIPTPROP_HOSTKEEPALIVE, propriété
Permet de spécifier si le moteur de script doit être conservé entièrement fonctionnel, s’il existe des références en suspens.  
  
 Utilisez [IActiveScriptProperty::SetProperty](../../winscript/reference/iactivescriptproperty-setproperty.md) pour définir cette propriété sur `true`. Si cette propriété est définie sur `true`, le moteur de script est conservé entièrement fonctionnel tant qu’il existe au moins une référence en suspens au moteur de script lui-même ou à un `IDispatch` pointeur vers un objet JavaScript créé à l’aide de l’écriture de scripts moteur. Lorsque cette propriété a la valeur `true`, vous ne devez pas explicitement fermer ou réinitialiser le moteur de script à l’aide de la [IActiveScript::Close](../../winscript/reference/iactivescript-close.md) ou [IActiveScript::SetScriptState](../../winscript/reference/iactivescript-setscriptstate.md) méthodes. La version de la dernière référence à un objet de script s’arrête le moteur de script.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
#define SCRIPTPROP_HOSTKEEPALIVE 0x70000004  
```  
  
## <a name="requirements"></a>Spécifications  
 Cette propriété apparaît uniquement dans la version de activscp.idl qui est installé avec [!INCLUDE[win8](../../javascript/includes/win8-md.md)], avec 2707082 Ko pour Internet Explorer 8 sur [!INCLUDE[win7](../../winscript/reference/includes/win7-md.md)], ou avec 2722913 Ko pour Internet Explorer 9 sur [!INCLUDE[win7](../../winscript/reference/includes/win7-md.md)] ou [!INCLUDE[vista_first](../../winscript/reference/includes/vista-first-md.md)].