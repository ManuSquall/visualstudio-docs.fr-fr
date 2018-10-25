---
title: IDebugSymbolProviderDirect::GetSymUnmanagedReader | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- GetSymUnmanagedReader
- IDebugSymbolProviderDirect::GetSymUnmanagedReader
ms.assetid: 147bacfa-f66c-43e0-8a72-e601058dc57f
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 705c5d1184f159309d289d70c7a787dc3fce03b9
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49872718"
---
# <a name="idebugsymbolproviderdirectgetsymunmanagedreader"></a>IDebugSymbolProviderDirect::GetSymUnmanagedReader
Récupère un lecteur de symboles du code non managé.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetSymUnmanagedReader (  
   ULONG32    ulAppDomainID,  
   GUID       guidModule,  
   IUnknown** ppSymUnmanagedReader  
);  
```  
  
```csharp  
int GetSymUnmanagedReader (  
   uint       ulAppDomainID,  
   Guid       guidModule,  
   out object ppSymUnmanagedReader  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `ulAppDomainID`  
 [in] Identificateur du domaine d’application.  
  
 `guidModule`  
 [in] Identificateur unique du module.  
  
 `ppSymUnmanagedReader`  
 [out] Retourne un objet qui représente le lecteur de symboles du code non managé.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugSymbolProviderDirect](../../../extensibility/debugger/reference/idebugsymbolproviderdirect.md)