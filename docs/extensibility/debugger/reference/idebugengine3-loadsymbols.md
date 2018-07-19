---
title: IDebugEngine3::LoadSymbols | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugEngine3::LoadSymbols
helpviewer_keywords:
- IDebugEngine3::LoadSymbols
ms.assetid: c846a440-1d91-4d48-b8f1-82e902ae152b
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: fde88d8ecc31c9e1326b36da33c7fd96530ff86d
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31110765"
---
# <a name="idebugengine3loadsymbols"></a>IDebugEngine3::LoadSymbols
Symboles de charge (si nécessaire) pour tous les modules en cours de débogage par ce moteur de débogage.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT LoadSymbols();  
```  
  
```csharp  
int LoadSymbols();  
```  
  
#### <a name="parameters"></a>Paramètres  
 Aucun.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne S_OK ; sinon retourne le code d’erreur.  
  
## <a name="remarks"></a>Notes  
 Cela charge les symboles de débogage pour tous les modules référencés par ce moteur de débogage. Les symboles sont chargés uniquement si elles n’ont pas encore été chargés. Les symboles sont recherchés sur les chemins d’accès définies par un appel à [SetSymbolPath](../../../extensibility/debugger/reference/idebugengine3-setsymbolpath.md).  
  
## <a name="see-also"></a>Voir aussi  
 [SetSymbolPath](../../../extensibility/debugger/reference/idebugengine3-setsymbolpath.md)   
 [IDebugEngine3](../../../extensibility/debugger/reference/idebugengine3.md)