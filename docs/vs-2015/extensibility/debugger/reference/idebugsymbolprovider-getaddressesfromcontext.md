---
title: 'IDebugSymbolProvider :: GetAddressesFromContext | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugSymbolProvider::GetAddressesFromContext
helpviewer_keywords:
- IDebugSymbolProvider::GetAddressesFromContext method
ms.assetid: a3124883-a255-4543-a5ec-e1c7a97beb69
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ebd36bdda5059a4fd3c0334a5a2f222aaae40f01
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68206011"
---
# <a name="idebugsymbolprovidergetaddressesfromcontext"></a>IDebugSymbolProvider::GetAddressesFromContext
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Cette méthode mappe un contexte de document à un tableau d’adresses de débogage.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
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
 dans Contexte du document.  
  
 `fStatmentOnly`  
 dans Si la valeur est TRUE, limite les adresses de débogage à une seule instruction.  
  
 `ppEnumBegAddresses`  
 à Retourne un énumérateur pour les adresses de début de débogage associées à cette instruction ou ligne.  
  
 `ppEnumEndAddresses`  
 à Retourne un énumérateur [IEnumDebugAddresses](../../../extensibility/debugger/reference/ienumdebugaddresses.md) pour les adresses de fin de débogage associées à cette instruction ou ligne.  
  
## <a name="return-value"></a>Valeur renvoyée  
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.  
  
## <a name="remarks"></a>Notes  
 Un contexte de document indique généralement une plage de lignes sources. Cette méthode fournit les adresses de débogage de début et de fin associées à ces lignes. Certains langages autorisent les instructions qui s’étendent sur plusieurs lignes, ou lignes contenant plusieurs instructions. Cette méthode fournit un indicateur pour limiter les adresses de débogage à une instruction unique.  
  
 Il est possible qu’une seule instruction ait plusieurs adresses de débogage, comme dans le cas de modèles.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)   
 [GetAddressesFromPosition](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromposition.md)   
 [IEnumDebugAddresses](../../../extensibility/debugger/reference/ienumdebugaddresses.md)
