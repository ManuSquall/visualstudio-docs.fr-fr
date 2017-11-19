---
title: IDebugSymbolProvider::GetAddressesFromContext | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugSymbolProvider::GetAddressesFromContext
helpviewer_keywords: IDebugSymbolProvider::GetAddressesFromContext method
ms.assetid: a3124883-a255-4543-a5ec-e1c7a97beb69
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d2499fb1cca7dcbbf278d00c0aac205774d3cb75
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="idebugsymbolprovidergetaddressesfromcontext"></a>IDebugSymbolProvider::GetAddressesFromContext
Cette méthode mappe un contexte de document dans un tableau d’adresses de débogage.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetAddressesFromContext(   
   IDebugDocumentContext2* pDocContext,  
   BOOL                    fStatmentOnly,  
   IEnumDebugAddresses**   ppEnumBegAddresses,  
   IEnumDebugAddresses**   ppEnumEndAddresses  
);  
```  
  
```csharp  
int GetAddressesFromContext(  
   IDebugDocumentContext2  pDocContext,  
   bool                    fStatmentOnly,  
   out IEnumDebugAddresses ppEnumBegAddresses,  
   out IEnumDebugAddresses ppEnumEndAddresses  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pDocContext`  
 [in] Le contexte de document.  
  
 `fStatmentOnly`  
 [in] Si la valeur est TRUE, limite les adresses de débogage à une seule instruction.  
  
 `ppEnumBegAddresses`  
 [out] Retourne un énumérateur pour les adresses de débogage de début associée à cette instruction ou d’une ligne.  
  
 `ppEnumEndAddresses`  
 [out] Retourne un [IEnumDebugAddresses](../../../extensibility/debugger/reference/ienumdebugaddresses.md) énumérateur pour les adresses de débogage fin associée à cette instruction ou d’une ligne.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.  
  
## <a name="remarks"></a>Remarques  
 Un contexte de document indique généralement une plage de lignes de code source. Cette méthode fournit le début et fin des adresses de débogage associées à ces lignes. Certains langages permettent aux instructions qui s’étendent sur plusieurs lignes, ou qui contient plusieurs instructions. Cette méthode fournit un indicateur pour limiter les adresses de débogage à une seule instruction.  
  
 Il est possible qu’une seule instruction d’avoir plusieurs adresses de débogage, comme dans le cas de modèles.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)   
 [GetAddressesFromPosition](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromposition.md)   
 [IEnumDebugAddresses](../../../extensibility/debugger/reference/ienumdebugaddresses.md)