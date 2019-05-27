---
title: IDebugSymbolProvider::GetLanguage | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugSymbolProvider::GetLanguage
helpviewer_keywords:
- IDebugSymbolProvider::GetLanguage method
ms.assetid: e4142183-3d8b-418f-907f-4ee4c753d8ce
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 86429e4ffe46fc182ea923f249bd5492dd433812
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/24/2019
ms.locfileid: "66207198"
---
# <a name="idebugsymbolprovidergetlanguage"></a>IDebugSymbolProvider::GetLanguage
Cette méthode obtient le langage ayant servi à compiler le code à l’adresse de débogage.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetLanguage( 
   IDebugAddress* pAddress,
   GUID*          pguidLanguage,
   GUID*          pguidLanguageVendor
);
```

```csharp
int GetLanguage(
   IDebugAddress pAddress,
   out Guid      pguidLanguage,
   out Guid      pguidLanguageVendor
);
```

## <a name="parameters"></a>Paramètres
`pAddress`\
[in] Un type d’objet représenté par un [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) interface.

`pguidLanguage`\
[out] Retourne un `GUID` qui spécifie le langage.

`pguidLanguageVendor`\
[out] Retourne un `GUID` qui spécifie le fournisseur de langage.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.

## <a name="remarks"></a>Notes
 Le moteur de débogage appelle cette méthode pour obtenir les informations nécessaires sélectionner l’évaluateur d’expression correcte.

## <a name="see-also"></a>Voir aussi
- [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)
- [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)