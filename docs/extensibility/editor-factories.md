---
title: "Fabriques d&#39;&#233;diteur | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "éditeurs (Visual Studio SDK), hérités - fabriques d'éditeur"
ms.assetid: cf4e8164-3546-441d-b465-e8a836ae7216
caps.latest.revision: 20
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 20
---
# Fabriques d&#39;&#233;diteur
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Une fabrique d'éditeur crée des objets d'éditeur et les place dans un frame de fenêtre, appelée vue physique.  Il crée les objets de vue de données et le fichier de document qui sont nécessaires pour créer des éditeurs et les concepteurs.  Une fabrique d'éditeur est requise pour créer l'éditeur principal de Visual Studio et tout éditeur standard.  un éditeur personnalisé peut éventuellement être créé également avec une fabrique d'éditeur.  
  
 vous créez une fabrique d'éditeur en implémentant l'interface d' <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> .  l'exemple suivant montre comment implémenter <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> pour créer une fabrique d'éditeur :  
  
 [!code-vb[VSSDKEditorFactories#1](../extensibility/codesnippet/VisualBasic/editor-factories_1.vb)]
 [!code-cs[VSSDKEditorFactories#1](../extensibility/codesnippet/CSharp/editor-factories_1.cs)]  
  
 un éditeur est chargé la première fois que vous ouvrez un type de fichier géré par cet éditeur.  vous pouvez choisir d'ouvrir un éditeur spécifique ou l'éditeur par défaut.  Si vous sélectionnez l'éditeur par défaut, l'environnement \(IDE\) IDE détermine l'éditeur approprié pour ouvrir puis l'ouvre.  Pour plus d'informations, consultez [Détermination de l'éditeur s'ouvre un fichier dans un projet](../extensibility/internals/determining-which-editor-opens-a-file-in-a-project.md).  
  
## Stocker les fabriques d'éditeur  
 Avant de pouvoir utiliser un éditeur que vous avez créé, vous devez d'abord enregistrer des informations sur ce sujet, notamment les extensions de fichier qu'elles peuvent gérer.  
  
 Si votre VSPackage est écrit en code managé, vous pouvez utiliser la méthode managée <xref:Microsoft.VisualStudio.Shell.Package.RegisterEditorFactory%2A> \(MPF\) d'infrastructure de package pour inscrire la fabrique d'éditeur après que votre VSPackage chargé.  Si votre VSPackage est écrit en code non managé, vous devez enregistrer votre fabrique d'éditeur à l'aide de le service d' <xref:Microsoft.VisualStudio.Shell.Interop.SVsRegisterEditors> .  
  
### Inscription d'une fabrique d'éditeur à l'aide de code managé  
 vous devez enregistrer votre fabrique d'éditeur dans la méthode d' `Initialize` de votre VSPackage.  Le premier appel `base.Initialize`, et appelez ensuite <xref:Microsoft.VisualStudio.Shell.Package.RegisterEditorFactory%2A> pour chaque fabrique d'éditeur  
  
 En code managé, il n'y a aucun besoin d'annuler l'enregistrement d'une fabrique d'éditeur, car le VSPackage gérera cette opération pour vous.  En outre, si votre fabrique d'éditeur implémente <xref:System.IDisposable>, il est automatiquement supprimé lorsqu'il est annulé.  
  
### Inscription d'une fabrique d'éditeur à l'aide de code non managé  
 Dans l'implémentation d' <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A> pour votre package de l'éditeur, utilisez la méthode d' `QueryService` pour appeler `SVsRegisterEditors`.  De cette façon retourne un pointeur vers <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterEditors>.  appelez la méthode d' <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterEditors.RegisterEditor%2A> en passant votre implémentation de l'interface d' <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> .  vous devez mplement <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> dans une classe distincte.  
  
## La procédure d'enregistrement de fabrique d'éditeur  
 Le processus suivant se produit lorsque Visual Studio charge votre éditeur qui utilisent votre fabrique d'éditeur :  
  
1.  le système de projet de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] appelle l' <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>.  
  
2.  Cette méthode retourne la fabrique d'éditeur.  Visual Studio diffère charger le package de l'éditeur, toutefois, jusqu'à ce qu'un système de projet a besoin de l'éditeur.  
  
3.  Lorsqu'un système de projet a besoin de l'éditeur, Visual Studio appelle l' <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A>, une méthode particulière qui retourne la vue du document et les objets de données du document.  
  
4.  Si les appels par Visual Studio à votre fabrique d'éditeur à l'aide de l' <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> retournent un objet de données du document et un objet de vue du document, Visual Studio crée la fenêtre de document, recherche l'objet de vue du document à l'intérieur, et transforme une entrée en tableau \(RDT\) en cours de exécution du document associé à l'objet de données du document.  
  
## Voir aussi  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory>   
 [Table de Document en cours d’exécution](../extensibility/internals/running-document-table.md)