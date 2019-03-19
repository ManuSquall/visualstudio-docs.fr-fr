---
title: IDebugDocumentHost Interface | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugDocumentHost interface
ms.assetid: 2fed4220-b6a2-47c6-bf28-daad7dd5c42d
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 226e2700b471cd34496682d233e57946e124ff3b
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/19/2019
ms.locfileid: "58155665"
---
# <a name="idebugdocumenthost-interface"></a>IDebugDocumentHost, interface
Expose les fonctionnalités spécifiques à l’hôte, telles que la coloration syntaxique, au débogueur. Le `IDebugDocumentHelper::SetDebugDocumentHost` méthode utilise cette interface en tant qu’argument.  
  
 Outre les méthodes héritées de `IUnknown`, le `IDebugDocumentHost` interface expose les méthodes suivantes.  
  
## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable  
  
|Méthode|Description|  
|------------|-----------------|  
|[IDebugDocumentHost::GetDeferredText](../../winscript/reference/idebugdocumenthost-getdeferredtext.md)|Retourne une plage de caractères qui ont été ajoutés à l’aide de `IDebugDocumentHelper::AddDeferredText`, dans le document d’hôte d’origine.|  
|[IDebugDocumentHost::GetScriptTextAttributes](../../winscript/reference/idebugdocumenthost-getscripttextattributes.md)|Retourne les attributs de texte pour un bloc de texte du document.|  
|[IDebugDocumentHost::OnCreateDocumentContext](../../winscript/reference/idebugdocumenthost-oncreatedocumentcontext.md)|Avertit l’hôte qu’un nouveau contexte de document est créé et permet à l’hôte pour éventuellement retourner un objet qui contrôle le nouveau contexte.|  
|[IDebugDocumentHost::GetPathName](../../winscript/reference/idebugdocumenthost-getpathname.md)|Retourne le chemin d’accès complet (y compris le nom de fichier) du fichier de source du document.|  
|[IDebugDocumentHost::GetFileName](../../winscript/reference/idebugdocumenthost-getfilename.md)|Retourne le nom du document, sans informations de chemin d’accès.|  
|[IDebugDocumentHost::NotifyChanged](../../winscript/reference/idebugdocumenthost-notifychanged.md)|Avertit l’hôte que le fichier du document source a été enregistré et que son contenu doit être actualisé.|