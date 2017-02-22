---
title: "Modification des param&#232;tres d&#39;affichage &#224; l&#39;aide de l&#39;API h&#233;rit&#233;e | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "éditeurs (Visual Studio SDK), hérités - modifier les paramètres d'affichage"
ms.assetid: 12c9b300-0894-4124-96a1-764326176d77
caps.latest.revision: 18
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 18
---
# Modification des param&#232;tres d&#39;affichage &#224; l&#39;aide de l&#39;API h&#233;rit&#233;e
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Les paramètres de l'éditeur principal fonctionnalité, telle que le retour automatique à la ligne, la marge de sélection, et l'espace virtuel, peut être modifié par l'utilisateur au moyen de la boîte de dialogue d' **Options** .  Toutefois, il est également possible de modifier ces paramètres par programmation.  
  
## Modifier les paramètres à l'aide de l'API héritée  
 L'interface d' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyCategoryContainer> expose un jeu de propriétés de l'éditeur de texte.  L'affichage de texte contient une catégorie de propriétés \(GUID\_EditPropCategory\_View\_MasterSettings\) qui représente le groupe de paramètres modifiés par programme pour l'affichage de texte.  Une fois que les ajustements d'affichage ont été modifiés de cette façon, ils ne peuvent pas être modifiés dans la boîte de dialogue d' **Options** jusqu'à ce qu'ils sont réinitialisés.  
  
 Voici le processus habituel pour modifier les ajustements d'affichage pour une instance du éditeur principal.  
  
1.  appelez `QueryInterface` sur \(<xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView>\) pour l'interface d' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyCategoryContainer> .  
  
2.  Appelez la méthode d' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyCategoryContainer.GetPropertyCategory%2A> , en spécifiant une valeur de GUID\_EditPropCategory\_View\_MasterSettings pour le paramètre d' `rguidCategory` .  
  
     De cette façon retourne un pointeur vers l'interface d' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyCategoryContainer> , qui contient l'ensemble de propriétés de liaison pour la vue.  Tous les paramètres à ce groupe sont définitivement convertis.  Si un paramètre n'est pas à ce groupe, il effectue les options spécifiées dans la boîte de dialogue d' **Options** ou les ordres de l'utilisateur.  
  
3.  Appelez la méthode d' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyContainer.SetProperty%2A> , en spécifiant la valeur appropriée de paramètres dans le paramètre d' `idprop` .  
  
     par exemple, pour forcer le retour automatique à la ligne, l' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyContainer.SetProperty%2A> d'appel et spécifier une valeur de VSEDITPROPID\_ViewLangOpt\_WordWrap, `vt` pour le paramètre d' `idprop` .  Dans cet appel, `vt` est a VARIANT du type VT\_BOOL et `vt.boolVal` est VARIANT\_TRUE.  
  
## Réinitialiser les ajustements d'affichage modifiés  
 Pour réinitialiser tout ajustement d'affichage modifié pour une instance du éditeur principal, appeler la méthode d' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyContainer.RemoveProperty%2A> et spécifier la valeur appropriée de paramètre dans le paramètre d' `idprop` .  
  
 par exemple, pour permettre au retour automatique à la ligne pour flotter librement, vous le supprimeriez de la catégorie de propriété <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyContainer.RemoveProperty%2A> appelant et en spécifiant une valeur de VSEDITPROPID\_ViewLangOpt\_WordWrap pour le paramètre d' `idprop` .  
  
 Pour supprimer tous les paramètres modifiés pour l'éditeur principal immédiatement, spécifiez une valeur de VSEDITPROPID\_ViewComposite\_AllCodeWindowDefaults, VT pour le paramètre d' `idprop` .  Dans cet appel, le VT est a VARIANT du type VT\_BOOL et vt.boolVal est VARIANT\_TRUE.  
  
## Voir aussi  
 [Dans l'éditeur de base](../extensibility/inside-the-core-editor.md)   
 [L'accès à theText vue à l'aide de l'API héritée](../extensibility/accessing-thetext-view-by-using-the-legacy-api.md)   
 [Options, boîte de dialogue](../ide/reference/options-dialog-box-visual-studio.md)