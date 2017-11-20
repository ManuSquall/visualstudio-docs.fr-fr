---
title: IDebugProviderProgramNode2::UnmarshalDebuggeeInterface | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugProviderProgramNode2::UnmarshalDebuggeeInterface
helpviewer_keywords: IDebugProviderProgramNode2::UnmarshalDebuggeeInterface
ms.assetid: 2e4653c5-10f1-493c-9973-f31d266c5d48
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: bb918c66e1b4b1b83a4919dd710f00c835f26045
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="idebugproviderprogramnode2unmarshaldebuggeeinterface"></a>IDebugProviderProgramNode2::UnmarshalDebuggeeInterface
Obtient une interface spécifiée au-delà des limites de processus.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT UnmarshalDebuggeeInterface(  
   REFIID riid,  
   void** ppvObject  
);  
```  
  
```csharp  
int UnmarshalDebuggeeInterface(  
   ref Guid   riid,  
   out IntPtr ppvObject  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `riid`  
 [in] GUID de l’interface à obtenir.  
  
 `ppvObject`  
 [out] Retourne l’objet qui implémente l’interface souhaitée. (C++) cela peut être converti directement vers le type d’interface voulu. (C#) utilisez le <xref:System.Runtime.InteropServices.Marshal.GetObjectForIUnknown%2A> méthode pour obtenir l’interface souhaitée.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.  
  
## <a name="remarks"></a>Remarques  
 Cette méthode est utilisée lorsque le moteur de débogage est en cours d’exécution le [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] espace de processus et le programme débogué est en cours d’exécution dans son propre espace de processus.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugProviderProgramNode2](../../../extensibility/debugger/reference/idebugproviderprogramnode2.md)