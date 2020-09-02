---
title: Choix du répertoire d’installation d’un VSPackage | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, installation directory
ms.assetid: 01fbbb5b-f747-446c-afe0-2a081626a945
caps.latest.revision: 18
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: c4100c045181f32e51abcc59116a69cad6cc33b5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65697244"
---
# <a name="choosing-the-installation-directory-for-a-vspackage"></a>Choix du répertoire d’installation d’un VSPackage
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Un VSPackage et ses fichiers de prise en charge doivent se trouver dans le système de fichiers d’un utilisateur. L’emplacement varie selon que le VSPackage est géré ou non, à votre schéma de contrôle de version côte à côte et au choix de l’utilisateur.  
  
## <a name="unmanaged-vspackages"></a>VSPackages non managés  
 Un VSPackage non géré est un serveur COM qui peut être installé à n’importe quel emplacement. Ses informations d’inscription doivent refléter précisément son emplacement. L’interface utilisateur de votre programme d’installation doit fournir un emplacement par défaut sous la forme d’un sous-répertoire de la propriété de Windows Installer ProgramFilesFolder. Par exemple :  
  
 ProgramFilesFolder MyCompany\MyVSPackageProduct\V1.0\  
  
 L’utilisateur doit être autorisé à modifier le répertoire par défaut pour prendre en charge les utilisateurs qui conservent une petite partition de démarrage et préfèrent installer des applications et des outils sur un autre volume.  
  
 Si votre schéma côte à côte utilise un VSPackage avec version, vous pouvez utiliser des sous-répertoires pour stocker des versions différentes. Par exemple :  
  
 ProgramFilesFolder MyCompany\MyVSPackageProduct\V1.0\2002\  
  
 ProgramFilesFolder MyCompany\MyVSPackageProduct\V1.0\2003\  
  
 ProgramFilesFolder MyCompany\MyVSPackageProduct\V1.0\2005\  
  
## <a name="managed-vspackages"></a>VSPackages gérés  
 Les VSPackages gérés peuvent également être installés à n’importe quel emplacement. Toutefois, vous devez envisager de toujours les installer dans le Global Assembly Cache (GAC) pour réduire les temps de chargement des assemblys. Étant donné que les VSPackages managés sont toujours des assemblys avec nom fort, leur installation dans le GAC signifie que leur vérification de signature de nom fort prend uniquement au moment de l’installation. Les signatures des assemblys avec nom fort installés ailleurs dans le système de fichiers doivent être vérifiées chaque fois qu’ils sont chargés. Quand vous installez des VSPackages managés dans le GAC, utilisez le commutateur **/assembly** de l’outil regpkg pour écrire des entrées de Registre pointant vers le nom fort de l’assembly.  
  
 Si vous installez les VSPackages gérés dans un autre emplacement que le GAC, suivez les conseils précédents fournis pour les VSPackages non managés pour le choix des hiérarchies de répertoire. Utilisez le commutateur **/codebase** de l’outil regpkg pour écrire des entrées de Registre pointant vers le chemin d’accès de l’assembly VSPackage.  
  
 Pour plus d’informations, consultez [inscription et annulation](../../extensibility/registering-and-unregistering-vspackages.md)de l’inscription de VSPackages.  
  
## <a name="satellite-dlls"></a>DLL satellites  
 Par Convention, les dll satellites du VSPackage, qui contiennent des ressources pour des paramètres régionaux particuliers, se trouvent dans des sous-répertoires du répertoire VSPackage. Les sous-répertoires correspondent aux valeurs d’ID de paramètres régionaux (LCID).  
  
 La [gestion des VSPackages](../../extensibility/managing-vspackages.md) indique que les entrées de Registre contrôlent où [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] recherche la DLL satellite d’un VSPackage. Toutefois, [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] tente de charger une DLL satellite dans un sous-répertoire nommé pour une valeur LCID, dans l’ordre suivant :  
  
1. LCID par défaut (VS LCID par exemple \ 1033 pour l’anglais)  
  
2. LCID par défaut avec la sous-langue par défaut.  
  
3. LCID par défaut du système.  
  
4. LCID par défaut du système avec la sous-langue par défaut.  
  
5. Anglais (États-Unis) (. \ 1033 ou .\0x409).  
  
   Si votre DLL VSPackage contient des ressources et que l’entrée de Registre SatelliteDll\DllName pointe vers celle-ci, [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] tente de les charger dans l’ordre indiqué ci-dessus.  
  
## <a name="see-also"></a>Voir aussi  
 [Choix entre les VSPackages partagés et les VSPackages avec version](../../extensibility/choosing-between-shared-and-versioned-vspackages.md)   
 [Gestion des VSPackages](../../extensibility/managing-vspackages.md)   
 [Inscription du package géré](https://msdn.microsoft.com/f69e0ea3-6a92-4639-8ca9-4c9c210e58a1)
