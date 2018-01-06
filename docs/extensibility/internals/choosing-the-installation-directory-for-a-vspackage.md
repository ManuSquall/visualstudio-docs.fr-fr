---
title: "En choisissant le répertoire d’Installation pour un VSPackage | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: VSPackages, installation directory
ms.assetid: 01fbbb5b-f747-446c-afe0-2a081626a945
caps.latest.revision: "17"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 085c3bea9b9edc726fa09dd5d7658aff4a55e568
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="choosing-the-installation-directory-for-a-vspackage"></a>En choisissant le répertoire d’Installation pour un VSPackage
Un VSPackage et ses fichiers de prise en charge doivent être sur le système de fichiers d’un utilisateur. L’emplacement varie selon que le VSPackage est géré ou non managé, le schéma de contrôle de version côte à côte et de votre choix de l’utilisateur.  
  
## <a name="unmanaged-vspackages"></a>VSPackages non managés  
 Un VSPackage non managé est un serveur COM qui peut être installé dans n’importe quel emplacement. Informations d’enregistrement doit reflète précisément son emplacement. Votre interface utilisateur (IU) du installer doit fournir un emplacement par défaut comme un sous-répertoire de la propriété ProgramFilesFolder Windows Installer. Exemple :  
  
 [ProgramFilesFolder] MyCompany\MyVSPackageProduct\V1.0\  
  
 L’utilisateur doit être autorisé à modifier le répertoire par défaut pour les utilisateurs qui conservent une partition de démarrage de petits et préférez installer les outils et applications sur un autre volume.  
  
 Si votre schéma côte-à-côte utilise un contrôle de version du VSPackage, vous pouvez utiliser dans les sous-répertoires pour stocker des versions différentes. Exemple :  
  
 [ProgramFilesFolder] MyCompany\MyVSPackageProduct\V1.0\2002\  
  
 [ProgramFilesFolder] MyCompany\MyVSPackageProduct\V1.0\2003\  
  
 [ProgramFilesFolder] MyCompany\MyVSPackageProduct\V1.0\2005\  
  
## <a name="managed-vspackages"></a>VSPackages gérés  
 VSPackages gérés peuvent également être installés dans n’importe quel emplacement. Toutefois, vous devez envisager de les installer toujours dans le global assembly cache (GAC) afin de réduire le temps de chargement d’assembly. Étant donné que les VSPackages gérés sont toujours des assemblys avec nom fort, leur installation dans le GAC signifie que leur vérification de signature de nom fort prend uniquement au moment de l’installation. Assemblys avec nom fort installés ailleurs dans le système de fichiers doivent avoir leurs signatures vérifiés chaque fois qu’ils sont chargés. Lorsque vous installez les VSPackages gérés dans le GAC, utilisez l’outil regpkg **/assembly** commutateur pour écrire des entrées de Registre pointant vers le nom fort de l’assembly.  
  
 Si vous installez les VSPackages gérés dans un emplacement autre que le GAC, suivez les conseils d’antérieures donnés pour les VSPackages non managés pour le choix des hiérarchies de répertoires. Utilisez l’outil regpkg **/ codebase** commutateur pour écrire des entrées de Registre pointant vers le chemin d’accès de l’assembly VSPackage.  
  
 Pour plus d’informations, consultez [inscription et annulation de l’inscription de VSPackages](../../extensibility/registering-and-unregistering-vspackages.md).  
  
## <a name="satellite-dlls"></a>DLL satellites  
 Par convention, VSPackage les DLL satellites, qui contiennent des ressources pour une langue particulière, se trouvent dans les sous-répertoires du répertoire VSPackage. Les sous-répertoires correspondent aux valeurs de paramètres régionaux (LCID) de code.  
  
 [Gestion des VSPackages](../../extensibility/managing-vspackages.md) indique que les entrées de Registre contrôlent where [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] réellement la recherche d’un VSPackage satellite DLL. Toutefois, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] essaie de charger une DLL satellite dans un sous-répertoire nommé pour une valeur LCID, dans l’ordre suivant :  
  
1.  La valeur par défaut LCID (VS LCID par exemple \1033 pour l’anglais)  
  
2.  LCID par défaut avec la sous-langue par défaut.  
  
3.  Système LCID par défaut.  
  
4.  Système LCID par défaut avec la sous-langue par défaut.  
  
5.  ÉTATS-UNIS Anglais (. \1033 ou. \0x409).  
  
 Si votre DLL VSPackage inclut les ressources et les points d’entrée de Registre SatelliteDll\DllName, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] tente de les charger dans l’ordre indiqué ci-dessus.  
  
## <a name="see-also"></a>Voir aussi  
 [Choix entre les VSPackages partagés et version](../../extensibility/choosing-between-shared-and-versioned-vspackages.md)   
 [Gestion des VSPackages](../../extensibility/managing-vspackages.md)   
 [Inscription de Package gérée](http://msdn.microsoft.com/en-us/f69e0ea3-6a92-4639-8ca9-4c9c210e58a1)