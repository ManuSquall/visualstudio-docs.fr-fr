---
title: Déterminer quel éditeur ouvre un fichier dans un projet | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], determining which editor opens a file
- projects [Visual Studio SDK], determining which editor opens file
- project types, determining which editor opens a file
- persistence, determining which editor opens a file
ms.assetid: acbcf4d8-a53a-4727-9043-696a47369479
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 13b39d52f574c90cf1a4ead8e47e7d24aac94708
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/21/2019
ms.locfileid: "56627959"
---
# <a name="determine-which-editor-opens-a-file-in-a-project"></a>Déterminer quel éditeur ouvre un fichier dans un projet
Lorsqu’un utilisateur ouvre un fichier dans un projet, l’environnement passe par un processus d’interrogation, finalement ouvrir l’éditeur approprié ou le concepteur pour ce fichier. La procédure initiale employée par l’environnement est identique pour les éditeurs standard et personnalisées. L’environnement utilise divers critères lors de l’interrogation de l’éditeur à utiliser pour ouvrir un fichier et le VSPackage doit coordonner avec l’environnement pendant ce processus.

 Par exemple, lorsqu’un utilisateur sélectionne le **Open** commande à partir de la **fichier** menu et choisit ensuite *filename.rtf* (ou tout autre fichier avec un *.rtf*extension), l’environnement appelle le <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A> implémentation pour chaque projet, mais finit par parcourir toutes les instances de projet dans la solution. Projets de retournent un jeu d’indicateurs qui identifient les revendications sur un document par priorité. À l’aide de la priorité la plus élevée, l’environnement appelle approprié <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A> (méthode). Pour plus d’informations sur le processus d’interrogation, consultez [ajouter le projet et les modèles d’élément de projet](../../extensibility/internals/adding-project-and-project-item-templates.md).

 Le projet fichiers divers de revendications de tous les fichiers qui ne sont pas demandées par d’autres projets. De cette façon, les éditeurs personnalisés peuvent ouvrir des documents avant de les ouvrir des éditeurs standard. Si un projet fichiers divers revendique un fichier, l’environnement appelle le <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> méthode pour ouvrir le fichier avec un éditeur standard. L’environnement vérifie sa liste interne des éditeurs enregistrés pour l’une qui gère *.rtf* fichiers. Cette liste se trouve dans le Registre au niveau de la clé suivante :

 **HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\\\<version > \Editors\\\<guid de fabrique d’éditeur > \Extensions**

 L’environnement vérifie également les identificateurs de classe le **HKEY_CLASSES_ROOT\CLSID** clés pour tous les objets qui ont une sous-clé **DocObject**. Si l’extension de fichier s’y trouve, une version incorporée de l’application, tel que Microsoft Word, est créée sur place dans Visual Studio. Ces objets de document doivent être des fichiers composés qui implémentent le <xref:Microsoft.VisualStudio.OLE.Interop.IPersistStorage> interface ou l’objet doit implémenter le <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat> interface.

 S’il n’existe aucune fabrique d’éditeur pour *.rtf* des fichiers dans le Registre, puis l’environnement de recherche les **HKEY_CLASSES_ROOT\\.rtf** de clé et ouvre l’éditeur spécifié. Si l’extension de fichier est introuvable dans **HKEY_CLASSES_ROOT**, puis l’environnement utilise l’éditeur de texte Visual Studio core pour ouvrir le fichier, s’il s’agit d’un fichier texte.

 Si l’éditeur de texte principal échoue, ce qui se produit que si le fichier n’est pas un fichier texte, l’environnement utilise son éditeur binaire pour le fichier.

 Si l’environnement ne trouve pas un éditeur pour le *.rtf* extension dans son Registre, il charge le VSPackage qui implémente cette fabrique d’éditeur. L’environnement appelle le <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A> méthode sur le nouveau VSPackage s’affiche. Les appels de VSPackage `QueryService` pour `SID_SVsRegistorEditor`, en utilisant le <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterEditors.RegisterEditor%2A> méthode pour inscrire la fabrique d’éditeur avec l’environnement.

 L’environnement est maintenant sa liste interne des éditeurs enregistrés pour trouver la fabrique d’éditeur qui vient d’être inscrit pour *.rtf* fichiers. L’environnement appelle votre implémentation de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> méthode, en passant le type de nom et le mode de fichier à créer.

## <a name="see-also"></a>Voir aussi
- <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat>
- <xref:Microsoft.VisualStudio.OLE.Interop.IPersistStorage>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>