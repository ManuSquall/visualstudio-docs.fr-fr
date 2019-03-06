---
title: TEXT_DOC_ATTR_2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- TEXT_DOC_ATTR_2
helpviewer_keywords:
- TEXT_DOC_ATTR_2 enumeration
ms.assetid: 2333b33b-042b-4ac6-9ebe-e66f95f52f51
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6167c5472f06e016fa45f17fb7cb493224f1668b
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/22/2019
ms.locfileid: "56700612"
---
# <a name="textdocattr2"></a>TEXT_DOC_ATTR_2
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
 TEXT_DOC_ATTR_READONLY_2 indique que le document est en lecture seule.

## <a name="remarks"></a>Notes

> [!NOTE]
>  En fait, cette valeur n’est pas définie dans l’assembly pour c#. Au lieu de cela, vous devez copier la définition de votre fichier source.

 Passé en tant qu’argument à la [onUpdateDocumentAttributes](../../../extensibility/debugger/reference/idebugdocumenttextevents2-onupdatedocumentattributes.md) (méthode).

## <a name="requirements"></a>Spécifications
 En-tête : msdbg.h

 Espace de noms : Microsoft.VisualStudio.Debugger.Interop

 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Énumérations](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [onUpdateDocumentAttributes](../../../extensibility/debugger/reference/idebugdocumenttextevents2-onupdatedocumentattributes.md)