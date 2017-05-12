---
title: "Impl&#233;mentation des interfaces d&#39;assistance d&#39;h&#244;te intelligent | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Assistance d'hôte intelligent (interfaces), implémenter"
ms.assetid: b9c44246-4d4d-469e-91be-00c8f5796fa5
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# Impl&#233;mentation des interfaces d&#39;assistance d&#39;h&#244;te intelligent
L'interface d' [IDebugDocumentHelper, interface](../winscript/reference/idebugdocumenthelper-interface.md) simplifie considérablement la tâche de création d'un hôte intelligent pour le débogage active, car elle fournit des implémentations pour de nombreuses interfaces nécessaires pour l'hébergement intelligent.  
  
 Pour être un intelligent hôte à l'aide de `IDebugDocumentHelper`, une application hôte doit effectuer uniquement trois choses :  
  
1.  `CoCreate` Process Debug Manager, puis utilisez l'interface d' [IProcessDebugManager, interface](../winscript/reference/iprocessdebugmanager-interface.md) pour ajouter votre application à la liste des applications débogable.  
  
2.  Créez un programme d'assistance de document de débogage pour chaque objet de script, à l'aide de la méthode d' [IProcessDebugManager::CreateDebugDocumentHelper](../winscript/reference/iprocessdebugmanager-createdebugdocumenthelper.md) .  Assurez\-vous que le nom de document, le document parent, le texte, et les blocs de script sont définis.  
  
