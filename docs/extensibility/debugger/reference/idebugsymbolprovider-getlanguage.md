---
description: Cette méthode obtient le langage utilisé pour compiler le code à l’adresse de débogage.
title: 'IDebugSymbolProvider :: GetLanguage | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugSymbolProvider::GetLanguage
helpviewer_keywords:
- IDebugSymbolProvider::GetLanguage method
ms.assetid: e4142183-3d8b-418f-907f-4ee4c753d8ce
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e7bcf2bd16212767fc8eff6106cdb3602bc293c9
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105086987"
---
# <a name="idebugsymbolprovidergetlanguage"></a>IDebugSymbolProvider::GetLanguage
Cette méthode obtient le langage utilisé pour compiler le code à l’adresse de débogage.

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
dans Objet d’adresse représenté par une interface [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) .

`pguidLanguage`\
à Retourne un `GUID` qui spécifie le langage.

`pguidLanguageVendor`\
à Retourne un `GUID` qui spécifie le fournisseur de langage.

## <a name="return-value"></a>Valeur renvoyée
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.

## <a name="remarks"></a>Notes
 Le moteur de débogage appelle cette méthode pour obtenir les informations dont il a besoin pour sélectionner l’évaluateur d’expression approprié.

## <a name="see-also"></a>Voir aussi
- [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)
- [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)
