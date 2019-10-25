---
title: Options utilisateur de solution (. Suo) fichier | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- .suo files, VSPackages
- suo files, VSPackages
- solutions, .suo files
- solutions, user options
- solution user options (.suo) file
ms.assetid: 75258e0d-600d-4a3d-94f4-3d7ac12cb47c
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6f21e4a4a6530692709247e64b0d84aa7b06eb3a
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72723809"
---
# <a name="solution-user-options-suo-file"></a>Fichiers des options utilisateur de solution (.Suo)
Le fichier d’options utilisateur de solution (. suo) contient des options de solution par utilisateur. Ce fichier ne doit pas être archivé dans le contrôle de code source.

 Le fichier d’options utilisateur de solution (. suo) est un fichier de stockage structuré, ou composé, stocké dans un format binaire. Vous enregistrez les informations utilisateur dans des flux avec le nom du flux qui est la clé qui sera utilisée pour identifier les informations dans le fichier. suo. Le fichier d’options utilisateur de solution est utilisé pour stocker les paramètres de préférence de l’utilisateur et est créé automatiquement lorsque Visual Studio enregistre une solution.

 Lorsque l’environnement ouvre un fichier. suo, il énumère tous les VSPackages actuellement chargés. Si un VSPackage implémente l’interface <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts>, l’environnement appelle la méthode <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts.LoadUserOptions%2A> sur le VSPackage lui demandant de charger toutes ses données à partir du fichier. suo.

 Il incombe au VSPackage de savoir quels flux il a pu écrire dans le fichier. suo. Pour chaque flux de données qu’il a écrit, le VSPackage rappelle l’environnement par le biais de <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence.LoadPackageUserOpts%2A> pour charger un flux particulier identifié par la clé, qui est le nom du flux. L’environnement appelle ensuite le VSPackage pour lire ce flux de données en passant le nom du flux et un `IStream` pointeur vers la méthode <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence.LoadPackageUserOpts%2A>.

 À ce stade, un autre appel est effectué pour `LoadUserOptions` pour voir s’il existe une autre section du fichier. suo qui doit être lue. Ce processus se poursuit jusqu’à ce que tous les flux de données du fichier. suo aient été lus et traités par l’environnement.

 Lorsque la solution est enregistrée ou fermée, l’environnement appelle la méthode <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence.SavePackageSolutionProps%2A> avec un pointeur vers la méthode <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts.SaveUserOptions%2A>. Un `IStream` contenant les informations binaires à enregistrer est passé à la méthode <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts.WriteUserOptions%2A>, qui écrit ensuite les informations dans le fichier. suo et appelle à nouveau la méthode `SaveUserOptions` pour voir s’il existe un autre flux d’informations à écrire dans le fichier. suo.

 Ces deux méthodes, `SaveUserOptions` et `WriteUserOptions`, sont appelées de manière récursive pour chaque flux d’informations à enregistrer dans le fichier. suo, en passant le pointeur à `IVsSolutionPersistence`. Elles sont appelées de manière récursive pour permettre l’écriture de plusieurs flux dans le fichier. suo. De cette façon, les informations utilisateur sont conservées avec la solution et sont assurées de s’y trouver lors de la prochaine ouverture de la solution.

## <a name="see-also"></a>Voir aussi
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts>
- [Solutions](../../extensibility/internals/solutions-overview.md)