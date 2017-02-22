---
title: "Choisir le r&#233;pertoire d&#39;Installation pour un VSPackage | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Packages VS, le répertoire d'installation"
ms.assetid: 01fbbb5b-f747-446c-afe0-2a081626a945
caps.latest.revision: 17
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 17
---
# Choisir le r&#233;pertoire d&#39;Installation pour un VSPackage
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Un VSPackage et ses fichiers de prise en charge doivent figurer sur le système de fichiers d'un utilisateur.  L'emplacement varie selon que le VSPackage est managé ou non managé, votre côte à côte modèle de contrôle de version, et choix de l'utilisateur.  
  
## VSPackages non managé  
 un VSPackage non managé est un serveur COM qui peut être installé dans n'importe quel emplacement.  Sa besoin des informations d'inscription précisément son emplacement.  L'interface utilisateur de programme \(UI\) d'installation doit fournir un emplacement par défaut comme sous\-répertoire de la propriété de ProgramFilesFolder Windows Installer.  Par exemple :  
  
 \[ProgramFilesFolder\] MyCompany \\MyVSPackageProduct\\V 1,0 \\  
  
 Doit être autorisé à modifier le répertoire par défaut pour des utilisateurs qui conservent une petite partition de démarrage et la préfèrent installer des applications et des outils sur un autre volume.  
  
 Si votre intriguez côte à côte utilise un VSPackage avec version, vous pouvez utiliser des sous\-répertoires pour stocker des versions différentes.  Par exemple :  
  
 \[ProgramFilesFolder\] MyCompany \\MyVSPackageProduct\\V 1,0 \\ 2002 \\  
  
 \[ProgramFilesFolder\] MyCompany \\MyVSPackageProduct\\V 1,0 \\ 2003 \\  
  
 \[ProgramFilesFolder\] MyCompany \\MyVSPackageProduct\\V 1,0 \\ 2005 \\  
  
## VSPackages managé  
 VSPackages managé peut également être installé dans n'importe quel emplacement.  Toutefois, vous devez envisager de les installer toujours au Global Assembly Cache \(GAC\) pour réduire les temps de chargement de l'assembly.  Étant donné que les VSPackages managé sont toujours les assemblys avec nom fort, l'installer dans le GAC signifient que leur vérification de signature de nom fort dure uniquement au moment de l'installation.  Les assemblys avec nom fort installés ailleurs dans le système de fichiers doivent faire vérifier leurs signatures chaque fois qu'ils sont chargés.  Lorsque vous installez les VSPackages managé dans le GAC, utilisez le commutateur d' **\/assembly** de l'outil de regpkg pour écrire des entrées du Registre qui désigne le nom fort de l'assembly.  
  
 Si vous installez les VSPackages managé dans un emplacement autre que le GAC, suivez le conseil précédemment fourni pour les VSPackages non managé pour choisir des hiérarchies de répertoire.  Utilisez le commutateur d' **\/codebase** de l'outil de regpkg pour écrire des entrées du Registre qui désigne le chemin d'accès de l'assembly d'un VSPackage.  
  
 Pour plus d'informations, consultez [Inscription et annulation de l’enregistrement de packages VS](../../extensibility/registering-and-unregistering-vspackages.md).  
  
## DLL satellite  
 Par convention, DLL satellites d'un VSPackage \- qui contiennent des ressources pour les paramètres régionaux particuliers \- se trouvent dans les sous\-répertoires du répertoire d'un VSPackage.  les sous\-répertoires correspondent aux valeurs d'ID de paramètres régionaux \(LCID\).  
  
 [La gestion de packages VS](../../extensibility/managing-vspackages.md) indique que les entrées du Registre contrôlent où [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] recherche en fait la DLL du satellite d'un VSPackage.  Toutefois, tente de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]pour charger une DLL satellite dans un sous\-répertoire nommé en fonction d'une valeur LCID, dans l'ordre suivant :  
  
1.  La cible par défaut \(LCID VS LCID par exemple \\1033 for English\)  
  
2.  LCID par défaut avec la sous\-langue par défaut.  
  
3.  Valeur par défaut du système LCID.  
  
4.  Valeur par défaut du système LCID avec la sous\-langue par défaut.  
  
5.  États\-Unis  Anglais \(.  \\ 1033 ou.  \\ 0x409\).  
  
 Si votre DLL d'un VSPackage inclut les ressources et les points d'entrée du Registre de SatelliteDll \\DllName à lui, essaie de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]de les charger dans l'ordre ci\-dessus.  
  
## Voir aussi  
 [Choix entre les packages VS partagés et version](../../extensibility/choosing-between-shared-and-versioned-vspackages.md)   
 [La gestion de packages VS](../../extensibility/managing-vspackages.md)   
 [Managed Package Registration](http://msdn.microsoft.com/fr-fr/f69e0ea3-6a92-4639-8ca9-4c9c210e58a1)