---
title: Contexte de document | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], contexts
ms.assetid: 8e8b5702-5c16-4988-953d-69dd807d8b84
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d15e53d29adc04a82274ebd456027d15b0e41703
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66345713"
---
# <a name="document-context"></a>Contexte de document
Dans [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] débogage, un *contexte de document*:

- Représente une position dans un fichier source. Pour les langues que le fichier source ne soient pas présents, un contexte de document identifie une position dans un document généralement généré par l’environnement d’exécution. Par exemple, un moteur de script peut générer un document à partir du script. Pour plus d’informations, consultez [Document position](../../extensibility/debugger/document-position.md).

- Décrit une position dans un document source qui correspond à un contexte de code. Le Gestionnaire de symboles est mappé à un contexte de code au contexte de la documentation, à l’aide des informations générées par un compilateur ou l’interpréteur.

- Est implémentée par un [IDebugDocumentContext2](../../extensibility/debugger/reference/idebugdocumentcontext2.md) interface.

## <a name="see-also"></a>Voir aussi
- [Contexte de code](../../extensibility/debugger/code-context.md)
- [Fournisseur de symboles](../../extensibility/debugger/symbol-provider.md)
- [Interfaces de fournisseur de symboles](../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [Contextes du débogueur](../../extensibility/debugger/debugger-contexts.md)