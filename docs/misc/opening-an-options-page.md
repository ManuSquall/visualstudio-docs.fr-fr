---
title: "Ouverture d’une page d’options | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "ouvrir une page d’options"
  - "options outils"
  - "page d’options"
ms.assetid: 6f24cbfa-288a-4a57-831b-bc82587de255
caps.latest.revision: 9
caps.handback.revision: 9
manager: "douge"
---
# Ouverture d’une page d’options
Vous pouvez afficher une page d’options par programmation pour que les utilisateurs de votre package puissent le configurer pendant l’installation. Un utilisateur peut toujours accéder à la page d’options à l’aide de la boîte de dialogue **Options** pour modifier les paramètres une fois le package installé.  
  
### Pour afficher une page d’options personnalisée  
  
1.  Créez une page d’options. Pour plus d'informations, consultez [Création de Pages d'Options](../extensibility/internals/creating-options-pages.md).  
  
2.  Obtenez le <xref:System.Type> de la page d’options en appliquant le mot clé `typeof` au nom de la classe qui définit la page d’options.  
  
3.  Appelez la méthode <xref:Microsoft.VisualStudio.Shell.Package.ShowOptionPage%2A> à l’aide du <xref:System.Type> de la page d’options en tant que paramètre.  
  
     L’exemple suivant affiche une page d’options nommée **HelloWorldOptions**.  
  
     [!code-cs[UI_UserSettings_ToolsOptionPages#5](../misc/codesnippet/CSharp/opening-an-options-page_1.cs)]
     [!code-vb[UI_UserSettings_ToolsOptionPages#5](../misc/codesnippet/VisualBasic/opening-an-options-page_1.vb)]  
  
### Pour afficher une page d’options définie par Visual Studio  
  
1.  Dans la sous\-clé de Registre HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\VisualStudio\\9.0\\ToolsOptionsPages\\, recherchez le nœud de la page d’options que vous voulez afficher, puis copiez son GUID, qui est la valeur de la clé de page.  
  
2.  Créez une instance <xref:System.ComponentModel.Design.CommandID> qui accepte les constantes <xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97> et <xref:Microsoft.VisualStudio.VSConstants.VSStd97CmdID> en tant que paramètres.  
  
     Cette opération spécifie la boîte de dialogue **Options**.  
  
3.  Appelez la méthode <xref:System.ComponentModel.Design.MenuCommandService.GlobalInvoke%2A> à l’aide de l’instance <xref:System.ComponentModel.Design.CommandID> et de la chaîne du GUID en tant que paramètres.  
  
     L’exemple suivant affiche l’onglet **Général** de la page d’options de l’**Éditeur de texte**.  
  
     [!code-cs[UI_UserSettings_ToolsOptionPages#6](../misc/codesnippet/CSharp/opening-an-options-page_2.cs)]
     [!code-vb[UI_UserSettings_ToolsOptionPages#6](../misc/codesnippet/VisualBasic/opening-an-options-page_2.vb)]