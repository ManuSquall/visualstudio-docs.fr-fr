---
title: IDebugDocumentHelper (Interface) | Documents Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- IDebugDocumentHelper interface
ms.assetid: b652a31e-b87b-45f1-b586-94f2b6e822db
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: baadcc1e2dba0b07e132298167b9b711e40cd912
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="idebugdocumenthelper-interface"></a>IDebugDocumentHelper, interface
Fournir des implémentations de nombreuses interfaces nécessaires pour l’hébergement actives, telles que la `IDebugDocument`, `IDebugDocumentContext`, `IDebugDocumentProvider`, `IDebugDocumentText`, et `IDebugDocumentTextEvents` interfaces.  
  
 Outre les méthodes héritées de `IUnknown`, le `IDebugDocumentHelper` interface expose les méthodes suivantes.  
  
## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable  
  
|Méthode|Description|  
|------------|-----------------|  
|[IDebugDocumentHelper::Init](../../winscript/reference/idebugdocumenthelper-init.md)|Initialise une application d’assistance du document de débogage avec un nom et les attributs initiaux.|  
|[IDebugDocumentHelper::Attach](../../winscript/reference/idebugdocumenthelper-attach.md)|Ajoute ce document à l’arborescence du document.|  
|[IDebugDocumentHelper::Detach](../../winscript/reference/idebugdocumenthelper-detach.md)|Supprime ce document à partir de l’arborescence du document.|  
|[IDebugDocumentHelper::AddUnicodeText](../../winscript/reference/idebugdocumenthelper-addunicodetext.md)|Ajoute une chaîne Unicode à la fin de ce document.|  
|[IDebugDocumentHelper::AddDBCSText](../../winscript/reference/idebugdocumenthelper-adddbcstext.md)|Ajoute une chaîne DBCS à la fin de ce document.|  
|[IDebugDocumentHelper::SetDebugDocumentHost](../../winscript/reference/idebugdocumenthelper-setdebugdocumenthost.md)|Définit le `IDebugDocumentHost` pour ce document.|  
|[IDebugDocumentHelper::AddDeferredText](../../winscript/reference/idebugdocumenthelper-adddeferredtext.md)|Notifie l’application d’assistance que le texte spécifié est disponible, mais il ne fournit pas les caractères.|  
|[IDebugDocumentHelper::DefineScriptBlock](../../winscript/reference/idebugdocumenthelper-definescriptblock.md)|Indique à l’application d’assistance qui a une plage particulière de caractères est un bloc de script géré par le moteur de script donné.|  
|[IDebugDocumentHelper::SetDefaultTextAttr](../../winscript/reference/idebugdocumenthelper-setdefaulttextattr.md)|Définit les attributs par défaut à utiliser pour le texte qui n’est pas dans un bloc de script.|  
|[IDebugDocumentHelper::SetTextAttributes](../../winscript/reference/idebugdocumenthelper-settextattributes.md)|Définit les attributs sur une plage de texte.|  
|[IDebugDocumentHelper::SetLongName](../../winscript/reference/idebugdocumenthelper-setlongname.md)|Définit le nom long du document.|  
|[IDebugDocumentHelper::SetShortName](../../winscript/reference/idebugdocumenthelper-setshortname.md)|Définit le nom court pour le document.|  
|[IDebugDocumentHelper::SetDocumentAttr](../../winscript/reference/idebugdocumenthelper-setdocumentattr.md)|Définit les attributs de ce document.|  
|[IDebugDocumentHelper::GetDebugApplicationNode](../../winscript/reference/idebugdocumenthelper-getdebugapplicationnode.md)|Retourne le nœud d’application de débogage correspondant à ce document.|  
|[IDebugDocumentHelper::GetScriptBlockInfo](../../winscript/reference/idebugdocumenthelper-getscriptblockinfo.md)|Récupère la plage de caractères et le moteur de script correspondant à un bloc de script.|  
|[IDebugDocumentHelper::CreateDebugDocumentContext](../../winscript/reference/idebugdocumenthelper-createdebugdocumentcontext.md)|Crée un nouveau contexte de document de débogage.|  
|[IDebugDocumentHelper::BringDocumentToTop](../../winscript/reference/idebugdocumenthelper-bringdocumenttotop.md)|Affiche ce document vers le haut dans le débogueur de l’interface utilisateur.|  
|[IDebugDocumentHelper::BringDocumentContextToTop](../../winscript/reference/idebugdocumenthelper-bringdocumentcontexttotop.md)|Met un contexte de ce document vers le haut dans l’interface utilisateur du débogueur.|