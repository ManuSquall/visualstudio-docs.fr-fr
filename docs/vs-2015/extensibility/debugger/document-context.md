---
title: Contexte de document | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], contexts
ms.assetid: 8e8b5702-5c16-4988-953d-69dd807d8b84
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: c5753e2353b351f6aa4bd73c5aced3d4959b3cde
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51741192"
---
# <a name="document-context"></a>Contexte de document
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Dans [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] débogage, un **contexte de document**:  
  
-   Représente une position dans un fichier source. Pour les langues que le fichier source ne soient pas présents, un contexte de document identifie une position dans un document généralement généré par l’environnement d’exécution. Par exemple, un moteur de script peut générer un document à partir du script. Pour plus d’informations, consultez [Position du Document](../../extensibility/debugger/document-position.md).  
  
-   Décrit une position dans un document source qui correspond à un contexte de code. Le Gestionnaire de symboles est mappé à un contexte de code au contexte de la documentation, à l’aide des informations générées par un compilateur ou l’interpréteur.  
  
-   Est implémentée par un [IDebugDocumentContext2](../../extensibility/debugger/reference/idebugdocumentcontext2.md) interface.  
  
## <a name="see-also"></a>Voir aussi  
 [Contexte de code](../../extensibility/debugger/code-context.md)   
 [Fournisseur de symboles](../../extensibility/debugger/symbol-provider.md)   
 [Interfaces de fournisseur de symboles](../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [Contextes du débogueur](../../extensibility/debugger/debugger-contexts.md)

