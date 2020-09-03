---
title: Modification des paramètres d’affichage à l’aide de l’API héritée | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - changing view settings
ms.assetid: 12c9b300-0894-4124-96a1-764326176d77
caps.latest.revision: 19
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a7d58d1477b9d7f58242f8cb4db7c3c360c248b9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68184467"
---
# <a name="changing-view-settings-by-using-the-legacy-api"></a>Modification des paramètres d’affichage à l’aide de l’API héritée
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Les paramètres des fonctionnalités principales de l’éditeur, tels que le retour automatique à la ligne, la marge de sélection et l’espace virtuel, peuvent être modifiés par l’utilisateur au moyen de la boîte de dialogue **options** . Toutefois, il est également possible de modifier ces paramètres par programmation.  
  
## <a name="changing-settings-by-using-the-legacy-api"></a>Modification des paramètres à l’aide de l’API héritée  
 L' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyCategoryContainer> interface expose un ensemble de propriétés d’éditeur de texte. L’affichage de texte contient une catégorie de propriétés (GUID_EditPropCategory_View_MasterSettings) qui représente le groupe de paramètres modifiés par programme pour l’affichage de texte. Une fois que les paramètres d’affichage ont été modifiés de cette manière, ils ne peuvent pas être modifiés dans la boîte de dialogue **options** tant qu’ils ne sont pas réinitialisés.  
  
 Voici le processus classique permettant de modifier les paramètres d’affichage d’une instance de l’éditeur principal.  
  
1. Appelez `QueryInterface` sur ( <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView> ) pour l' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyCategoryContainer> interface.  
  
2. Appelez la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyCategoryContainer.GetPropertyCategory%2A> méthode en spécifiant une valeur de GUID_EditPropCategory_View_MasterSettings pour le `rguidCategory` paramètre.  
  
     Cela retourne un pointeur vers l' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyCategoryContainer> interface, qui contient le jeu de propriétés forcées pour la vue. Tous les paramètres de ce groupe sont définitivement forcés. Si un paramètre n’est pas dans ce groupe, il suit les options spécifiées dans la boîte de dialogue **options** ou dans les commandes de l’utilisateur.  
  
3. Appelez la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyContainer.SetProperty%2A> méthode en spécifiant la valeur de paramètres appropriée dans le `idprop` paramètre.  
  
     Par exemple, pour forcer le retour automatique à la ligne, appelez <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyContainer.SetProperty%2A> et spécifiez une valeur de VSEDITPROPID_ViewLangOpt_WordWrap `vt` pour le `idprop` paramètre. Dans cet appel, `vt` est un variant de type VT_BOOL et `vt.boolVal` est VARIANT_TRUE.  
  
## <a name="resetting-changed-view-settings"></a>Réinitialisation des paramètres d’affichage modifiés  
 Pour réinitialiser les paramètres de vue modifiés pour une instance de l’éditeur principal, appelez la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyContainer.RemoveProperty%2A> méthode et spécifiez la valeur de paramètre appropriée dans le `idprop` paramètre.  
  
 Par exemple, pour autoriser le retour automatique à la ligne à virgule flottante, vous devez le supprimer de la catégorie de propriété en appelant <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyContainer.RemoveProperty%2A> et en spécifiant la valeur VSEDITPROPID_ViewLangOpt_WordWrap pour le `idprop` paramètre.  
  
 Pour supprimer simultanément tous les paramètres modifiés pour l’éditeur principal, spécifiez la valeur VSEDITPROPID_ViewComposite_AllCodeWindowDefaults, VT pour le `idprop` paramètre. Dans cet appel, VT est une variante de type VT_BOOL et VT. boolVal est VARIANT_TRUE.  
  
## <a name="see-also"></a>Voir aussi  
 [Dans l’éditeur de base](../extensibility/inside-the-core-editor.md)   
 [Accès à la vue theText à l’aide de l’API héritée](../extensibility/accessing-thetext-view-by-using-the-legacy-api.md)   
 [Options, boîte de dialogue](../ide/reference/options-dialog-box-visual-studio.md)
