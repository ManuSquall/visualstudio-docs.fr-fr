---
description: Récupère la taille du texte à cette position dans le document.
title: 'IDebugDocumentText2 :: obtient | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocumentText2::GetSize
helpviewer_keywords:
- IDebugDocumentText2::GetSize
ms.assetid: bf515a8f-dcee-4004-8f81-543d547ceaae
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: d9499af30f9e9139d0ff64fcf17695b7a4ad69c9
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105066332"
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
à Retourne le nombre de lignes de texte.

`pcNumChars`\
à Retourne le nombre de caractères du texte.

## <a name="return-value"></a>Valeur renvoyée
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.

## <a name="remarks"></a>Notes

 [C++ uniquement] Si une valeur particulière n’est pas souhaitée, transmettez une valeur NULL pour le paramètre.

 [C# uniquement] Les deux paramètres doivent être spécifiés.

## <a name="see-also"></a>Voir aussi
- [IDebugDocumentText2](../../../extensibility/debugger/reference/idebugdocumenttext2.md)
