---
title: Options utilisateur de solution (. Dossier Suo) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- .suo files, VSPackages
- suo files, VSPackages
- solutions, .suo files
- solutions, user options
- solution user options (.suo) file
ms.assetid: 75258e0d-600d-4a3d-94f4-3d7ac12cb47c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9469663d3ac258e1c568778894d8584c68c13632
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705317"
---
# <a name="solution-user-options-suo-file"></a>Fichiers des options utilisateur de solution (.Suo)
Le fichier d’options utilisateur de solution (.suo) contient des options de solution par utilisateur. Ce fichier ne doit pas être enregistré au contrôle du code source.

 Le fichier d’options d’utilisateur de solution (.suo) est un fichier de stockage structuré, ou composé, stocké dans un format binaire. Vous enregistrez les informations utilisateur dans les flux avec le nom du flux étant la clé qui sera utilisé pour identifier les informations dans le fichier .suo. Le fichier d’options utilisateur de solution est utilisé pour stocker les paramètres de préférence de l’utilisateur, et est créé automatiquement lorsque Visual Studio enregistre une solution.

 Lorsque l’environnement ouvre un fichier .suo, il énumère tous les VSPackages actuellement chargés. Si un VSPackage <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts> implémente l’interface, alors l’environnement appelle la <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts.LoadUserOptions%2A> méthode sur le VSPackage lui demandant de charger toutes ses données à partir du fichier .suo.

 Il est de la responsabilité du VSPackage de savoir quels flux il pourrait avoir écrit dans le fichier .suo. Pour chaque flux qu’il a écrit, le <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence.LoadPackageUserOpts%2A> VSPackage rappelle à l’environnement par le biais de charger un flux particulier qui est identifié par la clé, qui est le nom du flux. L’environnement rappelle ensuite à la VSPackage pour lire ce flux `IStream` particulier <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence.LoadPackageUserOpts%2A> en passant le nom du flux et un pointeur à la méthode.

 À ce moment-là, `LoadUserOptions` un autre appel est fait pour voir s’il y a une autre section du fichier .suo qui doit être lue. Ce processus se poursuit jusqu’à ce que tous les flux de données du fichier .suo aient été lus et traités par l’environnement.

 Lorsque la solution est sauvegardée <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence.SavePackageSolutionProps%2A> ou fermée, l’environnement appelle la méthode avec un pointeur vers la <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts.SaveUserOptions%2A> méthode. Un `IStream` contenant les informations binaires à <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts.WriteUserOptions%2A> sauver est passé à la méthode, qui `SaveUserOptions` écrit ensuite les informations sur le fichier .suo et appelle la méthode à nouveau pour voir s’il ya un autre flux d’informations à écrire sur le fichier .suo.

 Ces deux `SaveUserOptions` méthodes, et `WriteUserOptions`, sont appelés de façon récursive pour chaque flux d’informations à sauver sur le fichier .suo, en passant dans le pointeur à `IVsSolutionPersistence`. Ils sont appelés de façon récursive pour permettre l’écriture de plusieurs flux au fichier .suo. De cette façon, les informations utilisateur sont persistées avec la solution et est garanti d’être là la prochaine fois que la solution est ouverte.

## <a name="see-also"></a>Voir aussi
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts>
- [Solutions](../../extensibility/internals/solutions-overview.md)
