---
title: En choisissant le répertoire d’Installation d’un VSPackage | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- VSPackages, installation directory
ms.assetid: 01fbbb5b-f747-446c-afe0-2a081626a945
caps.latest.revision: 18
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 385877b8a682574946bfd43e1e51acd771d00a2b
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51775171"
---
# <a name="choosing-the-installation-directory-for-a-vspackage"></a>Choix du répertoire d’installation d’un VSPackage
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Un VSPackage et ses fichiers de prise en charge doivent être sur le système de fichiers d’un utilisateur. L’emplacement varie selon que le VSPackage est géré ou non gérés, le schéma de contrôle de version côte à côte et de votre choix de l’utilisateur.  
  
## <a name="unmanaged-vspackages"></a>VSPackages non managés  
 Un VSPackage non managé est un serveur COM qui peut être installé dans n’importe quel emplacement. Ses informations d’inscription doit reflète précisément son emplacement. Votre interface utilisateur de programme d’installation (IU) doit fournir un emplacement par défaut en tant que sous-répertoire de la propriété du programme d’installation de Windows de ProgramFilesFolder. Exemple :  
  
 [ProgramFilesFolder] MyCompany\MyVSPackageProduct\V1.0\  
  
 L’utilisateur doit être autorisé à modifier le répertoire par défaut pour les utilisateurs qui en assurent une partition de démarrage de petite et préférez installer les outils et applications sur un autre volume.  
  
 Si votre schéma côte à côte utilise un VSPackage avec contrôle de version, vous pouvez utiliser des sous-répertoires pour stocker différentes versions. Exemple :  
  
 [ProgramFilesFolder] MyCompany\MyVSPackageProduct\V1.0\2002\  
  
 [ProgramFilesFolder] MyCompany\MyVSPackageProduct\V1.0\2003\  
  
 [ProgramFilesFolder] MyCompany\MyVSPackageProduct\V1.0\2005\  
  
## <a name="managed-vspackages"></a>VSPackages gérés  
 VSPackages gérés peuvent également être installés dans n’importe quel emplacement. Toutefois, vous devez envisager de toujours les installer dans le global assembly cache (GAC) afin de réduire le temps de chargement d’assembly. Étant donné que les VSPackages gérés sont toujours des assemblys avec nom fort, leur installation dans le GAC signifie que leur vérification de signature de nom fort prend uniquement au moment de l’installation. Assemblys avec nom fort installés ailleurs dans le système de fichiers doivent avoir leurs signatures vérifiés chaque fois qu’ils sont chargés. Lorsque vous installez les VSPackages gérés dans le GAC, utilisez l’outil regpkg **/assembly** commutateur pour écrire des entrées de Registre qui pointe vers le nom fort de l’assembly.  
  
 Si vous installez les VSPackages gérés dans un emplacement autre que le GAC, suivez les conseils antérieures donnés pour les VSPackages non managés pour le choix des hiérarchies de répertoires. Utilisez l’outil regpkg **/codebase** commutateur pour écrire des entrées de Registre qui pointe vers le chemin d’accès de l’assembly VSPackage.  
  
 Pour plus d’informations, consultez [inscription et annulation de l’inscription de VSPackages](../../extensibility/registering-and-unregistering-vspackages.md).  
  
## <a name="satellite-dlls"></a>DLL satellites  
 Par convention, VSPackage les DLL satellites, qui contiennent des ressources pour les paramètres régionaux spécifiques, se trouvent dans les sous-répertoires du répertoire VSPackage. Les sous-répertoires correspondent aux valeurs d’ID (LCID) de paramètres régionaux.  
  
 [Gestion de VSPackages](../../extensibility/managing-vspackages.md) indique que les entrées de Registre contrôlent où [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] réellement la recherche d’un VSPackage satellites DLL. Toutefois, [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] essaie de charger une DLL satellite dans un sous-répertoire nommé pour une valeur LCID, dans l’ordre suivant :  
  
1. Par défaut LCID (VS LCID par exemple \1033 pour l’anglais)  
  
2. LCID par défaut avec la sous-langue par défaut.  
  
3. Par défaut du système LCID.  
  
4. Système LCID par défaut avec la sous-langue par défaut.  
  
5. ÉTATS-UNIS Anglais (. \1033 ou. \0x409).  
  
   Si votre DLL VSPackage inclut des ressources et les points d’entrée de Registre SatelliteDll\DllName, [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] tente de les charger dans l’ordre indiqué ci-dessus.  
  
## <a name="see-also"></a>Voir aussi  
 [Choix entre les VSPackages partagés et avec contrôle de version](../../extensibility/choosing-between-shared-and-versioned-vspackages.md)   
 [Gestion de VSPackages](../../extensibility/managing-vspackages.md)   
 [Inscription de Package gérée](http://msdn.microsoft.com/en-us/f69e0ea3-6a92-4639-8ca9-4c9c210e58a1)

