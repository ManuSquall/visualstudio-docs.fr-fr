---
title: Contexte de document (en anglais) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], contexts
ms.assetid: 8e8b5702-5c16-4988-953d-69dd807d8b84
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 48fe651e69e5e2c97756788cc30e54454c26e51e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738921"
---
# <a name="document-context"></a>Contexte documentaire
Dans [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] le débogage, un *contexte documentaire*:

- Représente une position dans un fichier source. Pour les langues où le fichier source peut ne pas être présent, un contexte de document identifie une position dans un document généralement généré par l’environnement de temps de ruissellement. Par exemple, un moteur de script peut générer un document à partir du script. Pour plus d’informations, voir [position du document](../../extensibility/debugger/document-position.md).

- Décrit une position dans un document source qui correspond à un contexte de code. Le gestionnaire de symboles cartographie un contexte de code au contexte de documentation, à l’aide d’informations générées par un compilateur ou un interprète.

- Est implémenté par une interface [IDebugDocumentContext2.](../../extensibility/debugger/reference/idebugdocumentcontext2.md)

## <a name="see-also"></a>Voir aussi
- [Contexte du code](../../extensibility/debugger/code-context.md)
- [Fournisseur de symboles](../../extensibility/debugger/symbol-provider.md)
- [Interfaces fournisseur de symboles](../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [Contextes Debugger](../../extensibility/debugger/debugger-contexts.md)
