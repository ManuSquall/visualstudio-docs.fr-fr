---
title: 'IDebugEngine2 :: SetRegistryRoot | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugEngine2::SetRegistryRoot
helpviewer_keywords:
- IDebugEngine2::SetRegistryRoot
ms.assetid: d0d81202-8a4a-4bc3-b297-30a047c5ec60
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 39bb532301d34a3abf9988cfa909e1606c3c73e8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68195945"
---
# <a name="idebugengine2setregistryroot"></a>IDebugEngine2::SetRegistryRoot
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Définit la racine du Registre pour le moteur de débogage (DE).  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT SetRegistryRoot(   
   LPCOLESTR pszRegistryRoot  
);  
```  
  
```csharp  
int SetRegistryRoot(   
   string pszRegistryRoot  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pszRegistryRoot`  
 dans Racine du Registre à utiliser.  
  
## <a name="return-value"></a>Valeur renvoyée  
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.  
  
## <a name="remarks"></a>Notes  
 Cette méthode permet [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] de spécifier une racine de registre de remplacement que le de doit utiliser pour obtenir des paramètres de Registre, par exemple « HKEY_LOCAL_MACHINE \software\microsoft\visualstudio\8.0exp ».  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
