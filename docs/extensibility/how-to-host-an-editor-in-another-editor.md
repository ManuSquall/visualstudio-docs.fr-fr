---
title: 'Comment : héberger un éditeur dans un autre éditeur | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - host a nested editor
ms.assetid: 2b0eb705-fe94-4ca8-93e0-9dbd8ce61a44
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 53b4f02135b18c4641d4e802df3d1124a5d06b47
ms.sourcegitcommit: 0bf2aff6abe485e3fe940f5344a62a885ad7f44e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/27/2018
ms.locfileid: "37058384"
---
# <a name="how-to-host-an-editor-in-another-editor"></a>Comment : héberger un éditeur dans un autre éditeur

Dans Visual Studio, vous pouvez héberger un seul éditeur à l’intérieur d’un autre en spécifiant la fenêtre hôte comme une fenêtre parente. Pour ce faire, définissez les paramètres <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID2.VSFPROPID_ParentHwnd> et <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID2.VSFPROPID_ParentFrame> sur le frame de fenêtre enfant.

## <a name="to-set-up-the-window-frame-to-host-an-editor"></a>Définir le frame de fenêtre pour héberger un éditeur

1.  Désigner un éditeur comme un éditeur hébergé par la création d’un volet de fenêtre enfant.

     Ce volet se trouve dans laquelle ira de texte de l’éditeur.

2.  Créer l’éditeur d’hébergement à l’aide de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> ou <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenSpecificEditor%2A> (méthode).

3.  Définir le <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID2.VSFPROPID_ParentHwnd> et <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID2.VSFPROPID_ParentFrame> propriétés dans l’implémentation de frame de fenêtre de l’Éditeur hébergé en transmettant ces propriétés en tant que paramètres à la <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.SetProperty%2A> (méthode), respectivement.

     Si vous avez besoin de récupérer ces paramètres, de ces propriétés pour transmettre le <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> (méthode).

4.  Appelez le <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A> méthode pour l’éditeur de relation contenant-contenu.

     L’éditeur apparaît dans le volet hébergé de l’éditeur de conteneur.

## <a name="robust-programming"></a>Programmation fiable

Le **Concepteur d’applications** dans Visual Studio Team Edition for Architects est un exemple d’un frame de fenêtre d’éditeur qui héberge un autre éditeur. Le **Concepteur d’applications** héberge d’autres concepteurs dans son volet de droite. Un panneau concepteur (ou **propriétés** page) pour chacun des concepteurs de relation contenant-contenus est ajouté pour le frame de fenêtre contenant.