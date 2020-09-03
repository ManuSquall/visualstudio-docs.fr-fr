---
title: Inscription et sélection (VSPackage de contrôle de code source) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- registration, source control packages
- source control packages, registration
ms.assetid: 7d21fe48-489a-4f55-acb5-73da64c4e155
caps.latest.revision: 35
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 692f2a9f34edd41839179f7229e079ec8e791800
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68185821"
---
# <a name="registration-and-selection-source-control-vspackage"></a>Inscription et sélection (VSPackage de contrôle de code source)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Un VSPackage de contrôle de code source doit être inscrit pour l’exposer à [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] . Si plus d’un VSPackage de contrôle de code source est inscrit, l’utilisateur peut sélectionner le VSPackage à charger aux moments opportuns. Pour plus d’informations sur les VSPackages et sur la manière de les inscrire, consultez [VSPackages](../../extensibility/internals/vspackages.md) .  
  
## <a name="registering-a-source-control-package"></a>Inscription d’un package de contrôle de code source  
 Le package de contrôle de code source est inscrit afin que l' [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] environnement puisse le trouver et rechercher les fonctionnalités prises en charge. Cela est conforme à un schéma de chargement différé dans lequel une instance d’un package est créée uniquement lorsque ses fonctionnalités ou commandes sont requises ou demandées de manière explicite.  
  
 Les VSPackages placent les informations dans une clé de Registre spécifique à la version, HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft\VisualStudio \\ *x. Y*, où *X* est le numéro de version principale et *Y* le numéro de version secondaire. Cette pratique offre la possibilité de prendre en charge l’installation côte à côte de plusieurs versions de [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] .  
  
 L' [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] interface utilisateur prend en charge la sélection parmi plusieurs plug-ins de contrôle de code source installés (via le package de l’adaptateur de contrôle de code source), ainsi que les VSPackages de contrôle de code source. Il ne peut y avoir qu’un seul plug-in ou VSPackage de contrôle de code source actif à la fois. Toutefois, comme décrit ci-dessous, l’IDE permet de basculer entre les plug-ins de contrôle de code source et les VSPackages via un mécanisme de permutation automatique basé sur une solution. Certaines conditions sont requises sur la partie du VSPackage de contrôle de code source pour activer ce mécanisme de sélection.  
  
### <a name="registry-entries"></a>Entrées de Registre  
 Un package de contrôle de code source a besoin de trois GUID privés :  
  
- GUID du package : il s’agit du GUID principal du package qui contient l’implémentation du contrôle de code source (appelée ID_Package dans cette section).  
  
- GUID du contrôle de code source : il s’agit d’un GUID pour le VSPackage de contrôle de code source utilisé pour l’inscription auprès du stub de contrôle de code source Visual Studio. il est également utilisé comme GUID de contexte d’interface utilisateur de commande. Le GUID du service de contrôle de code source est inscrit sous le GUID du contrôle de code source. Dans l’exemple, le GUID du contrôle de code source est appelé ID_SccProvider.  
  
- GUID du service de contrôle de code source : il s’agit du GUID du service privé utilisé par Visual Studio (appelé SID_SccPkgService dans cette section). En outre, le package de contrôle de code source doit définir d’autres GUID pour les VSPackages, les fenêtres outil, etc.  
  
  Les entrées de Registre suivantes doivent être effectuées par un VSPackage de contrôle de code source :  
  
