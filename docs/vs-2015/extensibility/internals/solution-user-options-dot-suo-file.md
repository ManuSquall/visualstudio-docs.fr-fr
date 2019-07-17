---
title: Options utilisateur de solution (. Fichier suo) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- .suo files, VSPackages
- suo files, VSPackages
- solutions, .suo files
- solutions, user options
- solution user options (.suo) file
ms.assetid: 75258e0d-600d-4a3d-94f4-3d7ac12cb47c
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 1a9825fabe08940e8950cf88a1dbf2bc149af0b2
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68197334"
---
# <a name="solution-user-options-suo-file"></a>Fichiers des options utilisateur de solution (.Suo)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Le fichier d’options (.suo) de solution utilisateur contient des options de la solution par l’utilisateur. Ce fichier ne doit pas être archivé au contrôle de code source.  
  
 Fichier des options (.suo) solution utilisateur soit un stockage structuré, composé, par fichier stocké dans un format binaire. Vous enregistrez des informations utilisateur dans le flux de données avec le nom du flux de données en cours de la clé qui servira à identifier les informations contenues dans le fichier .suo. Le fichier d’options utilisateur solution est utilisé pour stocker les paramètres de préférence utilisateur et est créé automatiquement lorsque Visual Studio enregistre une solution.  
  
 Lorsque l’environnement s’ouvre un fichier .suo, elle énumère tous les VSPackages actuellement chargés. Si un VSPackage implémente le <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts> interface, puis l’environnement appelle le <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts.LoadUserOptions%2A> méthode sur le VSPackage lui demandant de charger toutes ses données à partir du fichier .suo.  
  
 Il est responsable du VSPackage savoir ce que le flux avez pu écrire dans le fichier .suo. Pour chaque flux qui il a écrit, le VSPackage rappelle à l’environnement via <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence.LoadPackageUserOpts%2A> pour charger un flux particulier qui est identifié par la clé, qui est le nom du flux. L’environnement rappelle ensuite au VSPackage pour lire ce flux de données particulier en passant le nom du flux de données et un `IStream` pointeur vers le <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence.LoadPackageUserOpts%2A> (méthode).  
  
 À ce stade, un autre est appelé `LoadUserOptions` pour voir s’il existe une autre section du fichier .suo qui dispose être lues. Ce processus se poursuit jusqu'à ce que tous les flux de données dans le fichier .suo ont été lues et traitées par l’environnement.  
  
 Lorsque la solution est enregistrée ou fermée, l’environnement appelle le <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence.SavePackageSolutionProps%2A> méthode avec un pointeur vers le <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts.SaveUserOptions%2A> (méthode). Un `IStream` contenant les informations binaires à enregistrer est passé à la <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts.WriteUserOptions%2A> (méthode), puis écrit les informations sur le fichier .suo et appelle le `SaveUserOptions` à nouveau pour voir s’il existe un autre flux d’informations à écrire dans le .suo (méthode) fichier.  
  
 Ces deux méthodes, `SaveUserOptions` et `WriteUserOptions`, sont appelées de manière récursive pour chaque flux d’informations à enregistrer dans le fichier .suo, en passant le pointeur à `IVsSolutionPersistence`. Elles sont appelées de manière récursive pour permettre l’écriture de plusieurs flux de données dans le fichier .suo. De cette façon, les informations utilisateur sont rendue persistante avec la solution et sont garanties à cet emplacement la prochaine ouverture de la solution.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts>   
 [Solutions](../../extensibility/internals/solutions-overview.md)
