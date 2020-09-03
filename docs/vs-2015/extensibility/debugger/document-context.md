---
title: Contexte du document | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], contexts
ms.assetid: 8e8b5702-5c16-4988-953d-69dd807d8b84
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 3034c9ca02fca8e91eb1aa5e4d0eb5a2fe1f773f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68200584"
---
# <a name="document-context"></a>Contexte de document
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Dans [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] le cadre du débogage, un **contexte de document**:  
  
- Représente une position dans un fichier source. Pour les langages où le fichier source n’est peut-être pas présent, un contexte de document identifie une position dans un document généralement générée par l’environnement d’exécution. Par exemple, un moteur de script peut générer un document à partir d’un script. Pour plus d’informations, consultez [position du document](../../extensibility/debugger/document-position.md).  
  
- Décrit une position dans un document source qui correspond à un contexte de code. Le gestionnaire de symboles mappe un contexte de code au contexte de documentation, à l’aide des informations générées par un compilateur ou un interpréteur.  
  
- Est implémenté par une interface [IDebugDocumentContext2](../../extensibility/debugger/reference/idebugdocumentcontext2.md) .  
  
## <a name="see-also"></a>Voir aussi  
 [Contexte de code](../../extensibility/debugger/code-context.md)   
 [Fournisseur de symboles](../../extensibility/debugger/symbol-provider.md)   
 [Interfaces du fournisseur de symboles](../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [Contextes du débogueur](../../extensibility/debugger/debugger-contexts.md)
