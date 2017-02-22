---
title: "IDebugCoreServer3::CreateInstanceInServer | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugCoreServer3::CreateInstanceInServer"
helpviewer_keywords: 
  - "IDebugCoreServer3::CreateInstanceInServer"
ms.assetid: 76f36bae-f6ab-413c-a8a9-8808bfeba05b
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IDebugCoreServer3::CreateInstanceInServer
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

crée une instance d'un moteur de débogage sur le serveur.  
  
## Syntaxe  
  
```cpp#  
HRESULT CreateInstanceInServer(  
   LPCWSTR  szDll,  
   WORD     wLangId,  
   REFCLSID clsidObject,  
   REFIID   riid,  
   void**   ppvObject  
);  
```  
  
```c#  
int CreateInstanceInServer(  
   string     szDll,   
   ushort     wLangID,   
   ref Guid   clsidObject,   
   ref Guid   riid,   
   out IntPtr ppvObject  
);  
```  
  
#### Paramètres  
 `szDll`  
 \[in\]  Le chemin d'accès à la DLL qui implémente le CLSID spécifié dans le paramètre d' `clsidObject` .  Si c'est `NULL`, la fonction d' `CoCreateInstance` COM est appelée.  
  
 `wLangId`  
 \[in\]  paramètres régionaux du moteur de débogage.  Cela peut s'avérer 0 si la méthode d' [SetLocale](../../../extensibility/debugger/reference/idebugengine2-setlocale.md) est appelée.  
  
 `clsidObject`  
 \[in\]  Le CLSID du moteur de débogage à créer.  
  
 `riid`  
 \[in\]  ID de l'interface spécifique à récupérer de l'objet de classe.  
  
 `ppvObject`  
 \[out\]  interface d' `IUnknown` de l'objet instancié.  Effectuez un cast ou marshalez cet objet à l'interface souhaitée.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d'erreur.  
  
## Voir aussi  
 [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)   
 [SetLocale](../../../extensibility/debugger/reference/idebugengine2-setlocale.md)