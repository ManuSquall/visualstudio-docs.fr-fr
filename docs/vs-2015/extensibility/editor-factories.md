---
title: Fabriques d’éditeur | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - editor factories
ms.assetid: cf4e8164-3546-441d-b465-e8a836ae7216
caps.latest.revision: 21
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 2de1fc8440bd33a526da62dbb4c7937800484aaa
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68197761"
---
# <a name="editor-factories"></a>Fabriques d’éditeur
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Une fabrique d’éditeur crée des objets Editor et les place dans un cadre de fenêtre, connu sous le nom de vue physique. Il crée les données de document et les objets de vue de document nécessaires pour créer des éditeurs et des concepteurs. Une fabrique d’éditeur est requise pour créer l’éditeur principal de Visual Studio et n’importe quel éditeur standard. Un éditeur personnalisé peut également être créé à l’aide d’une fabrique d’éditeur.  
  
 Vous créez une fabrique d’éditeur en implémentant l' <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> interface. L’exemple suivant montre comment implémenter <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> pour créer une fabrique d’éditeur :  
  
 [!code-csharp[VSSDKEditorFactories#1](../snippets/csharp/VS_Snippets_VSSDK/vssdkeditorfactories/cs/vssdkeditorfactoriespackage.cs#1)]
 [!code-vb[VSSDKEditorFactories#1](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkeditorfactories/vb/vssdkeditorfactoriespackage.vb#1)]  
  
 Un éditeur est chargé la première fois que vous ouvrez un type de fichier géré par cet éditeur. Vous pouvez choisir d’ouvrir un éditeur spécifique ou l’éditeur par défaut. Si vous sélectionnez l’éditeur par défaut, l’environnement de développement intégré (IDE) détermine l’éditeur approprié pour l’ouvrir, puis l’ouvre. Pour plus d’informations, consultez [détermination de l’éditeur qui ouvre un fichier dans un projet](../extensibility/internals/determining-which-editor-opens-a-file-in-a-project.md).  
  
## <a name="registering-editor-factories"></a>Inscrire des fabriques d’éditeur  
 Avant de pouvoir utiliser un éditeur que vous avez créé, vous devez d’abord enregistrer les informations le concernant, y compris les extensions de fichier qu’il peut gérer.  
  
 Si votre VSPackage est écrit en code managé, vous pouvez utiliser la méthode Managed package Framework (MPF) <xref:Microsoft.VisualStudio.Shell.Package.RegisterEditorFactory%2A> pour inscrire la fabrique d’éditeur après le chargement de votre VSPackage. Si votre VSPackage est écrit en code non managé, vous devez inscrire votre fabrique d’éditeur à l’aide du <xref:Microsoft.VisualStudio.Shell.Interop.SVsRegisterEditors> service.  
  
### <a name="registering-an-editor-factory-by-using-managed-code"></a>Inscription d’une fabrique d’éditeur à l’aide de code managé  
 Vous devez inscrire votre fabrique d’éditeur dans la méthode de votre VSPackage `Initialize` . Premier appel `base.Initialize` , puis appeler <xref:Microsoft.VisualStudio.Shell.Package.RegisterEditorFactory%2A> pour chaque fabrique d’éditeur  
  
 En code managé, il n’est pas nécessaire d’annuler l’inscription d’une fabrique d’éditeur, car le VSPackage le gère pour vous. En outre, si votre fabrique d’éditeur implémente <xref:System.IDisposable> , elle est automatiquement supprimée lorsqu’elle est désinscrite.  
  
### <a name="registering-an-editor-factory-by-using-unmanaged-code"></a>Inscription d’une fabrique d’éditeur à l’aide de code non managé  
 Dans l' <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A> implémentation de votre package d’éditeur, utilisez la `QueryService` méthode pour appeler `SVsRegisterEditors` . Cela retourne un pointeur vers <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterEditors> . Appelez la <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterEditors.RegisterEditor%2A> méthode en passant votre implémentation de l' <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> interface. Vous devez mplémenter <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> dans une classe distincte.  
  
## <a name="the-editor-factory-registration-process"></a>Processus d’inscription de la fabrique d’éditeur  
 Le processus suivant se produit lorsque Visual Studio charge votre éditeur à l’aide de votre fabrique d’éditeur :  
  
1. Le [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] système de projet appelle <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> .  
  
2. Cette méthode retourne la fabrique d’éditeur. Toutefois, Visual Studio retarde le chargement du package de l’éditeur, jusqu’à ce qu’un système de projet ait réellement besoin de l’éditeur.  
  
3. Lorsqu’un système de projet a besoin de l’éditeur, Visual Studio appelle <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> , une méthode spécialisée qui retourne la vue de document et les objets de données de document.  
  
4. Si les appels de Visual Studio à votre fabrique d’éditeur à l’aide de <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> retournent un objet de données de document et un objet de vue de document, Visual Studio crée ensuite la fenêtre de document, y place l’objet de vue de document et crée une entrée dans la table de document en cours d’exécution (RDT) pour l’objet de données de document.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory>   
 [Exécution de la table de document](../extensibility/internals/running-document-table.md)
