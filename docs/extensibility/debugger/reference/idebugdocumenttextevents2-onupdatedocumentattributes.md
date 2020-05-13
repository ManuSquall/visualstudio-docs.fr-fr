---
title: IDebugDocumentTextEvents2::onUpdateDocumentAttributes (en anglais seulement) Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocumentTextEvents2::OnUpdateDocumentAttributes
helpviewer_keywords:
- IDebugDocumentTextEvents2::onUpdateDocumentAttributes
ms.assetid: 31b7d151-9ce2-438e-b405-f8cc46b9f537
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: c5ed964905db6aa591252018b408cf67fa43d310
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80731396"
---
# <a name="idebugdocumenttextevents2onupdatedocumentattributes"></a>IDebugDocumentTextEvents2::onUpdateDocumentAttributes
Informe le destinataire de l’événement que les attributs du document ont été mis à jour.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT onUpdateDocumentAttributes( 
   TEXT_DOC_ATTR_2 textdocattr
);
```

```csharp
int onUpdateDocumentAttributes( 
   enum_TEXT_DOC_ATTR_2 textdocattr
);
```

## <a name="parameters"></a>Paramètres
`textdocattr`\
[dans] Une combinaison de drapeaux de [l’TEXT_DOC_ATTR_2](../../../extensibility/debugger/reference/text-doc-attr-2.md) énumération qui spécifie les attributs mis à jour du document.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.

## <a name="see-also"></a>Voir aussi
- [IDebugDocumentTextEvents2](../../../extensibility/debugger/reference/idebugdocumenttextevents2.md)
- [TEXT_DOC_ATTR_2](../../../extensibility/debugger/reference/text-doc-attr-2.md)
