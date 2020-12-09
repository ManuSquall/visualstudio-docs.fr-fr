---
title: Contexte du document | Microsoft Docs
description: En savoir plus sur le contexte de document dans le débogage Visual Studio, qui représente une position dans un fichier source ou une position dans un document source pour un contexte de code.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 5d19830346ea09731dde608e019109f61011cd60
ms.sourcegitcommit: 8e9c38da7bcfbe9a461c378083846714933a0e1e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/09/2020
ms.locfileid: "96915529"
---
# <a name="document-context"></a>Contexte de document
Dans [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] le cadre du débogage, un *contexte de document*:

- Représente une position dans un fichier source. Pour les langages où le fichier source n’est peut-être pas présent, un contexte de document identifie une position dans un document généralement générée par l’environnement d’exécution. Par exemple, un moteur de script peut générer un document à partir d’un script. Pour plus d’informations, consultez [position du document](../../extensibility/debugger/document-position.md).

- Décrit une position dans un document source qui correspond à un contexte de code. Le gestionnaire de symboles mappe un contexte de code au contexte de documentation, à l’aide des informations générées par un compilateur ou un interpréteur.

- Est implémenté par une interface [IDebugDocumentContext2](../../extensibility/debugger/reference/idebugdocumentcontext2.md) .

## <a name="see-also"></a>Voir aussi
- [Contexte de code](../../extensibility/debugger/code-context.md)
- [Fournisseur de symboles](../../extensibility/debugger/symbol-provider.md)
- [Interfaces du fournisseur de symboles](../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [Contextes du débogueur](../../extensibility/debugger/debugger-contexts.md)
