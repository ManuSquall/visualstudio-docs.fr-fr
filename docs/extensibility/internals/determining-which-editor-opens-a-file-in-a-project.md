---
title: Détermination de l’éditeur qui ouvre un fichier dans un projet | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80708654"
---
# <a name="determine-which-editor-opens-a-file-in-a-project"></a>Déterminer quel éditeur ouvre un fichier dans un projet
Lorsqu’un utilisateur ouvre un fichier dans un projet, l’environnement passe par un processus d’interrogation, ouvrant finalement l’éditeur ou le concepteur approprié pour ce fichier. La procédure initiale employée par l’environnement est la même pour les éditeurs standard et personnalisés. L’environnement utilise un certain nombre de critères lors de l’interrogation de l’éditeur à utiliser pour ouvrir un fichier et le VSPackage doit coordonner l’environnement au cours de ce processus.

 Par exemple, lorsqu’un utilisateur sélectionne la commande **ouvrir** dans le menu **fichier** , puis choisit *NomFichier. rtf* (ou tout autre fichier avec une extension *. rtf* ), l’environnement appelle l' <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A> implémentation pour chaque projet, en parcourant toutes les instances de projet de la solution. Les projets retournent un jeu d’indicateurs qui identifient les revendications sur un document par priorité. À l’aide de la priorité la plus élevée, l’environnement appelle la <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A> méthode appropriée. Pour plus d’informations sur le processus d’interrogation, consultez [Ajouter des modèles de projet et d’élément de projet](../../extensibility/internals/adding-project-and-project-item-templates.md).

 Le projet fichiers divers prétend tous les fichiers qui ne sont pas revendiqués par d’autres projets. Ainsi, les éditeurs personnalisés peuvent ouvrir des documents avant qu’ils ne soient ouverts par les éditeurs standard. Si un projet fichiers divers prétend un fichier, l’environnement appelle la <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> méthode pour ouvrir le fichier avec un éditeur standard. L’environnement examine sa liste interne des éditeurs inscrits pour en obtenir un qui gère les fichiers *. rtf* . Cette liste se trouve dans le registre à la clé suivante :

 **HKEY_LOCAL_MACHINE \Software\Microsoft\VisualStudio \\ \<version> \Editors \\ \<editor factory guid> \Extensions**

 L’environnement vérifie également les identificateurs de classe dans la clé de **\clsid HKEY_CLASSES_ROOT** pour tous les objets qui ont une sous-clé **DocObject**. Si l’extension de fichier y figure, une version incorporée de l’application, telle que Microsoft Word, est créée sur place dans Visual Studio. Ces objets de document doivent être des fichiers composés qui implémentent l' <xref:Microsoft.VisualStudio.OLE.Interop.IPersistStorage> interface, ou l’objet doit implémenter l' <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat> interface.

 S’il n’y a aucune fabrique d’éditeur pour les fichiers *. rtf* dans le registre, l’environnement recherche l’environnement dans la clé **HKEY_CLASSES_ROOT \\ . rtf** et ouvre l’éditeur spécifié. Si l’extension de fichier est introuvable dans **HKEY_CLASSES_ROOT**, l’environnement utilise l’éditeur de texte principal de Visual Studio pour ouvrir le fichier, s’il s’agit d’un fichier texte.

 En cas d’échec de l’éditeur de texte principal, qui se produit si le fichier n’est pas un fichier texte, l’environnement utilise son éditeur binaire pour le fichier.

 Si l’environnement trouve un éditeur pour l’extension *. rtf* dans son registre, il charge le VSPackage qui implémente cette fabrique d’éditeur. L’environnement appelle la <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A> méthode sur le nouveau VSPackage. Le VSPackage appelle `QueryService` pour `SID_SVsRegistorEditor` , à l’aide de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterEditors.RegisterEditor%2A> méthode pour inscrire la fabrique d’éditeur avec l’environnement.

 L’environnement revérifie à présent la liste interne des éditeurs inscrits pour trouver la fabrique d’éditeur nouvellement inscrite pour les fichiers *. rtf* . L’environnement appelle votre implémentation de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> méthode, en passant le nom de fichier et le type de vue à créer.

## <a name="see-also"></a>Voir aussi
- <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat>
- <xref:Microsoft.VisualStudio.OLE.Interop.IPersistStorage>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>
