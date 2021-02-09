---
title: 'IDebugCustomAttributeQuery2 :: GetCustomAttributeByName, | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCustomAttributeQuery2::GetCustomAttributeByName
helpviewer_keywords:
- IDebugCustomAttributeQuery2::GetCustomAttributeByName
ms.assetid: 7428dfeb-8929-41b2-9b99-cb343a86c02d
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 8662e3c18f568e60ac98e5468acc3da28966505c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99842444"
---
# <a name="idebugcustomattributequery2getcustomattributebyname"></a>IDebugCustomAttributeQuery2::GetCustomAttributeByName
Obtient les octets d’attributs personnalisés en fonction du nom de l’attribut personnalisé.

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
dans Chaîne contenant le nom de l’attribut personnalisé à rechercher.

`ppBlob`\
[in, out] Tableau qui est renseigné avec les octets d’attributs personnalisés.

`pdwLen`\
[in, out] Spécifie le nombre maximal d’octets à retourner dans le `ppBlob` tableau et retourne le nombre d’octets réellement écrits dans le tableau.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne S_OK ou retourne S_FALSE si l’attribut personnalisé n’existe pas. Sinon, retourne un code d'erreur.

## <a name="remarks"></a>Remarques
 Définissez le `ppBlob` paramètre sur une valeur null pour retourner le nombre d’octets d’attributs disponibles. Allouez ensuite un tableau et transmettez ce tableau dans pour le `ppBlob` paramètre.

 Les octets d’attributs représentent les données brutes de l’attribut personnalisé.

 Si les `ppBlob` `pdwLen` paramètres et sont définis sur une valeur null, cette méthode peut être utilisée pour déterminer si l’attribut personnalisé existe simplement. Toutefois, une alternative plus simple consiste à appeler la méthode [IsCustomAttributeDefined](../../../extensibility/debugger/reference/idebugcustomattributequery2-iscustomattributedefined.md) .

## <a name="see-also"></a>Voir aussi
- [IDebugCustomAttributeQuery2](../../../extensibility/debugger/reference/idebugcustomattributequery2.md)
- [IsCustomAttributeDefined](../../../extensibility/debugger/reference/idebugcustomattributequery2-iscustomattributedefined.md)
