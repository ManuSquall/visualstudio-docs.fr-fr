---
title: Implémentation des interfaces d’assistance d’hôte intelligent | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Smart Host Helper Interfaces, implementing
ms.assetid: b9c44246-4d4d-469e-91be-00c8f5796fa5
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d79d1a4176a10ea236d1ac91084bdcbfd5ca73d1
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/19/2019
ms.locfileid: "58154593"
---
# <a name="implementing-smart-host-helper-interfaces"></a>Implémentation des interfaces d'assistance d'hôte intelligent
[L’interface IDebugDocumentHelper](../winscript/reference/idebugdocumenthelper-interface.md) simplifie considérablement la tâche de création d’un hôte intelligent pour le débogage, car elle fournit des implémentations pour de nombreuses interfaces nécessaires pour l’hébergement intelligent.  
  
 Pour être un hôte intelligent utilisant `IDebugDocumentHelper`, une application hôte doit effectuer uniquement trois actions :  
  
1. `CoCreate` le gestionnaire de débogage de processus et utiliser l’interface [IProcessDebugManager](../winscript/reference/iprocessdebugmanager-interface.md) pour ajouter votre application à la liste des applications pouvant être déboguées.  
  
2. Créer une assistance de document de débogage pour chaque objet de script, à l’aide de la méthode [IProcessDebugManager::CreateDebugDocumentHelper](../winscript/reference/iprocessdebugmanager-createdebugdocumenthelper.md). Vérifiez que le nom du document, le document parent, le texte et les blocs de script sont définis.  
  
3. Implémenter l’interface [IActiveScriptSiteDebug](../winscript/reference/iactivescriptsitedebug-interface.md) sur l’objet qui implémente l’interface [IActiveScriptSite](../winscript/reference/iactivescriptsite.md) (qui est nécessaire pour Active Scripting). La seule méthode non triviale sur l’interface `IActiveScriptSiteDebug` délègue simplement à l’assistance.  
  
   Si vous le souhaitez, l’hôte peut implémenter l’interface [IDebugDocumentHost](../winscript/reference/idebugdocumenthost-interface.md) s’il a besoin de mieux contrôler la couleur de la syntaxe, la création de contexte de document et d’autres fonctionnalités étendues.  
  
   La principale limitation de l’assistance d’hôte intelligent est qu’elle ne peut traiter que les documents dont le contenu change ou diminue après leur ajout (bien que les documents puissent croître). Pour de nombreux hôtes intelligents, toutefois, la fonctionnalité qu’elle fournit est exactement celle qui est nécessaire.  
  
   Les sections suivantes décrivent chaque étape en détail.  
  
## <a name="create-an-application-object"></a>Créer un objet d’application  
 Avant de pouvoir utiliser l’assistance d’hôte intelligent, vous devez créer un objet d’interface [IDebugApplication](../winscript/reference/idebugapplication-interface.md) pour représenter votre application dans le débogueur.  
  
#### <a name="to-create-an-application-object"></a>Pour créer un objet d'application  
  
1.  Créez une instance du gestionnaire de débogage de processus à l’aide de `CoCreateInstance`.  
  
2.  Appelez [IProcessDebugManager::CreateApplication](../winscript/reference/iprocessdebugmanager-createapplication.md).  
  
3.  Définissez le nom de l’application à l’aide de [IDebugApplication::SetName](../winscript/reference/idebugapplication-setname.md).  
  
4.  Ajoutez l’objet d’application à la liste des applications pouvant être déboguées à l’aide de [IProcessDebugManager::AddApplication](../winscript/reference/iprocessdebugmanager-addapplication.md).  
  
     Le code ci-dessous illustre le processus, mais il n’inclut pas de vérification des erreurs ou autres techniques de programmation robuste.  
  
    ```cpp
    CoCreateInstance(CLSID_ProcessDebugManager, NULL,  
          CLSCTX_INPROC_SERVER | CLSCTX_INPROC_HANDLER  
          | CLSCTX_LOCAL_SERVER,  
    IID_IProcessDebugManager, (void **)&g_ppdm);  
    g_ppdm->CreateApplication(&g_pda);  
    g_pda->SetName(L"My cool application");  
    g_ppdm->AddApplication(g_pda, &g_dwAppCookie);  
    ```  
  
## <a name="using-idebugdocumenthelper"></a>Utilisation d’IDebugDocumentHelper  
  
#### <a name="to-use-the-helper-minimal-sequence-of-steps"></a>Pour utiliser l’assistance (séquence d’étapes minimale)  
  
1.  Pour chaque document hôte, créez une assistance à l’aide de [IProcessDebugManager::CreateDebugDocumentHelper](../winscript/reference/iprocessdebugmanager-createdebugdocumenthelper.md).  
  
