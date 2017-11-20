---
title: IDebugEngine3::LoadSymbols | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugEngine3::LoadSymbols
helpviewer_keywords: IDebugEngine3::LoadSymbols
ms.assetid: c846a440-1d91-4d48-b8f1-82e902ae152b
caps.latest.revision: "7"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: ad486256b194ae0f03ed3fe41c23a71f2f9159c8
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
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
  
## <a name="remarks"></a>Remarques  
 Cela charge les symboles de débogage pour tous les modules référencés par ce moteur de débogage. Les symboles sont chargés uniquement si elles n’ont pas encore été chargés. Les symboles sont recherchés sur les chemins d’accès définies par un appel à [SetSymbolPath](../../../extensibility/debugger/reference/idebugengine3-setsymbolpath.md).  
  
## <a name="see-also"></a>Voir aussi  
 [SetSymbolPath](../../../extensibility/debugger/reference/idebugengine3-setsymbolpath.md)   
 [IDebugEngine3](../../../extensibility/debugger/reference/idebugengine3.md)