|Nom de clé|Écritures|  
|--------------|-------------|  
|`HKEY_LOCAL_MACHINE\   SOFTWARE\     Microsoft\       VisualStudio\         X.Y\           SourceControlProviders\`|(par défaut) = rg_sz : {ID_SccProvider}|  
|`HKEY_LOCAL_MACHINE\   SOFTWARE\     Microsoft\       VisualStudio\         X.Y\           SourceControlProviders\             {ID_SccProvider}\`|(par défaut) = rg_sz :\<Friendly name of Package><br /><br /> Service = rg_sz : {SID_SccPkgService}|  
|`HKEY_LOCAL_MACHINE\   SOFTWARE\     Microsoft\       VisualStudio\         X.Y\           SourceControlProviders\             {ID_SccProvider}\               Name\`|(par défaut) = rg_sz : #\<Resource ID for localized name><br /><br /> Package = rg_sz : {ID_Package}|  
|`HKEY_LOCAL_MACHINE\   SOFTWARE\     Microsoft\       VisualStudio\         X.Y\           SolutionPersistence\             <PackageName>\`<br /><br /> (Notez que le nom de clé, `SourceCodeControl` , est déjà utilisé par [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] et n’est pas disponible en tant que choix pour \<PackageName> .)|(par défaut) = rg_sz : {ID_Package}|  
  
## <a name="selecting-a-source-control-package"></a>Sélection d’un package de contrôle de code source  
 Plusieurs plug-ins basés sur des API de plug-in de contrôle de code source et packages de contrôle de code source peuvent être inscrits simultanément. Le processus de sélection d’un plug-in ou d’un VSPackage de contrôle de code source doit garantir le chargement [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] du plug-in ou du VSPackage au moment opportun et peut différer le chargement des composants inutiles jusqu’à ce qu’ils soient nécessaires. En outre, [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] doit supprimer toute l’interface utilisateur d’autres VSPackages inactifs, y compris les éléments de menu, les boîtes de dialogue et les barres d’outils, et afficher l’interface utilisateur du VSPackage actif.  
  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] charge un VSPackage de contrôle de code source lors de l’exécution de l’une des opérations suivantes :  
  
- La solution est ouverte (lorsque la solution est sous contrôle de code source).  
  
   Lorsqu’une solution ou un projet sous contrôle de code source est ouvert, l’IDE entraîne le chargement du VSPackage de contrôle de code source désigné pour cette solution.  
  
- Toutes les commandes de menu du VSPackage de contrôle de code source sont exécutées.  
  
  Un VSPackage de contrôle de code source doit charger tous les composants dont il a besoin uniquement lorsqu’ils vont être utilisés en fait (également appelés chargement différé).  
  
### <a name="automatic-solution-based-vspackage-swapping"></a>Échange de VSPackages automatisés basés sur une solution  
 Vous pouvez échanger manuellement les VSPackages de contrôle de code source via la [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] boîte de dialogue **options** sous la catégorie **contrôle de code source** . L’échange automatique de packages basé sur une solution signifie qu’un package de contrôle de code source qui a été désigné pour une solution particulière est automatiquement défini sur actif lorsque cette solution est ouverte. Chaque package de contrôle de code source doit implémenter <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider.SetActive%2A> et <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider.SetInactive%2A> . [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] gère le basculement entre les deux plug-ins de contrôle de code source (implémentation de l’API de plug-in de contrôle de code source) et les VSPackages de contrôle de code source.  
  
 Le package de l’adaptateur de contrôle de code source est utilisé pour basculer vers n’importe quel plug-in basé sur une API de plug-in de contrôle de code source. Le processus de basculement vers le package d’adaptateur de contrôle de code source intermédiaire et de déterminer quel plug-in de contrôle de code source doit être défini sur actif ou inactif est transparent pour l’utilisateur. Le package d’adaptateur est toujours actif quand un plug-in de contrôle de code source est actif. Le basculement entre deux plug-ins de contrôle de code source permet simplement de charger et de décharger la DLL du plug-in. Toutefois, le basculement vers un VSPackage de contrôle de code source implique l’interaction avec l’IDE pour charger le VSPackage approprié.  
  
 Un VSPackage de contrôle de code source est appelé quand une solution est ouverte et que la clé de Registre du VSPackage se trouve dans le fichier solution. Lorsque la solution est ouverte, [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] recherche la valeur de Registre et charge le VSPackage de contrôle de code source approprié. Tous les VSPackages de contrôle de code source doivent avoir les entrées de Registre décrites ci-dessus. Une solution sous contrôle de code source est marquée comme étant associée à un VSPackage de contrôle de code source particulier. Les VSPackages de contrôle de code source doivent implémenter le <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence> pour activer l’échange VSPackage automatique basé sur une solution.  
  
### <a name="visual-studio-ui-for-package-selection-and-switching"></a>Interface utilisateur de Visual Studio pour la sélection et le changement de packages  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] fournit une interface utilisateur pour la sélection du plug-in et du plug-in de contrôle de code source dans la boîte de dialogue **options** sous la catégorie **contrôle de code source** . Il permet à l’utilisateur de sélectionner le plug-in de contrôle de code source actif ou le VSPackage. Une liste déroulante comprend les éléments suivants :  
  
- Tous les packages de contrôle de code source installés  
  
- Tous les plug-ins de contrôle de code source installés  
  
- Une option « None », qui désactive le contrôle de code source  
  
  Seule l’interface utilisateur pour le choix du contrôle de code source actif est visible. La sélection VSPackage masque l’interface utilisateur pour le VSPackage précédent et affiche l’interface utilisateur pour la nouvelle. Le VSPackage actif est sélectionné pour chaque utilisateur. Si plusieurs copies d’un utilisateur sont [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] ouvertes simultanément, chacune d’elles peut utiliser un VSPackage actif différent. Si plusieurs utilisateurs sont connectés au même ordinateur, chaque utilisateur peut avoir des instances de ouvertes distinctes [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] , chacune avec un VSPackage actif différent. Lorsque plusieurs instances de [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] sont fermées par un utilisateur, le VSPackage de contrôle de code source qui était actif pour la dernière solution ouverte devient le VSPackage de contrôle de code source par défaut, qui doit être défini sur actif au redémarrage.  
  
  Contrairement aux versions précédentes de [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] , un redémarrage de l’IDE n’est plus le seul moyen de basculer les VSPackages de contrôle de code source. La sélection du VSPackage est automatique. Le changement de packages requiert des privilèges d’utilisateur Windows (et non un administrateur ou un utilisateur avec pouvoir).  
  
## <a name="see-also"></a>Voir aussi  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence>   
 [Éléments](../../extensibility/internals/source-control-vspackage-features.md)   
 [Création d’un plug-in de contrôle de code source](../../extensibility/internals/creating-a-source-control-plug-in.md)   
 [VSPackages](../../extensibility/internals/vspackages.md)
