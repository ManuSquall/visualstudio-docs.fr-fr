---
title: Options utilisateur de solution (. Suo) fichier | Microsoft Docs
description: Découvrez le fichier d’options utilisateur de solution (. suo), qui contient des options de solution par utilisateur dans un fichier de stockage structuré stocké dans un format binaire.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- .suo files, VSPackages
- suo files, VSPackages
- solutions, .suo files
- solutions, user options
- solution user options (.suo) file
ms.assetid: 75258e0d-600d-4a3d-94f4-3d7ac12cb47c
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 1a38eb865cf003f7a2f9bafde7b6e527ce24f2bd
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112899613"
---
# <a name="solution-user-options-suo-file"></a>Fichiers des options utilisateur de solution (.Suo)
Le fichier d’options utilisateur de solution (. suo) contient des options de solution par utilisateur. Ce fichier ne doit pas être archivé dans le contrôle de code source.

 Le fichier d’options utilisateur de solution (. suo) est un fichier de stockage structuré, ou composé, stocké dans un format binaire. Vous enregistrez les informations utilisateur dans des flux avec le nom du flux qui est la clé qui sera utilisée pour identifier les informations dans le fichier. suo. Le fichier d’options utilisateur de solution est utilisé pour stocker les paramètres de préférence de l’utilisateur et est créé automatiquement lorsque Visual Studio enregistre une solution.

 Lorsque l’environnement ouvre un fichier. suo, il énumère tous les VSPackages actuellement chargés. Si un VSPackage implémente l' <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts> interface, l’environnement appelle la <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts.LoadUserOptions%2A> méthode sur le VSPackage lui demandant de charger toutes ses données à partir du fichier. suo.

 Il incombe au VSPackage de savoir quels flux il a pu écrire dans le fichier. suo. Pour chaque flux de données qu’il a écrit, le VSPackage rappelle l’environnement par le biais <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence.LoadPackageUserOpts%2A> de pour charger un flux particulier identifié par la clé, qui est le nom du flux. L’environnement appelle ensuite le VSPackage pour lire ce flux de données en passant le nom du flux et un `IStream` pointeur vers la <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence.LoadPackageUserOpts%2A> méthode.

 À ce stade, un autre appel est fait à `LoadUserOptions` pour déterminer s’il existe une autre section du fichier. suo qui doit être lue. Ce processus se poursuit jusqu’à ce que tous les flux de données du fichier. suo aient été lus et traités par l’environnement.

 Lorsque la solution est enregistrée ou fermée, l’environnement appelle la <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence.SavePackageSolutionProps%2A> méthode avec un pointeur vers la <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts.SaveUserOptions%2A> méthode. Un `IStream` contenant les informations binaires à enregistrer est passé à la <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts.WriteUserOptions%2A> méthode, qui écrit ensuite les informations dans le fichier. suo et appelle à `SaveUserOptions` nouveau la méthode pour voir s’il existe un autre flux d’informations à écrire dans le fichier. suo.

 Ces deux méthodes, `SaveUserOptions` et `WriteUserOptions` , sont appelées de manière récursive pour chaque flux d’informations à enregistrer dans le fichier. suo, en passant le pointeur à `IVsSolutionPersistence` . Elles sont appelées de manière récursive pour permettre l’écriture de plusieurs flux dans le fichier. suo. De cette façon, les informations utilisateur sont conservées avec la solution et sont assurées de s’y trouver lors de la prochaine ouverture de la solution.

## <a name="see-also"></a>Voir aussi
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts>
- [Solutions](../../extensibility/internals/solutions-overview.md)
