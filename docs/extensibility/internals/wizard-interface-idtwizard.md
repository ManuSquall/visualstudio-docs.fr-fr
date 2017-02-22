---
title: "Interface de l&#39;Assistant (IDTWizard) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Interface IDTWizard"
  - "Assistants, interface"
ms.assetid: 09618d9d-d115-45b6-bccc-de328994b39c
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# Interface de l&#39;Assistant (IDTWizard)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

L'environnement de \(IDE\) développement intégré \(IDE\) utilise l'interface d' <xref:EnvDTE.IDTWizard> de communiquer avec des Assistant.  Les assistants doivent implémenter cette interface pour être installés dans l'IDE.  
  
 La méthode d' <xref:EnvDTE.IDTWizard.Execute%2A> est la seule méthode associée à l'interface d' <xref:EnvDTE.IDTWizard> .  Les assistants implémentent cette méthode et l'IDE appelle la méthode sur l'interface.  L'exemple suivant affiche la signature de la méthode.  
  
```  
/* IDTWizard Method */  
STDMETHOD(Execute)(THIS_  
   /* [in] */ IDispatch *Application,  
   /* [in] */ long hwndOwner,  
   /* [in] */ SAFEARRAY * *ContextParams,  
   /* [in] */ SAFEARRAY * *CustomParams,  
   /* [out] [in] */ wizardResult *RetVal  
   );  
```  
  
 Le mécanisme de début est semblable pour les assistants de **Nouveau projet** et d' **Ajouter un nouvel élément** .  Pour démarrer l'un ou l'autre, vous appelez l'interface d' <xref:EnvDTE.IDTWizard> définie dans Dteinternal.h.  La seule différence est un ensemble de paramètres de contexte et personnalisés qui sont passées à l'interface lorsque l'interface est appelée.  
  
 Les informations suivantes décrivent l'interface d' <xref:EnvDTE.IDTWizard> que les assistants doivent implémenter pour travailler dans [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] l'IDE.  L'IDE appelle la méthode d' <xref:EnvDTE.IDTWizard.Execute%2A> dans l'Assistant, en lui passant les éléments suivants :  
  
-   L'objet DTE  
  
     L'objet DTE est la racine du modèle Automation.  
  
-   Le handle de la boîte de dialogue de fenêtre comme indiqué dans le segment de code, `hwndOwner ([in] long)`.  
  
     L'Assistant utilise cet `hwndOwner` en tant que parent pour la boîte de dialogue Assistant.  
  
-   Les paramètres de contexte sont passés à l'interface comme variant pour SAFEARRAY comme indiqué dans le segment de code, `[in] SAFEARRAY (VARIANT)* ContextParams`.  
  
     Les paramètres de contexte contiennent un tableau de valeurs qui sont spécifiques au type d'Assistant qui est démarré et de l'état actuel du projet.  L'IDE passe les paramètres de contexte à l'Assistant.  Pour plus d'informations, consultez [Paramètres de contexte](../../extensibility/internals/context-parameters.md).  
  
-   Les paramètres personnalisés sont passés à l'interface comme variant pour SAFEARRAY comme indiqué dans le segment de code, `[in] SAFEARRAY (VARIANT)* CustomParams`.  
  
     Les paramètres personnalisés contiennent un tableau de paramètres définis par l'utilisateur.  Un fichier .vsz passe des paramètres personnalisés dans l'IDE.  les valeurs sont déterminées par les instructions d' `Param=` .  Pour plus d'informations, consultez [Paramètres personnalisés](../../extensibility/internals/custom-parameters.md).  
  
-   Les valeurs de retour de l'interface sont  
  
    ```  
    wizardResultSuccess = -1,  
    wizardResultFailure = 0  
    wizardResultCancel = 1  
    wizardResultBackout = 2  
    ```  
  
## Voir aussi  
 [Paramètres de contexte](../../extensibility/internals/context-parameters.md)   
 [Paramètres personnalisés](../../extensibility/internals/custom-parameters.md)   
 [Assistants](../../extensibility/internals/wizards.md)   
 [Assistant \(. Fichier vsz\)](../../extensibility/internals/wizard-dot-vsz-file.md)