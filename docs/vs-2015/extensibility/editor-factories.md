---
title: Fabriques d’éditeur | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - editor factories
ms.assetid: cf4e8164-3546-441d-b465-e8a836ae7216
caps.latest.revision: 21
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 74ea8d296db643e74654f9016c1f5bff4f34c6d8
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51809452"
---
# <a name="editor-factories"></a>Fabriques d’éditeur
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Une fabrique d’éditeur crée les objets de l’éditeur et les place dans un frame de fenêtre, appelé une vue physique. Il crée les données de document et les objets de vue de document qui sont nécessaires pour créer des éditeurs et concepteurs. Une fabrique d’éditeur est requis pour créer l’éditeur principal de Visual Studio et n’importe quel éditeur standard. Un éditeur personnalisé peut également être créé avec une fabrique d’éditeur.  
  
 Vous créez une fabrique d’éditeur en implémentant le <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> interface. L’exemple suivant illustre comment implémenter <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> pour créer une fabrique d’éditeur :  
  
 [!code-csharp[VSSDKEditorFactories#1](../snippets/csharp/VS_Snippets_VSSDK/vssdkeditorfactories/cs/vssdkeditorfactoriespackage.cs#1)]
 [!code-vb[VSSDKEditorFactories#1](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkeditorfactories/vb/vssdkeditorfactoriespackage.vb#1)]  
  
 Un éditeur est chargé la première fois que vous ouvrez un type de fichier géré par cet éditeur. Vous pouvez choisir d’ouvrir un éditeur spécifique ou l’éditeur par défaut. Si vous sélectionnez l’éditeur par défaut, l’environnement de développement intégré (IDE) détermine l’ouverture de l’éditeur approprié et l’ouvre ensuite. Pour plus d’informations, consultez [déterminer quel éditeur ouvre un fichier dans un projet](../extensibility/internals/determining-which-editor-opens-a-file-in-a-project.md).  
  
## <a name="registering-editor-factories"></a>L’inscription de fabriques d’éditeur  
 Avant de pouvoir utiliser un éditeur que vous avez créé, vous devez tout d’abord enregistrer des informations le concernant, y compris les extensions de fichier qu’il peut gérer.  
  
 Si votre VSPackage est écrit en code managé, vous pouvez utiliser la méthode de Managed Package Framework (MPF) <xref:Microsoft.VisualStudio.Shell.Package.RegisterEditorFactory%2A> pour inscrire la fabrique d’éditeur une fois votre VSPackage est chargé. Si votre VSPackage est écrit en code non managé, vous devez inscrire votre fabrique d’éditeur à l’aide de la <xref:Microsoft.VisualStudio.Shell.Interop.SVsRegisterEditors> service.  
  
### <a name="registering-an-editor-factory-by-using-managed-code"></a>Enregistrement d’une fabrique d’éditeur à l’aide du Code managé  
 Vous devez inscrire votre fabrique d’éditeur dans votre package Visual Studio le `Initialize` (méthode). Tout d’abord appeler `base.Initialize`, puis appelez <xref:Microsoft.VisualStudio.Shell.Package.RegisterEditorFactory%2A> pour chaque fabrique d’éditeur  
  
 Dans le code managé, il est inutile d’annuler l’inscription d’une fabrique d’éditeur, étant donné que le VSPackage gèrent cette étape pour vous. En outre, si votre fabrique d’éditeur implémente <xref:System.IDisposable>, elle est automatiquement supprimée lorsqu’elle est annulée.  
  
### <a name="registering-an-editor-factory-by-using-unmanaged-code"></a>L’inscription d’une fabrique d’éditeur à l’aide de code non managé  
 Dans le <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A> implémentation pour votre package de l’éditeur, utilisez le `QueryService` méthode à appeler `SVsRegisterEditors`. Cette opération retourne un pointeur vers <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterEditors>. Appelez le <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterEditors.RegisterEditor%2A> méthode en passant votre implémentation de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> interface. Vous devez mplémenter <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> dans une classe distincte.  
  
## <a name="the-editor-factory-registration-process"></a>Le processus d’inscription de fabrique d’éditeur  
 Le processus suivant se produit lorsque Visual Studio charge votre éditeur à l’aide de votre fabrique d’éditeur :  
  
1.  Le [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] appels système de projet <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>.  
  
2.  Cette méthode retourne la fabrique d’éditeur. Visual Studio des retards du chargement de package de l’éditeur, toutefois, jusqu'à ce qu’un système de projet a réellement besoin de l’éditeur.  
  
3.  Lorsque l’éditeur a besoin d’un système de projet, Visual Studio appelle <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A>, une méthode spécialisée qui retourne des objets de données de la vue de document et le document.  
  
4.  Si appels par Visual Studio à votre fabrique d’éditeur à l’aide <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> retourner un objet de données de document et un objet de vue de document, Visual Studio crée la fenêtre de document, place l’objet de vue de document qu’elle contient, puis crée une entrée dans le document en cours d’exécution RDT (table) pour l’objet de données de document.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory>   
 [Exécution de la table de document](../extensibility/internals/running-document-table.md)