2.  Appelez [IDebugDocumentHelper::Init](../winscript/reference/idebugdocumenthelper-init.md) sur l’assistance, en donnant le nom, les attributs de document, et ainsi de suite.  
  
3.  Appelez [IDebugDocumentHelper::Attach](../winscript/reference/idebugdocumenthelper-attach.md) avec l’assistance parente pour le document (ou NULL si le document est la racine) afin de définir la position du document dans l’arborescence et le rendre visible par le débogueur.  
  
4.  Appelez [IDebugDocumentHelper::AddDBCSText](../winscript/reference/idebugdocumenthelper-adddbcstext.md) ou [IDebugDocumentHelper::AddUnicodeText](../winscript/reference/idebugdocumenthelper-addunicodetext.md) pour définir le texte du document. (Vous pouvez les appeler plusieurs fois si le document est téléchargé de façon incrémentielle, comme dans le cas d’un navigateur.)  
  
5.  Appelez [IDebugDocumentHelper::DefineScriptBlock](../winscript/reference/idebugdocumenthelper-definescriptblock.md) afin de définir les plages pour chaque bloc de script et les moteurs de script associés.  
  
## <a name="implementing-iactivescriptsitedebug"></a>Implémentation d’IActiveScriptSiteDebug  
 Pour implémenter [IActiveScriptSiteDebug::GetDocumentContextFromPosition](../winscript/reference/iactivescriptsitedebug-getdocumentcontextfromposition.md), obtenez l’assistance correspondant au site en question, puis obtenez l’offset du document de départ pour le contexte source donné, comme suit :  
  
```cpp
pddh->GetScriptBlockInfo(dwSourceContext, NULL, &ulStartPos, NULL);  
```  
  
 Ensuite, utilisez l’assistance pour créer un contexte de document pour l’offset de caractère donné :  
  
```cpp
pddh->CreateDebugDocumentContext(ulStartPos + uCharacterOffset, cChars, &pddcNew);  
```  
  
 Pour implémenter [IActiveScriptSiteDebug::GetRootApplicationNode](../winscript/reference/iactivescriptsitedebug-getrootapplicationnode.md), appelez simplement `IDebugApplication::GetRootNode` (héritée de [IRemoteDebugApplication::GetRootNode](../winscript/reference/iremotedebugapplication-getrootnode.md)).  
  
 Pour implémenter [IDebugDocumentHelper::GetDebugApplicationNode](../winscript/reference/idebugdocumenthelper-getdebugapplicationnode.md), retournez simplement l’objet `IDebugApplication` que vous avez initialement créé à l’aide du gestionnaire de débogage de processus.  
  
## <a name="the-optional-idebugdocumenthost-interface"></a>L’interface IDebugDocumentHost facultative  
 L’hôte peut fournir une implémentation de l’interface [IDebugDocumentHost](../winscript/reference/idebugdocumenthost-interface.md) à l’aide de [IDebugDocumentHelper::SetDebugDocumentHost](../winscript/reference/idebugdocumenthelper-setdebugdocumenthost.md) afin de bénéficier d’un contrôle supplémentaire sur l’assistance. L’interface hôte vous permet entre autres d’effectuer les tâches suivantes :  
  
-   Ajouter du texte à l’aide de [IDebugDocumentHelper::AddDeferredText](../winscript/reference/idebugdocumenthelper-adddeferredtext.md) pour que l’hôte n’ait pas besoin de fournir immédiatement les caractères. Quand ceux-ci sont réellement nécessaires, l’assistance appelle [IDebugDocumentHost::GetDeferredText](../winscript/reference/idebugdocumenthost-getdeferredtext.md) sur l’hôte.  
  
-   Remplacer la coloration syntaxique par défaut fournie par l’assistance. L’assistance appelle [IDebugDocumentHost::GetScriptTextAttributes](../winscript/reference/idebugdocumenthost-getscripttextattributes.md) afin de déterminer la coloration pour une plage de caractères, et utilise son implémentation par défaut si l’hôte retourne `E_NOTIMPL`.  
  
-   Fournir un contrôle inconnu pour les contextes de document créés par l’assistance en implémentant [IDebugDocumentHost::OnCreateDocumentContext](../winscript/reference/idebugdocumenthost-oncreatedocumentcontext.md). Cela permet à l’hôte de substituer la fonctionnalité de l’implémentation de contexte de document par défaut.  
  
-   Fournir un nom de chemin dans le système de fichiers pour le document. Certaines interfaces utilisateur de débogage utilisent cela afin d’autoriser l’utilisateur à modifier et à enregistrer les modifications apportées au document. [IDebugDocumentHost::NotifyChanged](../winscript/reference/idebugdocumenthost-notifychanged.md) est appelée pour avertir l’hôte une fois que le document a été enregistré.  
  
## <a name="see-also"></a>Voir aussi  
 [Présentation du débogage de script actif](../winscript/active-script-debugging-overview.md)