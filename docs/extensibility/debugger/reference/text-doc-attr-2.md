---
title: TEXT_DOC_ATTR_2 Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- TEXT_DOC_ATTR_2
helpviewer_keywords:
- TEXT_DOC_ATTR_2 enumeration
ms.assetid: 2333b33b-042b-4ac6-9ebe-e66f95f52f51
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: afbb7d7f4525050e73dafaed906dbc504cc8b52e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80713458"
---
# <a name="text_doc_attr_2"></a>TEXT_DOC_ATTR_2
Décrit les attributs d’un document.

## <a name="syntax"></a>Syntaxe

```cpp
typedef DWORD TEXT_DOC_ATTR_2;
const TEXT_DOC_ATTR_2 TEXT_DOC_ATTR_READONLY_2 = 0x00000001;
```

```csharp
public const uint TEXT_DOC_ATTR_READONLY_2 = 0x00000001;
```

## <a name="members"></a>Membres
 `TEXT_DOC_ATTR_READONLY_2`\
 Indique que le document est lu uniquement.

## <a name="remarks"></a>Notes

> [!NOTE]
> Cette valeur n’est pas réellement définie dans l’assemblage pour le C. Au lieu de cela, vous devez copier la définition de votre fichier source.

 Passé comme argument à la méthode [onUpdateDocumentAttributes.](../../../extensibility/debugger/reference/idebugdocumenttextevents2-onupdatedocumentattributes.md)

## <a name="requirements"></a>Spécifications
 En-tête: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assemblage: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Énumérations](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [onUpdateDocumentAttributes](../../../extensibility/debugger/reference/idebugdocumenttextevents2-onupdatedocumentattributes.md)
