---
title: "IDebugProviderProgramNode2::UnmarshalDebuggeeInterface | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProviderProgramNode2::UnmarshalDebuggeeInterface"
helpviewer_keywords: 
  - "IDebugProviderProgramNode2::UnmarshalDebuggeeInterface"
ms.assetid: 2e4653c5-10f1-493c-9973-f31d266c5d48
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugProviderProgramNode2::UnmarshalDebuggeeInterface
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Obtient une interface spécifiée au delà de les limites du processus.  
  
## Syntaxe  
  
```cpp  
HRESULT UnmarshalDebuggeeInterface(  
   REFIID riid,  
   void** ppvObject  
);  
```  
  
```c#  
int UnmarshalDebuggeeInterface(  
   ref Guid   riid,  
   out IntPtr ppvObject  
);  
```  
  
#### Paramètres  
 `riid`  
 \[in\]  Le GUID de l'interface à obtenir.  
  
 `ppvObject`  
 \[out\]  Retourne l'objet qui implémente l'interface souhaitée.  \[C\+\+\] cela peut être casté directement au type d'interface souhaité.  \[C\#\] utilisez la méthode d' <xref:System.Runtime.InteropServices.Marshal.GetObjectForIUnknown%2A> pour obtenir l'interface souhaitée.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d'erreur.  
  
## Notes  
 Cette méthode est utilisée lorsque le moteur de débogage s'exécute dans l'espace de processus de [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] et le programme débogué s'exécute dans son propre espace de processus.  
  
## Voir aussi  
 [IDebugProviderProgramNode2](../../../extensibility/debugger/reference/idebugproviderprogramnode2.md)