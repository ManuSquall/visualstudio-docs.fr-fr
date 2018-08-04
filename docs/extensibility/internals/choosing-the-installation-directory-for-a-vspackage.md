---
title: En choisissant le répertoire d’Installation d’un VSPackage | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, installation directory
ms.assetid: 01fbbb5b-f747-446c-afe0-2a081626a945
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 18153e86c75f48b362fc09eddb54ea61263e09e1
ms.sourcegitcommit: 206e738fc45ff8ec4ddac2dd484e5be37192cfbd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/03/2018
ms.locfileid: "39511880"
---
# <a name="choose-the-installation-directory-for-a-vspackage"></a>Choisissez le répertoire d’installation d’un VSPackage
Un VSPackage et ses fichiers de prise en charge doivent être sur le système de fichiers d’un utilisateur. L’emplacement varie selon que le VSPackage est géré ou non gérés, le schéma de contrôle de version côte à côte et de votre choix de l’utilisateur.  
  
## <a name="unmanaged-vspackages"></a>VSPackages non managés  
 Un VSPackage non managé est un serveur COM qui peut être installé dans n’importe quel emplacement. Ses informations d’inscription doivent refléter précisément son emplacement. Votre interface utilisateur de programme d’installation (IU) doit fournir un emplacement par défaut en tant que sous-répertoire de le `ProgramFilesFolder` valeur de propriété de programme d’installation de Windows. Exemple :  
  
*&lt;ProgramFilesFolder&gt;\\&lt;MyCompany&gt;\\&lt;MyVSPackageProduct&gt;\V1.0\\*
  
 L’utilisateur doit être autorisé à modifier le répertoire par défaut pour les utilisateurs qui en assurent une partition de démarrage de petite et préférez installer les outils et applications sur un autre volume.  
  
 Si votre schéma côte à côte utilise un VSPackage avec contrôle de version, vous pouvez utiliser des sous-répertoires pour stocker différentes versions. Exemple :

 *&lt;ProgramFilesFolder&gt;\\&lt;MyCompany&gt;\\&lt;MyVSPackageProduct&gt;\\V1.0\\2002\\*
  
 *&lt;ProgramFilesFolder&gt;\\&lt;MyCompany&gt;\\&lt;MyVSPackageProduct&gt;\\V1.0\\2003\\*
  
 *&lt;ProgramFilesFolder&gt;\\&lt;MyCompany&gt;\\&lt;MyVSPackageProduct&gt;\\V1.0\\2005\\*
  
## <a name="managed-vspackages"></a>VSPackages gérés  
 VSPackages gérés peuvent également être installés dans n’importe quel emplacement. Toutefois, vous devez envisager de toujours les installer dans le global assembly cache (GAC) afin de réduire le temps de chargement d’assembly. Étant donné que les VSPackages gérés sont toujours des assemblys avec nom fort, leur installation dans le GAC signifie que leur vérification de signature de nom fort prend uniquement au moment de l’installation. Assemblys avec nom fort installés ailleurs dans le système de fichiers doivent avoir leurs signatures vérifiés chaque fois qu’ils sont chargés. Lorsque vous installez les VSPackages gérés dans le GAC, utilisez l’outil regpkg **/assembly** commutateur pour écrire des entrées de Registre qui pointe vers le nom fort de l’assembly.  
  
 Si vous installez les VSPackages gérés dans un emplacement autre que le GAC, suivez les conseils antérieures donnés pour les VSPackages non managés pour le choix des hiérarchies de répertoires. Utilisez l’outil regpkg **/codebase** commutateur pour écrire des entrées de Registre qui pointe vers le chemin d’accès de l’assembly VSPackage.  
  
 Pour plus d’informations, consultez [inscrire et désinscrire des VSPackages](../../extensibility/registering-and-unregistering-vspackages.md).  
  
## <a name="satellite-dlls"></a>DLL satellites  
 Par convention, VSPackage DLL contenant des ressources pour les paramètres régionaux particuliers, satellites sont situés dans les sous-répertoires de la *VSPackage* directory. Les sous-répertoires correspondent aux valeurs d’ID (LCID) de paramètres régionaux.  
  
 Le [gérer les VSPackages](../../extensibility/managing-vspackages.md) article indique que les entrées de Registre contrôlent où [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] réellement la recherche d’un VSPackage satellites DLL. Toutefois, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] essaie de charger une DLL satellite dans un sous-répertoire nommé pour une valeur LCID, dans l’ordre suivant :  
  
1.  Par défaut LCID (Visual Studio LCID ; par exemple, *\1033* pour l’anglais)  
  
2.  LCID par défaut avec la sous-langue par défaut.  
  
3.  Par défaut du système LCID.  
  
4.  Système LCID par défaut avec la sous-langue par défaut.  
  
5.  ÉTATS-UNIS Anglais (*. \1033* ou *. \0x409*).  
  

Si votre DLL VSPackage inclut des ressources et le **SatelliteDll\DllName** entrée de Registre pointe vers elle, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] tente de les charger dans l’ordre indiqué ci-dessus.  
  
## <a name="see-also"></a>Voir aussi  
 [Choisissez entre les VSPackages partagés et avec contrôle de version](../../extensibility/choosing-between-shared-and-versioned-vspackages.md)   
 [Gérer les packages VS](../../extensibility/managing-vspackages.md)   
 [Gérer l’inscription du package](http://msdn.microsoft.com/en-us/f69e0ea3-6a92-4639-8ca9-4c9c210e58a1)