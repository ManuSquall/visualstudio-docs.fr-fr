---
title: Déterminer quel éditeur ouvre un fichier dans un projet | Microsoft Docs
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
- editors [Visual Studio SDK], determining which editor opens a file
- projects [Visual Studio SDK], determining which editor opens file
- project types, determining which editor opens a file
- persistence, determining which editor opens a file
ms.assetid: acbcf4d8-a53a-4727-9043-696a47369479
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 832fd838246c075087700494b09757184be687a7
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51741604"
---
# <a name="determining-which-editor-opens-a-file-in-a-project"></a>Déterminer quel éditeur ouvre un fichier dans un projet
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Lorsqu’un utilisateur ouvre un fichier dans un projet, l’environnement passe par un processus d’interrogation, finalement ouvrir l’éditeur approprié ou le concepteur pour ce fichier. La procédure initiale employée par l’environnement est identique pour les éditeurs standard et personnalisées. L’environnement utilise divers critères lors de l’interrogation de l’éditeur à utiliser pour ouvrir un fichier et le VSPackage doit coordonner avec l’environnement pendant ce processus.  
  
 Par exemple, lorsqu’un utilisateur sélectionne le **Open** commande à partir de la **fichier** menu et choisit ensuite `filename`.rtf (ou tout autre fichier avec une extension .rtf), l’environnement appelle le <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A> implémentation pour chaque projet, mais finit par parcourir toutes les instances de projet dans la solution. Projets de retournent un jeu d’indicateurs qui identifient les revendications sur un document par priorité. À l’aide de la priorité la plus élevée, l’environnement appelle approprié <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A> (méthode). Pour plus d’informations sur le processus d’interrogation, [Ajout d’un projet et des modèles d’élément de projet](../../extensibility/internals/adding-project-and-project-item-templates.md).  
  
 Le projet fichiers divers de revendications de tous les fichiers qui ne sont pas demandées par d’autres projets. De cette façon, les éditeurs personnalisés peuvent ouvrir des documents avant de les ouvrir des éditeurs standard. Si un projet fichiers divers revendique un fichier, l’environnement appelle le <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> méthode pour ouvrir le fichier avec un éditeur standard. L’environnement vérifie sa liste interne des éditeurs enregistrés pour l’une qui gère les fichiers .rtf. Cette liste se trouve dans le Registre au niveau de la clé suivante :  
  
 [HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\\<`version`> \Editors\\{<`editor factory guid`>} \Extensions]  
  
 L’environnement vérifie également les identificateurs de classe dans la clé HKEY_CLASSES_ROOT\CLSID pour tous les objets qui ont une sous-clé DocObject. Si l’extension de fichier s’y trouve, une version incorporée de l’application, tel que Microsoft Word, est créée sur place dans Visual Studio. Ces objets de document doivent être des fichiers composés qui implémentent le <xref:Microsoft.VisualStudio.OLE.Interop.IPersistStorage> interface ou l’objet doit implémenter le <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat> interface.  
  
 Si il n’existe aucune fabrique d’éditeur pour les fichiers .rtf dans le Registre, l’environnement de recherche dans le HKEY_CLASSES_ROOT \\.rtf clé et ouvre l’éditeur spécifié. Si l’extension de fichier est introuvable dans HKEY_CLASSES_ROOT, l’environnement utilise l’éditeur de texte Visual Studio core pour ouvrir le fichier s’il s’agit d’un fichier texte.  
  
 Si l’éditeur de texte principal échoue, ce qui se produit que si le fichier n’est pas un fichier texte, l’environnement utilise son éditeur binaire pour le fichier.  
  
 Si l’environnement trouve un éditeur pour l’extension .rtf dans son Registre, il charge le VSPackage qui implémente cette fabrique d’éditeur. L’environnement appelle le <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A> méthode sur le nouveau VSPackage s’affiche. Les appels de VSPackage `QueryService` pour `SID_SVsRegistorEditor`, en utilisant le <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterEditors.RegisterEditor%2A> méthode pour inscrire la fabrique d’éditeur avec l’environnement.  
  
 L’environnement maintenant vérifie à nouveau sa liste interne des éditeurs enregistrés pour trouver la fabrique d’éditeur qui vient d’être inscrit pour les fichiers .rtf. L’environnement appelle votre implémentation de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> méthode, en passant le type de nom et le mode de fichier à créer.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat>   
 <xref:Microsoft.VisualStudio.OLE.Interop.IPersistStorage>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>

