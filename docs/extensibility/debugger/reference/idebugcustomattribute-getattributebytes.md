---
description: Obtient les informations d’attribut sous la forme d’un objet blob d’octets.
title: 'IDebugCustomAttribute :: GetAttributeBytes | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCustomAttribute::GetAttributeBytes
helpviewer_keywords:
- IDebugCustomAttribute::GetAttributeBytes
ms.assetid: cf34583b-6530-4dcc-89f8-eb27e4e8d594
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 84d6e807e3be6d0fbdaa94834fbc8cad37f8e4d2
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105088079"
---
# <a name="idebugcustomattributegetattributebytes"></a>IDebugCustomAttribute::GetAttributeBytes
Obtient les informations d’attribut sous la forme d’un objet blob d’octets.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetAttributeBytes( 
   BYTE*  ppBlob,
   DWORD* pdwLen
);
```

```csharp
int GetAttributeBytes(
   ref byte[] ppBlob,
   ref uint   pdwLen
);
```

## <a name="parameters"></a>Paramètres
`ppBlob`\
[in, out] Tableau qui est renseigné avec les octets d’attribut.

`pdwLen`\
[in, out] Spécifie le nombre maximal d’octets à retourner dans le `ppBlob` tableau et retourne le nombre d’octets réellement écrits dans le tableau.

## <a name="return-value"></a>Valeur renvoyée
 En cas de réussite, retourne S_OK ; Sinon, retourne un code d’erreur.

## <a name="remarks"></a>Notes
 Définissez le `ppBlob` paramètre sur une valeur null pour retourner le nombre d’octets d’attributs disponibles. Allouez ensuite un tableau et transmettez ce tableau dans pour le `ppBlob` paramètre.

 Les octets d’attributs représentent les données brutes de l’attribut personnalisé.

## <a name="see-also"></a>Voir aussi
- [IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md)
