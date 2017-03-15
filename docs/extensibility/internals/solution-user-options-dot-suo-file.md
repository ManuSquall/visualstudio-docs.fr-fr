---
title: "Options utilisateur de solution (. Fichiers suo) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "fichiers .suo, VSPackages"
  - "fichiers suo, les packages VS"
  - "solutions, fichiers .suo"
  - "solutions, les options de l’utilisateur"
  - "fichier de solution utilisateur options (.suo)"
ms.assetid: 75258e0d-600d-4a3d-94f4-3d7ac12cb47c
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# Options utilisateur de solution (. Fichiers suo)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Le fichier d’options \(.suo\) de solution utilisateur contient des options de solution par utilisateur. Ce fichier ne doit pas être archivé au contrôle de code source.  
  
 Le fichier d’options \(.suo\) de solution utilisateur est un stockage structuré ou composée, fichier stocké dans un format binaire. Vous enregistrez des informations utilisateur dans le flux de données avec le nom du flux de données en tant que clé qui servira à identifier les informations contenues dans le fichier .suo. Le fichier d’options utilisateur solution est utilisé pour stocker des paramètres de préférence utilisateur et est créé automatiquement lorsque Visual Studio enregistre une solution.  
  
 Lorsque l’environnement ouvre un fichier .suo, il énumère tous les packages VS actuellement chargés. Si un VSPackage implémente la <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts> interface, puis l’environnement appelle le <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts.LoadUserOptions%2A> méthode sur le VSPackage lui demandant de charger toutes les données à partir du fichier .suo.  
  
 Il est responsable du VSPackage savoir ce que le flux avez pu écrire dans le fichier .suo. Pour chaque flux qui il a écrit, le VSPackage rappelle à l’environnement via <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence.LoadPackageUserOpts%2A> pour charger un flux particulier qui est identifié par la clé, qui est le nom du flux de données. L’environnement puis rappelle le VSPackage lire ce flux de données particulier en passant le nom du flux de données et un `IStream` pointeur vers le <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence.LoadPackageUserOpts%2A> \(méthode\).  
  
 À ce stade, un autre est appelé `LoadUserOptions` pour voir s’il existe une autre section du fichier .suo qui doit être lu. Ce processus se poursuit jusqu'à ce que tous les flux de données dans le fichier .suo lus et traités par l’environnement.  
  
 Lorsque la solution est enregistrée ou fermée, l’environnement appelle le <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence.SavePackageSolutionProps%2A> méthode avec un pointeur vers le <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts.SaveUserOptions%2A> \(méthode\). Un `IStream` contenant les informations à enregistrer binaire est passé à la <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts.WriteUserOptions%2A> méthode, puis écrit les informations dans le fichier .suo et appelle le `SaveUserOptions` méthode pour vérifier s’il existe un autre flux d’informations à écrire dans le fichier .suo.  
  
 Ces deux méthodes, `SaveUserOptions` et `WriteUserOptions`, sont appelées de manière récursive pour chaque flux d’informations à enregistrer dans le fichier .suo, en passant le pointeur vers `IVsSolutionPersistence`. Elles sont appelées de manière récursive pour permettre l’écriture de plusieurs flux de données dans le fichier .suo. De cette façon, les informations utilisateur sont rendue persistante avec la solution et sont garanties à cet endroit lors de la prochaine ouverture de la solution.  
  
## Voir aussi  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts>   
 [Solutions](../../extensibility/internals/solutions.md)