3.  Implémentez l'interface d' [IActiveScriptSiteDebug, interface](../winscript/reference/iactivescriptsitedebug-interface.md) sur votre objet qui implémente l'interface d' [IActiveScriptSite](../winscript/reference/iactivescriptsite.md) \(qui est nécessaire pour l'Active Scripting\).  La seule méthode non triviale sur les délégués d'interface d' `IActiveScriptSiteDebug` simplement au programme d'assistance.  
  
 Éventuellement, l'hôte peut implémenter l'interface d' [IDebugDocumentHost, interface](../winscript/reference/idebugdocumenthost-interface.md) s'il a besoin du contrôle supplémentaire de la couleur de syntaxe, de la création du contexte de document, et de toute autre fonctionnalité étendue.  
  
 La limitation principale du programme d'assistance intelligent hôte est qu'elle ne peut traiter les documents dont le contenu est modifié ou réduction après qu'ils ont été ajoutés \(bien que les documents peuvent développer\).  Pour de nombreux hôtes intelligents, toutefois, les fonctionnalités qu'elle fournit est exactement ce qui est nécessaire.  
  
 Les sections suivantes décrivent chaque étape plus en détail.  
  
## Créez un objet Application  
 Avant que le programme d'assistance intelligent hôte puisse être utilisé, il est nécessaire de créer un objet d' [IDebugApplication, interface](../winscript/reference/idebugapplication-interface.md) pour représenter votre application dans le débogueur.  
  
#### Pour créer un objet application  
  
1.  Créez une instance du processus de débogage le gestionnaire de `CoCreateInstance`.  
  
2.  Appelez [IProcessDebugManager::CreateApplication](../winscript/reference/iprocessdebugmanager-createapplication.md).  
  
3.  Définissez le nom de l'application à l'aide de [IDebugApplication::SetName](../winscript/reference/idebugapplication-setname.md).  
  
4.  Ajoutez l'objet application à la liste des applications débogable à l'aide de [IProcessDebugManager::AddApplication](../winscript/reference/iprocessdebugmanager-addapplication.md).  
  
     Le code ci\-dessous des contours le processus, mais elle n'inclut pas la vérification des erreurs ou d'autres techniques de programmation fiables.  
  
    ```  
    CoCreateInstance(CLSID_ProcessDebugManager, NULL,  
          CLSCTX_INPROC_SERVER | CLSCTX_INPROC_HANDLER  
          | CLSCTX_LOCAL_SERVER,  
    IID_IProcessDebugManager, (void **)&g_ppdm);  
    g_ppdm->CreateApplication(&g_pda);  
    g_pda->SetName(L"My cool application");  
    g_ppdm->AddApplication(g_pda, &g_dwAppCookie);  
    ```  
  
## Utilisation IDebugDocumentHelper  
  
#### Pour utiliser le d'assistance \(minimale séquence d'étapes\)  
  
1.  Pour chaque document hôte, créez un programme d'assistance à l'aide de [IProcessDebugManager::CreateDebugDocumentHelper](../winscript/reference/iprocessdebugmanager-createdebugdocumenthelper.md).  
  
2.  Appelez [IDebugDocumentHelper::Init](../winscript/reference/idebugdocumenthelper-init.md) dans le d'assistance, en fournissant le nom, les attributs de document, et ainsi de suite.  
  
3.  Appelez [IDebugDocumentHelper::Attach](../winscript/reference/idebugdocumenthelper-attach.md) avec le programme d'assistance parent pour le document \(NULL ou si le document est la racine\) pour définir la position du document dans l'arborescence et pour le rendre visible au débogueur.  
  
4.  Appelez [IDebugDocumentHelper::AddDBCSText](../winscript/reference/idebugdocumenthelper-adddbcstext.md) ou [IDebugDocumentHelper::AddUnicodeText](../winscript/reference/idebugdocumenthelper-addunicodetext.md) pour définir le texte du document.  \(Ils peuvent être appelés plusieurs fois que le document est téléchargé de façon incrémentielle, comme dans le cas d'un navigateur.\)  
  
5.  Appelez [IDebugDocumentHelper::DefineScriptBlock](../winscript/reference/idebugdocumenthelper-definescriptblock.md) pour définir les intervalles pour chaque bloc de script et les moteurs de script associés.  
  
## Implémenter IActiveScriptSiteDebug  
 Pour implémenter [IActiveScriptSiteDebug::GetDocumentContextFromPosition](../winscript/reference/iactivescriptsitedebug-getdocumentcontextfromposition.md), obligez le programme d'assistance correspondant au site donné, puis récupérez le document décalé à partir de le contexte donné de source, comme suit :  
  
```  
pddh->GetScriptBlockInfo(dwSourceContext, NULL, &ulStartPos, NULL);  
```  
  
 Ensuite, utilisez le programme d'assistance pour créer un nouveau contexte de le document pour le caractère décalage donné :  
  
```  
pddh->CreateDebugDocumentContext(ulStartPos + uCharacterOffset, cChars, &pddcNew);  
```  
  
 Pour implémenter [IActiveScriptSiteDebug::GetRootApplicationNode](../winscript/reference/iactivescriptsitedebug-getrootapplicationnode.md), appelez simplement `IDebugApplication::GetRootNode` \(hérité d' [IRemoteDebugApplication::GetRootNode](../winscript/reference/iremotedebugapplication-getrootnode.md)\).  
  
 Pour implémenter [IDebugDocumentHelper::GetDebugApplicationNode](../winscript/reference/idebugdocumenthelper-getdebugapplicationnode.md), retournez simplement `IDebugApplication` que vous avez initialement créé à l'aide de le processus de débogage le gestionnaire.  
  
## l'interface facultative d'IDebugDocumentHost  
 L'hôte peut fournir une implémentation d' [IDebugDocumentHost, interface](../winscript/reference/idebugdocumenthost-interface.md) à l'aide de [IDebugDocumentHelper::SetDebugDocumentHost](../winscript/reference/idebugdocumenthelper-setdebugdocumenthost.md) pour lui donner le contrôle supplémentaire du programme d'assistance.  Voici quelques\-unes des opérations principales que l'interface hôte vous permet de faire :  
  
-   Ajoutez du texte à l'aide [IDebugDocumentHelper::AddDeferredText](../winscript/reference/idebugdocumenthelper-adddeferredtext.md) afin que l'hôte n'a pas besoin de fournir les caractères réels immédiatement.  Lorsque des caractères sont réellement nécessaires, le programme d'assistance appellera [IDebugDocumentHost::GetDeferredText](../winscript/reference/idebugdocumenthost-getdeferredtext.md) sur l'hôte.  
  
-   Substituez la coloration de syntaxe par défaut fournie par le programme d'assistance.  Le programme d'assistance appelle [IDebugDocumentHost::GetScriptTextAttributes](../winscript/reference/idebugdocumenthost-getscripttextattributes.md) pour déterminer la coloration pour une plage de caractères, chute arrière sur son implémentation par défaut pour héberger `E_NOTIMPL`de retour.  
  
-   Fournissez un inconnu de contrôle pour les contextes de le document créés par le programme d'assistance en implémentant [IDebugDocumentHost::OnCreateDocumentContext](../winscript/reference/idebugdocumenthost-oncreatedocumentcontext.md).  Cela permet à l'hôte pour remplacer la fonctionnalité de l'implémentation de contexte de document par défaut.  
  
-   Fournissez un nom de chemin d'accès dans le système de fichiers pour le document.  Le débogage interface utilisateur utilisent cette opération pour permettre à l'utilisateur de modifier et enregistrer les modifications dans le document.  [IDebugDocumentHost::NotifyChanged](../winscript/reference/idebugdocumenthost-notifychanged.md) est appelé pour informer l'hôte après que le document a été enregistré.  
  
## Voir aussi  
 [Débogage de script actif, présentation](../winscript/active-script-debugging-overview.md)