---
title: 'IDebugCustomAttribute :: GetAttributeBytes | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCustomAttribute::GetAttributeBytes
helpviewer_keywords:
- IDebugCustomAttribute::GetAttributeBytes
ms.assetid: cf34583b-6530-4dcc-89f8-eb27e4e8d594
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: fe0db0267898b54837cd9d05e39b0ddce97d21cb
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99928457"
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

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne S_OK ; Sinon, retourne un code d’erreur.

## <a name="remarks"></a>Notes
 Définissez le `ppBlob` paramètre sur une valeur null pour retourner le nombre d’octets d’attributs disponibles. Allouez ensuite un tableau et transmettez ce tableau dans pour le `ppBlob` paramètre.

 Les octets d’attributs représentent les données brutes de l’attribut personnalisé.

## <a name="see-also"></a>Voir aussi
- [IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md)
