---
title: IDebugDocumentContext Interface | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugDocumentContext interface
ms.assetid: 665ee08a-5c6a-4ab1-ab93-de376acc9a74
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: df4c8b8639a6d4b232f82cf87fff7b069829cc46
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62783192"
---
# <a name="idebugdocumentcontext-interface"></a>IDebugDocumentContext, interface
Fournit une représentation abstraite d’une partie du document en cours de débogage. Pour les documents de texte, cette représentation se compose d’une plage de la position de caractère.  
  
 Outre les méthodes héritées de `IUnknown`, le `IDebugDocumentContext` interface expose les méthodes suivantes.  
  
## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable  
  
|Méthode|Description|  
|------------|-----------------|  
|[IDebugDocumentContext::GetDocument](../../winscript/reference/idebugdocumentcontext-getdocument.md)|Retourne le document qui contient ce contexte.|  
|[IDebugDocumentContext::EnumCodeContexts](../../winscript/reference/idebugdocumentcontext-enumcodecontexts.md)|Énumère les contextes de code associés à ce contexte de document.|