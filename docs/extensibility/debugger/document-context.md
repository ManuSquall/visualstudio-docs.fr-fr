---
title: Contexte de document | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], contexts
ms.assetid: 8e8b5702-5c16-4988-953d-69dd807d8b84
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 8ed5498961a575d0f9d3f7c64b46bc73a2d510b5
ms.lasthandoff: 02/22/2017

---
# <a name="document-context"></a>Contexte de document
Dans [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] débogage, un **contexte de document**:  
  
-   Représente une position dans un fichier source. Pour les langues où le fichier source ne peut pas être présent, un contexte de document identifie une position dans un document habituellement générée par l’environnement d’exécution. Par exemple, un moteur de script peut générer un document à partir du script. Pour plus d’informations, consultez [Document Position](../../extensibility/debugger/document-position.md).  
  
-   Décrit une position dans un document source qui correspond à un contexte de code. Le Gestionnaire de symboles est mappé à un contexte de code au contexte de la documentation, à l’aide des informations générées par un compilateur ou l’interpréteur.  
  
-   Est implémentée par un [IDebugDocumentContext2](../../extensibility/debugger/reference/idebugdocumentcontext2.md) interface.  
  
## <a name="see-also"></a>Voir aussi  
 [Contexte de code](../../extensibility/debugger/code-context.md)   
 [Fournisseur de symboles](../../extensibility/debugger/symbol-provider.md)   
 [Interfaces de fournisseur de symboles](../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [Contextes de débogueur](../../extensibility/debugger/debugger-contexts.md)
