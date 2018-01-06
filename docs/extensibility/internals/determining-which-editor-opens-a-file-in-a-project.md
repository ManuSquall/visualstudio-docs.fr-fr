---
title: "Détermination de l’éditeur ouvre un fichier dans un projet | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], determining which editor opens a file
- projects [Visual Studio SDK], determining which editor opens file
- project types, determining which editor opens a file
- persistence, determining which editor opens a file
ms.assetid: acbcf4d8-a53a-4727-9043-696a47369479
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: f7c69bc08d0f1bb72a37b76fca2d402d73036deb
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="determining-which-editor-opens-a-file-in-a-project"></a>Détermination pour ouvrir l’éditeur à un fichier dans un projet
Lorsqu’un utilisateur ouvre un fichier dans un projet, l’environnement passe par un processus d’interrogation, par la suite ouvrir l’éditeur approprié ou du concepteur pour ce fichier. La procédure initiale employée par l’environnement est identique pour les éditeurs standard et personnalisées. L’environnement utilise une grande variété de critères lors de l’interrogation de l’éditeur à utiliser pour ouvrir un fichier et le VSPackage doit coordonner avec l’environnement pendant ce processus.  
  
 Par exemple, lorsqu’un utilisateur sélectionne le **ouvrir** commande à partir de la **fichier** menu et choisit ensuite `filename`.rtf (ou tout autre fichier avec une extension .rtf), l’environnement appelle le <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A> implémentation pour chaque projet, éventuellement parcourir toutes les instances de projet dans la solution. Projets de retournent un jeu d’indicateurs qui identifient les revendications sur un document par priorité. À l’aide de la priorité la plus élevée, l’environnement appelle approprié <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A> (méthode). Pour plus d’informations sur le processus d’interrogation, [Ajout d’un projet et modèles d’élément de projet](../../extensibility/internals/adding-project-and-project-item-templates.md).  
  
 Le projet fichiers divers revendications tous les fichiers qui ne sont pas demandés par d’autres projets. De cette manière, les éditeurs personnalisés peuvent ouvrir des documents avant d’ouvrir les éditeurs standards. Si un projet fichiers divers déclare un fichier, l’environnement appelle le <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> méthode pour ouvrir le fichier avec un éditeur standard. L’environnement vérifie sa liste interne des éditeurs inscrits pour un objet qui gère les fichiers .rtf. Cette liste se trouve dans le Registre à la clé suivante :  
  
 [HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\\<`version`> \Editors\\{<`editor factory guid`>} \Extensions]  
  
 L’environnement vérifie également les identificateurs de classe dans la clé HKEY_CLASSES_ROOT\CLSID pour tous les objets qui ont une sous-clé DocObject. Si l’extension de fichier est trouvée, une version incorporée de l’application, telles que Microsoft Word, est créée sur place dans Visual Studio. Ces objets de document doivent être des fichiers composés qui implémentent la <xref:Microsoft.VisualStudio.OLE.Interop.IPersistStorage> interface, soit l’objet doit implémenter le <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat> interface.  
  
 S’il n’existe aucune fabrique d’éditeur pour les fichiers .rtf dans le Registre, puis l’environnement recherche dans le HKEY_CLASSES_ROOT \\.rtf clé et ouvre l’éditeur spécifié. Si l’extension de fichier est introuvable dans HKEY_CLASSES_ROOT, l’environnement utilise l’éditeur de texte Visual Studio core pour ouvrir le fichier s’il s’agit d’un fichier texte.  
  
 Si l’éditeur de texte principal échoue, ce qui se produit que si le fichier n’est pas un fichier texte, l’environnement utilise son éditeur binaire pour le fichier.  
  
 Si l’environnement trouve un éditeur pour l’extension .rtf dans son Registre, il charge le VSPackage qui implémente cette fabrique d’éditeur. L’environnement appelle le <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A> méthode sur le nouveau VSPackage s’affiche. Les appels VSPackage `QueryService` pour `SID_SVsRegistorEditor`, à l’aide du <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterEditors.RegisterEditor%2A> méthode pour inscrire la fabrique d’éditeur avec l’environnement.  
  
 L’environnement maintenant vérifie à nouveau sa liste interne des éditeurs pour trouver la fabrique d’éditeur qui vient d’être inscrit pour les fichiers .rtf. L’environnement appelle votre implémentation de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> méthode, en passant le type de nom et la vue de fichier à créer.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat>   
 <xref:Microsoft.VisualStudio.OLE.Interop.IPersistStorage>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>