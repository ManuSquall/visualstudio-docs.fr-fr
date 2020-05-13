---
title: IDebugCustomAttributeQuery2::GetCustomAttributeByName (fr) Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCustomAttributeQuery2::GetCustomAttributeByName
helpviewer_keywords:
- IDebugCustomAttributeQuery2::GetCustomAttributeByName
ms.assetid: 7428dfeb-8929-41b2-9b99-cb343a86c02d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 47471f2743e705b06fb9a1bda6752b24a7836d1b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80732564"
---
# <a name="idebugcustomattributequery2getcustomattributebyname"></a>IDebugCustomAttributeQuery2::GetCustomAttributeByName
Obtient les octets d’attributs personnalisés donnés le nom de l’attribut personnalisé.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetCustomAttributeByName( 
   LPCOLESTR pszCustomAttributeName,
   BYTE*     ppBlob,
   DWORD*    pdwLen
);
```

```csharp
int GetCustomAttributeByName(
   [In] string        pszCustomAttributeName,
   [In, Out] byte[]   ppBlob,
   [In, Out] ref uint pdwLen
);
```

## <a name="parameters"></a>Paramètres
`pszCustomAttributeName`\
[dans] Une chaîne contenant le nom de l’attribut personnalisé à rechercher.

`ppBlob`\
[dans, dehors] Un tableau qui est rempli avec les octets attribut personnalisé.

`pdwLen`\
[dans, dehors] Spécifie le nombre maximum d’octets à revenir dans le `ppBlob` tableau et retourne le nombre d’octets effectivement écrits sur le tableau.

## <a name="return-value"></a>Valeur de retour
 En cas de succès, les retours S_OK ou renvoient S_FALSE si l’attribut personnalisé n’existe pas. Sinon, retourne un code d'erreur.

## <a name="remarks"></a>Notes
 Définissez `ppBlob` le paramètre à une valeur nulle pour retourner le nombre d’octets d’attributs disponibles. Ensuite, allouez un tableau et `ppBlob` passez ce tableau pour le paramètre.

 Les octets d’attribut représentent les données brutes de l’attribut personnalisé.

 Si `ppBlob` les `pdwLen` paramètres et les paramètres sont réglés à une valeur nulle, cette méthode peut être utilisée pour déterminer si l’attribut personnalisé existe simplement. Une alternative plus facile, cependant, est d’appeler la méthode [IsCustomAttributedéfined.](../../../extensibility/debugger/reference/idebugcustomattributequery2-iscustomattributedefined.md)

## <a name="see-also"></a>Voir aussi
- [IDebugCustomAttributeQuery2](../../../extensibility/debugger/reference/idebugcustomattributequery2.md)
- [IsCustomAttributeDefined](../../../extensibility/debugger/reference/idebugcustomattributequery2-iscustomattributedefined.md)
