---
title: Objet VSTextBuffer | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- VSTextBuffer
helpviewer_keywords:
- VSTextBuffer object, reference
- views [Visual Studio SDK], VSTextBuffer object
ms.assetid: c5f94b45-7249-4e1f-a53d-1d2a1c61e0ef
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 00405642ea1a14ae703a2d5fc992c98c4c59ea03
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53955368"
---
# <a name="vstextbuffer-object"></a>Objet VSTextBuffer
L’objet de mémoire tampon de texte représente un flux de texte Unicode, ce qui est généralement associé à un fichier. Un <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> objet peut être utilisé en dehors du contexte de l’éditeur principal, par exemple, un Assistant.  
  
 Le tableau suivant présente les interfaces de `VSTextBuffer`.  
  
|Méthode|Description|  
|------------|-----------------|  
|[IOleCommandTarget](/windows/desktop/api/docobj/nn-docobj-iolecommandtarget)|Interface OLE standard. Utilisé pour la gestion de la mémoire tampon Annuler/Rétablir.|  
|[IPersistFile](/windows/desktop/api/objidl/nn-objidl-ipersistfile)|Interface OLE standard.|  
|[IPersistStream](/windows/desktop/api/objidl/nn-objidl-ipersiststream)|Interface OLE standard.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompoundAction>|Permet la création d’actions composés (autrement dit, les actions qui sont regroupées dans une unité d’annulation/de rétablissement unique).|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData>|Active la persistance des données de document gérées par la mémoire tampon de texte.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>|Fournit des services de base ; utilisé par de nombreux clients.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextFind>|Utilisé pour rechercher une mémoire tampon.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines>|Fournit lire et écrire des fonctionnalités à l’aide de coordonnées à deux dimensions. Hérite de `IVsTextBuffer`.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream>|Fournit lire et écrire des fonctionnalités à l’aide des coordonnées unidimensionnelles. Hérite de `IVsTextBuffer`.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextScanner>|Offre un accès séquentiel, orienté flux et à du texte dans la mémoire tampon rapide.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsUserData>|Fournit l’accès à une collection générique de propriétés. La propriété la plus importante est le nom ou le moniker, de la mémoire tampon. Vous pouvez stocker vos propres données aléatoires dans la mémoire tampon avec cette interface par la création d’un GUID et l’utiliser en tant que clé.|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer>|Prend en charge les points de connexion pour les événements.|  
  
## <a name="remarks"></a>Notes  
 Le `VSTextBuffer` se trouve généralement par un `QueryInterface` appeler sur `IVsTextBuffer`. Pour plus d’informations, consultez [mémoire tampon de texte](../extensibility/accessing-the-text-buffer-by-using-the-legacy-api.md).  
  
## <a name="see-also"></a>Voir aussi  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView>   
 [Édition de figures](https://www.microsoft.com/download/details.aspx?id=55984)