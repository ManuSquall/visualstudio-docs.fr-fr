---
title: Position du document | Microsoft Docs
description: Découvrez comment la position d’un document dans le débogage Visual Studio fournit une abstraction d’une position dans un fichier source comme connu de l’IDE.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: fef3debcbce3a178c4321114d69c87c627611a07
ms.sourcegitcommit: 8e9c38da7bcfbe9a461c378083846714933a0e1e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/09/2020
ms.locfileid: "96915321"
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
