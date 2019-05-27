---
title: IDebugDocumentText2::GetSize | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocumentText2::GetSize
helpviewer_keywords:
- IDebugDocumentText2::GetSize
ms.assetid: bf515a8f-dcee-4004-8f81-543d547ceaae
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 9207858bd43809cbc070935ae2f53f354d9d6f9b
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/24/2019
ms.locfileid: "66199158"
---
# <a name="idebugdocumenttext2getsize"></a>IDebugDocumentText2::GetSize
Récupère la taille du texte à cette position dans le document.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetSize( 
   ULONG* pcNumLines,
   ULONG* pcNumChars
);
```

```csharp
int GetSize( 
   ref uint pcNumLines,
   ref uint pcNumChars
);
```

## <a name="parameters"></a>Paramètres
`pcNumLines`\
[out] Retourne le nombre de lignes de texte.

`pcNumChars`\
[out] Retourne le nombre de caractères du texte.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.

## <a name="remarks"></a>Notes

 [C++ uniquement] Si une valeur particulière n’est pas souhaitée, passez une valeur NULL pour le paramètre.

 [C# uniquement] Les deux paramètres doivent être spécifiés.

## <a name="see-also"></a>Voir aussi
- [IDebugDocumentText2](../../../extensibility/debugger/reference/idebugdocumenttext2.md)