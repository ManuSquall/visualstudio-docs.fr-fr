---
title: Contexte de document | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], contexts
ms.assetid: 8e8b5702-5c16-4988-953d-69dd807d8b84
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: ef82c6533eddf32dd8315193531a57e2e7328ad9
ms.sourcegitcommit: 36835f1b3ec004829d6aedf01938494465587436
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/23/2018
ms.locfileid: "39203558"
---
# <a name="document-context"></a>Contexte de document
Dans [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] débogage, un *contexte de document*:  
  
-   Représente une position dans un fichier source. Pour les langues que le fichier source ne soient pas présents, un contexte de document identifie une position dans un document généralement généré par l’environnement d’exécution. Par exemple, un moteur de script peut générer un document à partir du script. Pour plus d’informations, consultez [Document position](../../extensibility/debugger/document-position.md).  
  
-   Décrit une position dans un document source qui correspond à un contexte de code. Le Gestionnaire de symboles est mappé à un contexte de code au contexte de la documentation, à l’aide des informations générées par un compilateur ou l’interpréteur.  
  
-   Est implémentée par un [IDebugDocumentContext2](../../extensibility/debugger/reference/idebugdocumentcontext2.md) interface.  
  
## <a name="see-also"></a>Voir aussi  
 [Contexte de code](../../extensibility/debugger/code-context.md)   
 [Fournisseur de symboles](../../extensibility/debugger/symbol-provider.md)   
 [Interfaces de fournisseur de symboles](../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [Contextes du débogueur](../../extensibility/debugger/debugger-contexts.md)