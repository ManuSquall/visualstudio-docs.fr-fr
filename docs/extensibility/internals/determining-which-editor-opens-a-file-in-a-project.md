---
title: "Détermination de l’éditeur s’ouvre un fichier dans un projet | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], determining which editor opens a file
- projects [Visual Studio SDK], determining which editor opens file
- project types, determining which editor opens a file
- persistence, determining which editor opens a file
ms.assetid: acbcf4d8-a53a-4727-9043-696a47369479
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: ac16b6f4d8429d328cfd76b8b02cd1620f4a4294
ms.lasthandoff: 02/22/2017

---
# <a name="determining-which-editor-opens-a-file-in-a-project"></a>Détermination de l’éditeur s’ouvre un fichier dans un projet
Lorsqu’un utilisateur ouvre un fichier dans un projet, l’environnement passe par un processus d’interrogation, finalement ouvrir l’éditeur approprié ou du concepteur pour ce fichier. La procédure initiale employée par l’environnement est identique pour les éditeurs standard et personnalisées. L’environnement utilise divers critères lors de l’interrogation de l’éditeur à utiliser pour ouvrir un fichier et le VSPackage doit coordonner avec l’environnement au cours de ce processus.  
  
 Par exemple, lorsqu’un utilisateur sélectionne le **Open** commande à partir de la **fichier** menu et choisit ensuite `filename`.rtf (ou tout autre fichier ayant l’extension .rtf), l’environnement appelle le <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A>implémentation pour chaque projet, et finalement à parcourir toutes les instances de projet dans la solution.</xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A> Projets de retournent un jeu d’indicateurs qui identifient les revendications sur un document par priorité. À l’aide de la priorité la plus élevée, l’environnement appelle approprié <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A>méthode.</xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A> Pour plus d’informations sur le processus d’interrogation, [Ajout d’un projet et modèles d’élément de projet](../../extensibility/internals/adding-project-and-project-item-templates.md).  
  
 Le projet fichiers divers de revendications tous les fichiers qui ne sont pas demandées par d’autres projets. De cette façon, les éditeurs personnalisés peuvent ouvrir des documents avant d’ouvrir les éditeurs standards. Si un projet fichiers divers déclare un fichier, l’environnement appelle le <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>méthode pour ouvrir le fichier avec un éditeur standard.</xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> L’environnement vérifie sa liste interne des éditeurs celui qui gère les fichiers .rtf. Cette liste se trouve dans le Registre à la clé suivante :  
  
 [HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\\<`version`> \Editors\\{`editor factory guid`>} \Extensions]  
  
 L’environnement vérifie également les identificateurs de classe dans la clé HKEY_CLASSES_ROOT\CLSID pour tous les objets qui ont une sous-clé DocObject. Si l’extension de fichier s’y trouve, une version incorporée de l’application, tels que Microsoft Word, est créée sur place dans Visual Studio. Ces objets de document doivent être des fichiers composés qui implémentent la <xref:Microsoft.VisualStudio.OLE.Interop.IPersistStorage>interface ou l’objet doit implémenter le <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat>interface.</xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat> </xref:Microsoft.VisualStudio.OLE.Interop.IPersistStorage>  
  
 S’il n’existe aucune fabrique d’éditeur pour les fichiers .rtf dans le Registre, puis l’environnement de recherche dans le HKEY_CLASSES_ROOT \\.rtf clé et ouvre l’éditeur spécifié. Si l’extension de fichier est introuvable dans HKEY_CLASSES_ROOT, l’environnement utilise l’éditeur de texte Visual Studio core pour ouvrir le fichier s’il s’agit d’un fichier texte.  
  
 Si l’éditeur de texte principal tombe en panne, ce qui se produit que si le fichier n’est pas un fichier texte, l’environnement utilise son éditeur binaire pour le fichier.  
  
 Si l’environnement trouve un éditeur pour l’extension .rtf dans son Registre, il charge le VSPackage qui implémente cette fabrique d’éditeur. L’environnement appelle le <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A>méthode sur le nouveau VSPackage.</xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A> Les appels VSPackage `QueryService` pour `SID_SVsRegistorEditor`, en utilisant la <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterEditors.RegisterEditor%2A>méthode pour inscrire la fabrique d’éditeur avec l’environnement.</xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterEditors.RegisterEditor%2A>  
  
 L’environnement maintenant vérifie à nouveau sa liste interne des éditeurs pour trouver la fabrique d’éditeur qui vient d’être inscrit pour les fichiers .rtf. L’environnement appelle l’implémentation de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A>méthode, en passant le type de nom et le mode fichier à créer.</xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A>  
  
## <a name="see-also"></a>Voir aussi  
 <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat></xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat>   
 <xref:Microsoft.VisualStudio.OLE.Interop.IPersistStorage></xref:Microsoft.VisualStudio.OLE.Interop.IPersistStorage>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A></xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A></xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A></xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A></xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>
