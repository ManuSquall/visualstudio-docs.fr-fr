---
title: "Param&#232;tres personnalis&#233;s | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Assistants, paramètres personnalisés"
  - "paramètres personnalisés"
ms.assetid: ba5c364b-66e6-47ea-9760-a0b70de8f0a0
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# Param&#232;tres personnalis&#233;s
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Les paramètres personnalisés contrôlent l'opération d'un Assistant après qu'un Assistant a commencé.  Un fichier relatif .vsz fournit un tableau de paramètres définis par l'utilisateur qui sont empaquetés par l'environnement de développement \(IDE\) intégré \(IDE\) et passés à l'Assistant comme tableau de chaînes lorsque l'Assistant est démarré.  L'Assistant ensuite analyse le tableau de chaînes et utilise les informations pour contrôler l'opération réelle de l'Assistant.  De cette manière, un Assistant peut personnaliser la fonctionnalité selon le contenu du fichier .vsz.  
  
 Les paramètres de contexte, en revanche, affectez à l'état du projet lorsque l'Assistant est démarré.  Pour plus d'informations, consultez [Paramètres de contexte](../../extensibility/internals/context-parameters.md).  
  
 Voici un exemple de fichier .vsz qui dispose des paramètres personnalisés :  
  
```  
VSWIZARD 8.0  
Wizard=VsWizard.VsWizard_Engine  
Param="WIZARD_NAME = Sample Wizard"  
Param="WIZARD_UI = FALSE"  
Param="RELATIVE_PATH = VSWizards\Classwiz\ATL"  
Param="PREPROCESS_FUNCTION = CanAddATLSupport"  
Param="PROJECT_TYPE = CSPROJ"  
```  
  
 L'auteur du fichier .vsz ajoute les valeurs des paramètres.  Lorsqu'un utilisateur sélectionne **Nouveau projet** ou **Ajouter un nouvel élément** dans le menu Fichier ou cliquez avec le bouton droit sur un projet dans **Explorateur de solutions**, l'IDE collecte ces valeurs dans un tableau de chaînes.  L'IDE appelle ensuite la méthode de l' <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.AddItem%2A> du projet avec l'indicateur d' <xref:Microsoft.VisualStudio.Shell.Interop.VSADDITEMOPERATION> , et le projet appelle la méthode d' <xref:EnvDTE.IVsExtensibility.RunWizardFile%2A> chargé d'exécuter l'Assistant et retourner le résultat.  
  
 L'Assistant est chargé d'analyser le tableau de chaînes et d'agir sur les chaînes correctement.  De cette manière, en implémentant des paramètres personnalisés vous pouvez créer un Assistant qui remplit diverses fonctions.  En d'autres termes, un Assistant peut avoir trois fichiers différents .vsz.  Chaque fichier passe différents jeux de paramètres personnalisés pour contrôler le comportement de l'Assistant dans différentes situations.  
  
 Pour plus d'informations, consultez [Assistant \(. Fichier vsz\)](../../extensibility/internals/wizard-dot-vsz-file.md).  
  
## Voir aussi  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3>   
 [Paramètres de contexte](../../extensibility/internals/context-parameters.md)   
 [Assistants](../../extensibility/internals/wizards.md)   
 [Assistant \(. Fichier vsz\)](../../extensibility/internals/wizard-dot-vsz-file.md)