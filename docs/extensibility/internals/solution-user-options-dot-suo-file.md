---
title: Options utilisateur de solution (. Fichier suo) | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- .suo files, VSPackages
- suo files, VSPackages
- solutions, .suo files
- solutions, user options
- solution user options (.suo) file
ms.assetid: 75258e0d-600d-4a3d-94f4-3d7ac12cb47c
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: a71f3e14c6a8c87290de2a6204fa28f99a8cabe8
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="solution-user-options-suo-file"></a>Options utilisateur de solution (. Fichier suo)
Le fichier d’options (.suo) de solution utilisateur contient des options de la solution par l’utilisateur. Ce fichier ne doit pas être archivé au contrôle de code source.  
  
 Le fichier d’options (.suo) de solution utilisateur est un stockage structuré ou composée, les fichiers stockés dans un format binaire. Vous enregistrez des informations utilisateur dans le flux de données avec le nom du flux de données en tant que clé qui doit servir à identifier les informations contenues dans le fichier .suo. Le fichier d’options utilisateur solution est utilisé pour stocker les paramètres de préférence utilisateur et est créé automatiquement lorsque Visual Studio enregistre une solution.  
  
 Lorsque l’environnement s’ouvre un fichier .suo, elle énumère toutes les VSPackages actuellement chargés. Si un VSPackage implémente la <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts> interface, puis l’environnement appelle le <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts.LoadUserOptions%2A> méthode sur le VSPackage lui demandant de charger toutes ses données à partir du fichier .suo.  
  
 Il s’agit de responsabilité le VSPackage de savoir ce que le flux peut avoir écrite dans le fichier .suo. Pour chaque flux de données qu’il a écrit, le VSPackage rappelle à l’environnement via <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence.LoadPackageUserOpts%2A> pour charger un flux particulier qui est identifié par la clé, qui est le nom du flux de données. L’environnement puis rappelle le VSPackage pour ce flux de données spécifique en passant le nom du flux de lecture et d’un `IStream` pointeur vers le <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence.LoadPackageUserOpts%2A> (méthode).  
  
 À ce stade, un autre appel est fait à `LoadUserOptions` pour voir s’il existe une autre section du fichier .suo qui doit être lu. Ce processus se poursuit jusqu'à ce que tous les flux de données dans le fichier .suo lus et traités par l’environnement.  
  
 Lorsque la solution est enregistrée ou fermée, l’environnement appelle le <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence.SavePackageSolutionProps%2A> méthode avec un pointeur vers le <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts.SaveUserOptions%2A> (méthode). Un `IStream` contenant les informations binaires à enregistrer est passé à la <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts.WriteUserOptions%2A> (méthode), puis écrit les informations dans le fichier .suo et appelle le `SaveUserOptions` pour voir s’il existe un autre flux d’informations à écrire dans le .suo (méthode) fichier.  
  
 Ces deux méthodes, `SaveUserOptions` et `WriteUserOptions`, sont appelées de manière récursive pour chaque flux d’informations à enregistrer dans le fichier .suo, en passant le pointeur vers `IVsSolutionPersistence`. Ils sont appelés pour permettre l’écriture de plusieurs flux de données dans le fichier .suo de manière récursive. De cette façon, les informations utilisateur sont conservées avec la solution et sont garanties être présent lors de la prochaine ouverture de la solution.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts>   
 [Solutions](../../extensibility/internals/solutions.md)