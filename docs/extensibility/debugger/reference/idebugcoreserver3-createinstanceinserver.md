---
title: IDebugCoreServer3::CreateInstanceInServer | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugCoreServer3::CreateInstanceInServer
helpviewer_keywords:
- IDebugCoreServer3::CreateInstanceInServer
ms.assetid: 76f36bae-f6ab-413c-a8a9-8808bfeba05b
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 71995e38cf58c23437cbb9a6d6973fbd09cab8ab
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="idebugcoreserver3createinstanceinserver"></a>IDebugCoreServer3::CreateInstanceInServer
Crée une instance d’un moteur de débogage sur le serveur.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT CreateInstanceInServer(  
   LPCWSTR  szDll,  
   WORD     wLangId,  
   REFCLSID clsidObject,  
   REFIID   riid,  
   void**   ppvObject  
);  
```  
  
```csharp  
int CreateInstanceInServer(  
   string     szDll,   
   ushort     wLangID,   
   ref Guid   clsidObject,   
   ref Guid   riid,   
   out IntPtr ppvObject  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `szDll`  
 [in] Chemin d’accès à la dll qui implémente le CLSID spécifié dans le `clsidObject` paramètre. S’il s’agit `NULL`, puis COM `CoCreateInstance` est appelée.  
  
 `wLangId`  
 [in] Paramètres régionaux du moteur de débogage. Cela peut être 0 si la [SetLocale](../../../extensibility/debugger/reference/idebugengine2-setlocale.md) méthode ne doit pas être appelée.  
  
 `clsidObject`  
 [in] CLSID du moteur de débogage à créer.  
  
 `riid`  
 [in] ID de l’interface spécifique pour récupérer à partir de l’objet de classe.  
  
 `ppvObject`  
 [out] `IUnknown` interface à partir de l’objet instancié. Effectuez un cast ou marshaler cet objet à l’interface souhaitée.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)   
 [SetLocale](../../../extensibility/debugger/reference/idebugengine2-setlocale.md)