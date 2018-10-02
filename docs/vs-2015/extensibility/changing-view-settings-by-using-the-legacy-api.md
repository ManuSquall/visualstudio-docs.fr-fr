---
title: Modification des paramètres de la vue à l’aide de l’API héritée | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - changing view settings
ms.assetid: 12c9b300-0894-4124-96a1-764326176d77
caps.latest.revision: 19
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 9c6ffd7796e0f90748ed46050d5d07ce2df210db
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47516742"
---
# <a name="changing-view-settings-by-using-the-legacy-api"></a>Modification des paramètres de vue à l’aide de l’API héritée
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [modification des paramètres de vue à l’aide de l’API héritée](https://docs.microsoft.com/visualstudio/extensibility/changing-view-settings-by-using-the-legacy-api).  
  
Paramètres pour les principales fonctionnalités de l’éditeur, telles que le retour automatique à la marge de sélection et l’espace virtuel, peuvent être modifiés par l’utilisateur par le biais de la **Options** boîte de dialogue. Toutefois, il est également possible de modifier ces paramètres par programmation.  
  
## <a name="changing-settings-by-using-the-legacy-api"></a>Modification des paramètres à l’aide de l’API héritée  
 Le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyCategoryContainer> interface expose un ensemble de propriétés de l’éditeur de texte. L’affichage de texte contient une catégorie de propriétés (GUID_EditPropCategory_View_MasterSettings) qui représente le groupe de paramètres modifiés par programme pour l’affichage de texte. Une fois que les paramètres d’affichage ont été modifiés de cette façon, ils ne peuvent pas être modifiés dans le **Options** boîte de dialogue jusqu'à ce qu’elles sont réinitialisées.  
  
 Voici le processus classique permettant de modifier les paramètres de vue pour une instance de l’éditeur principal.  
  
1.  Appelez `QueryInterface` sur le (<xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView>) pour le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyCategoryContainer> interface.  
  
2.  Appelez le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyCategoryContainer.GetPropertyCategory%2A> méthode, en spécifiant une valeur de GUID_EditPropCategory_View_MasterSettings pour la `rguidCategory` paramètre.  
  
     Cette opération retourne un pointeur vers le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyCategoryContainer> interface, qui contient l’ensemble de propriétés forcées pour la vue. Tous les paramètres de ce groupe sont contraints de façon permanente. Si un paramètre n’est pas dans ce groupe, puis il suit les options spécifiées dans le **Options** boîte de dialogue ou les commandes de l’utilisateur.  
  
3.  Appelez le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyContainer.SetProperty%2A> méthode, en spécifiant la valeur de paramètres appropriés dans le `idprop` paramètre.  
  
     Par exemple, pour forcer le retour automatique à, appelez <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyContainer.SetProperty%2A> et spécifiez la valeur VSEDITPROPID_ViewLangOpt_WordWrap, `vt` pour le `idprop` paramètre. Dans cet appel, `vt` est une variante de type VT_BOOL et `vt.boolVal` a la valeur VARIANT_TRUE.  
  
## <a name="resetting-changed-view-settings"></a>Réinitialisation des paramètres d’affichage modifié  
 Pour rétablir n’importe quelle vue modifiée définition d’une instance de l’éditeur principal, appelez le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyContainer.RemoveProperty%2A> (méthode) et spécifiez la valeur du paramètre approprié dans le `idprop` paramètre.  
  
 Par exemple, pour permettre le retour automatique à pour les faire flotter librement, vous serez supprimer à partir de la catégorie de propriété en appelant <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyContainer.RemoveProperty%2A> et en spécifiant une valeur de VSEDITPROPID_ViewLangOpt_WordWrap pour la `idprop` paramètre.  
  
 Pour supprimer les paramètres de tout cela a changé pour l’éditeur principal à la fois, spécifiez la valeur VSEDITPROPID_ViewComposite_AllCodeWindowDefaults, vt pour le `idprop` paramètre. Dans cet appel, vt est une variante de type VT_BOOL et vt.boolVal a la valeur VARIANT_TRUE.  
  
## <a name="see-also"></a>Voir aussi  
 [À l’intérieur de l’éditeur principal](../extensibility/inside-the-core-editor.md)   
 [L’accès à theText vue à l’aide de l’API héritée](../extensibility/accessing-thetext-view-by-using-the-legacy-api.md)   
 [Options, boîte de dialogue](../ide/reference/options-dialog-box-visual-studio.md)

