---
title: Position du document | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], contexts
ms.assetid: b59d739c-7572-427f-a70d-4e5df63d02c1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 19b88ead19e4578adb7c151a681583120cf2ec17
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80738903"
---
# <a name="document-position"></a>Position du document
Dans [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] le débogage, une *position de document*:

- Fournit une abstraction d’une position dans un fichier source comme connu de l’IDE. Pour la plupart des langues actuelles, une position de document peut être considérée comme une position dans un fichier source.

- Décrit une position dans un document source à un moteur de débogage.

- Est implémenté par une interface [IDebugDocumentPosition2](../../extensibility/debugger/reference/idebugdocumentposition2.md) .

## <a name="see-also"></a>Voir aussi
- [Contexte de code](../../extensibility/debugger/code-context.md)
- [Contexte de document](../../extensibility/debugger/document-context.md)
- [Fournisseur de symboles](../../extensibility/debugger/symbol-provider.md)
- [Interfaces du fournisseur de symboles](../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [Contextes du débogueur](../../extensibility/debugger/debugger-contexts.md)
