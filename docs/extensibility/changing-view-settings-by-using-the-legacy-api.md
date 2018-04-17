---
title: Modification des paramètres de la vue à l’aide de l’API héritée | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - changing view settings
ms.assetid: 12c9b300-0894-4124-96a1-764326176d77
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 9857daab890c2dd7bf7a799b6dca4d1b74cb9e37
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="changing-view-settings-by-using-the-legacy-api"></a>Modification des paramètres de la vue à l’aide de l’API héritée
Paramètres pour les fonctionnalités de l’éditeur de base, telles que le retour automatique à la marge de sélection et l’espace virtuel, peuvent être modifiés par l’utilisateur à l’aide de la **Options** boîte de dialogue. Toutefois, il est également possible de modifier ces paramètres par programmation.  
  
## <a name="changing-settings-by-using-the-legacy-api"></a>Modification des paramètres à l’aide de l’API héritée  
 Le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyCategoryContainer> interface expose un ensemble de propriétés de l’éditeur de texte. L’affichage de texte contient une catégorie de propriétés (GUID_EditPropCategory_View_MasterSettings) qui représente le groupe de paramètres modifiés par programme pour l’affichage de texte. Une fois que les paramètres d’affichage ont été modifiés de cette manière, ils ne peuvent pas être modifiés dans le **Options** boîte de dialogue jusqu'à ce qu’elles sont réinitialisées.  
  
 Voici le processus classique permettant de modifier les paramètres d’affichage d’une instance de l’éditeur principal.  
  
1.  Appelez `QueryInterface` sur le (<xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView>) pour le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyCategoryContainer> interface.  
  
2.  Appelez le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyCategoryContainer.GetPropertyCategory%2A> méthode, en spécifiant une valeur de GUID_EditPropCategory_View_MasterSettings pour la `rguidCategory` paramètre.  
  
     Cette opération retourne un pointeur vers le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyCategoryContainer> interface, qui contient le jeu de propriétés forcés pour la vue. Tous les paramètres de ce groupe sont définitivement forcés. Si un paramètre n’est pas dans ce groupe, puis il suit les options spécifiées dans le **Options** boîte de dialogue ou les commandes de l’utilisateur.  
  
3.  Appelez le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyContainer.SetProperty%2A> méthode, en spécifiant la valeur de paramètres appropriés dans le `idprop` paramètre.  
  
     Par exemple, pour forcer le retour automatique à, appelez <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyContainer.SetProperty%2A> et spécifiez une valeur de VSEDITPROPID_ViewLangOpt_WordWrap, `vt` pour la `idprop` paramètre. Dans cet appel, `vt` est une variante de type VT_BOOL et `vt.boolVal` a la valeur VARIANT_TRUE.  
  
## <a name="resetting-changed-view-settings"></a>La réinitialisation des paramètres d’affichage modifié  
 Pour rétablir n’importe quelle vue modifiée définition d’une instance de l’éditeur principal, appelez le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyContainer.RemoveProperty%2A> (méthode) et spécifiez la valeur du paramètre approprié dans le `idprop` paramètre.  
  
 Par exemple, pour permettre le retour automatique à faire flotter librement, vous serez supprimer à partir de la catégorie de propriété en appelant <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyContainer.RemoveProperty%2A> et en spécifiant une valeur de VSEDITPROPID_ViewLangOpt_WordWrap pour la `idprop` paramètre.  
  
 Pour supprimer tous les paramètres de l’éditeur de base à la fois, spécifiez une valeur de VSEDITPROPID_ViewComposite_AllCodeWindowDefaults, vt pour le `idprop` paramètre. Dans cet appel, vt est une variante de type VT_BOOL et vt.boolVal a la valeur VARIANT_TRUE.  
  
## <a name="see-also"></a>Voir aussi  
 [Dans l’éditeur de base](../extensibility/inside-the-core-editor.md)   
 [L’accès à theText vue à l’aide de l’API héritée](../extensibility/accessing-thetext-view-by-using-the-legacy-api.md)   
 [Options, boîte de dialogue](../ide/reference/options-dialog-box-visual-studio.md)