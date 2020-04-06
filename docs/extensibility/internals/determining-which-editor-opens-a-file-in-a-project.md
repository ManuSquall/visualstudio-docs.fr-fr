---
title: Déterminer quel éditeur ouvre un fichier dans un projet . Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], determining which editor opens a file
- projects [Visual Studio SDK], determining which editor opens file
- project types, determining which editor opens a file
- persistence, determining which editor opens a file
ms.assetid: acbcf4d8-a53a-4727-9043-696a47369479
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: af7037a3b4bfbae1801e802256af240d017d2789
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708654"
---
# <a name="determine-which-editor-opens-a-file-in-a-project"></a>Déterminer quel éditeur ouvre un fichier dans un projet
Lorsqu’un utilisateur ouvre un fichier dans un projet, l’environnement passe par un processus de sondage, ouvrant éventuellement l’éditeur ou le concepteur approprié pour ce fichier. La procédure initiale utilisée par l’environnement est la même pour les éditeurs standard et personnalisés. L’environnement utilise une variété de critères lors du sondage que l’éditeur utiliser pour ouvrir un fichier et le VSPackage doit coordonner avec l’environnement au cours de ce processus.

 Par exemple, lorsqu’un utilisateur sélectionne la commande **Open** dans le menu **Fichier,** puis choisit *filename.rtf* (ou <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A> tout autre fichier avec une extension *.rtf),* l’environnement appelle la mise en œuvre de chaque projet, éventuellement à vélo à travers toutes les instances du projet dans la solution. Les projets renvoient un ensemble de drapeaux qui identifient les revendications sur un document par priorité. En utilisant la plus haute <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A> priorité, l’environnement appelle la méthode appropriée. Pour plus d’informations sur le processus de vote, voir [ajouter des modèles de projet et d’élément de projet](../../extensibility/internals/adding-project-and-project-item-templates.md).

 Le projet Divers Files revendique tous les dossiers qui ne sont pas réclamés par d’autres projets. De cette façon, les éditeurs personnalisés peuvent ouvrir des documents avant que les éditeurs standard ne les ouvrent. Si un projet Miscellaneous Files revendique un <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> fichier, l’environnement appelle la méthode pour ouvrir le fichier auprès d’un éditeur standard. L’environnement vérifie sa liste interne des éditeurs enregistrés pour celui qui gère les fichiers *.rtf.* Cette liste est située dans le registre à la clé suivante :

 **\\\<HKEY_LOCAL_MACHINE-Software-Microsoft-VisualStudio version>-Editors\\\<editor factory guid>-Extensions**

 L’environnement vérifie également les identifiants de classe dans la clé **HKEY_CLASSES_ROOT CLSID** pour tous les objets qui ont un **DocObject**sous-clé . Si l’extension de fichier y est trouvée, une version intégrée de l’application, comme Microsoft Word, est créée en place dans Visual Studio. Ces objets de document doivent <xref:Microsoft.VisualStudio.OLE.Interop.IPersistStorage> être des fichiers composés <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat> qui implémentent l’interface, ou l’objet doit implémenter l’interface.

 S’il n’y a pas d’usine d’éditeur pour les fichiers *.rtf* dans le registre, alors l’environnement regarde dans la HKEY_CLASSES_ROOT clé **\\.rtf** et ouvre l’éditeur spécifié là-bas. Si l’extension de fichier n’est pas trouvée dans **HKEY_CLASSES_ROOT,** alors l’environnement utilise l’éditeur de texte de base visual Studio pour ouvrir le fichier, s’il s’agit d’un fichier texte.

 Si l’éditeur de texte de base échoue, ce qui se produit si le fichier n’est pas un fichier texte, alors l’environnement utilise son éditeur binaire pour le fichier.

 Si l’environnement ne trouver un éditeur pour l’extension *.rtf* dans son registre, il charge le VSPackage qui met en œuvre cette usine d’éditeur. L’environnement <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A> appelle la méthode sur le nouveau VSPackage. Le VSPackage `QueryService` `SID_SVsRegistorEditor`appelle à <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterEditors.RegisterEditor%2A> , en utilisant la méthode pour enregistrer l’usine de rédacteur avec l’environnement.

 L’environnement revérifier maintenant sa liste interne des éditeurs enregistrés pour trouver l’usine nouvellement enregistrée de rédacteur pour les fichiers *.rtf.* L’environnement appelle votre <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> mise en œuvre de la méthode, en passant dans le nom de fichier et le type de vue à créer.

## <a name="see-also"></a>Voir aussi
- <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat>
- <xref:Microsoft.VisualStudio.OLE.Interop.IPersistStorage>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>
