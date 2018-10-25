---
title: Inscription et sélection (VSPackage de contrôle de code Source) | Microsoft Docs
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
- registration, source control packages
- source control packages, registration
ms.assetid: 7d21fe48-489a-4f55-acb5-73da64c4e155
caps.latest.revision: 35
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 7bf98c263f3452e0383f5891116849e85140b763
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49818757"
---
# <a name="registration-and-selection-source-control-vspackage"></a>Inscription et sélection (VSPackage de contrôle de code source)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Un contrôle de code source VSPackage doit être inscrite pour l’exposer à la [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]. Si le contrôle de code source plus d’un VSPackage est inscrit, l’utilisateur peut sélectionner le VSPackage à charger aux moments opportuns. Consultez [VSPackages](../../extensibility/internals/vspackages.md) pour plus d’informations sur les VSPackages et comment les enregistrer.  
  
## <a name="registering-a-source-control-package"></a>L’inscription d’un Package de contrôle de code Source  
 Le package de contrôle de code source est inscrit pour que le [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] environnement trouverez il et requête de ses fonctionnalités prises en charge. Il s’agit conformément à un schéma de chargement différé dans lequel une instance d’un package est créée uniquement lorsque ses fonctionnalités ou les commandes sont nécessaires ou sont explicitement demandés.  
  
 VSPackages placer des informations dans une clé de Registre spécifiques à la version, HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\\*X.Y*, où *X* est le numéro de version principale et *Y* est le numéro de version mineure. Cette pratique offre la possibilité de prendre en charge d’installation côte à côte de plusieurs versions de [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].  
  
 Le [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] l’interface utilisateur (IU) prend en charge la sélection parmi le contrôle de code source installé plusieurs plug-ins (via le Package de l’adaptateur de contrôle de code Source), ainsi que le contrôle de code source VSPackages. Il peut y avoir qu’un seul plug-in de contrôle de code source actif ou VSPackage à la fois. Toutefois, comme décrit ci-dessous, l’IDE permet de basculer entre les plug-ins de contrôle de code source et des VSPackages via un mécanisme automatique le remplacement de package de solution basée. Il existe certaines exigences part le VSPackage de contrôle de code source pour activer ce mécanisme de sélection.  
  
### <a name="registry-entries"></a>Entrées de Registre  
 Un package de contrôle de code source a besoin de trois GUID privé :  
  
- GUID du package : Il s’agit de la principal GUID pour le package qui contient l’implémentation du contrôle de source (appelée ID_Package dans cette section).  
  
- GUID du contrôle source : Ceci est un GUID pour le contrôle de code source VSPackage permet d’enregistrer avec le Stub de contrôle de Source de Visual Studio et est également utilisé comme contexte GUID de l’interface utilisateur de commande. Le GUID du service de contrôle de source est enregistré sous le GUID du contrôle de code source. Dans l’exemple, le GUID du contrôle de code source est appelé ID_SccProvider.  
  
- GUID du service de contrôle de source : il s’agit du service privé GUID utilisé par Visual Studio (appelé SID_SccPkgService dans cette section). En outre, le package de contrôle de code source doit définir d’autres GUID pour les VSPackages, fenêtres Outil et ainsi de suite.  
  
  Les entrées de Registre suivantes doivent être apportées par un VSPackage de contrôle de code source :  
  
|Nom de la clé|Entrées|  
|--------------|-------------|  
|`HKEY_LOCAL_MACHINE\   SOFTWARE\     Microsoft\       VisualStudio\         X.Y\           SourceControlProviders\`|(valeur par défaut) = rg_sz : {ID_SccProvider}|  
|`HKEY_LOCAL_MACHINE\   SOFTWARE\     Microsoft\       VisualStudio\         X.Y\           SourceControlProviders\             {ID_SccProvider}\`|(valeur par défaut) = rg_sz :\<nom convivial du Package ><br /><br /> Service = rg_sz : {SID_SccPkgService}|  
|`HKEY_LOCAL_MACHINE\   SOFTWARE\     Microsoft\       VisualStudio\         X.Y\           SourceControlProviders\             {ID_SccProvider}\               Name\`|(valeur par défaut) = rg_sz : #\<ID de ressource pour le nom localisé ><br /><br /> Package = rg_sz : {ID_Package}|  
|`HKEY_LOCAL_MACHINE\   SOFTWARE\     Microsoft\       VisualStudio\         X.Y\           SolutionPersistence\             <PackageName>\`<br /><br /> (Notez que le nom de clé, `SourceCodeControl`, est déjà utilisé par [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] et n’est pas disponible comme un choix pour \<PackageName >.)|(valeur par défaut) = rg_sz : {ID_Package}|  
  
## <a name="selecting-a-source-control-package"></a>Sélection d’un Package de contrôle de code Source  
 Plusieurs basée sur les API de plug-in de contrôle de Source de plug-ins et les VSPackages peuvent être inscrits simultanément de contrôle de code source. Le processus de sélection d’un plug-in de contrôle de code source ou d’un VSPackage doit s’assurer que [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] charge le plug-in ou VSPackage au moment opportun et peut différer le chargement des composants inutiles jusqu'à ce qu’ils sont requis. En outre, [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] doit supprimer toute l’interface utilisateur à partir d’autres packages VS inactive, y compris les éléments de menu, les boîtes de dialogue et les barres d’outils et afficher l’interface utilisateur pour le VSPackage actif.  
  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] charge un VSPackage de contrôle de code source lors de l’une des opérations suivantes :  
  
- Solution est ouverte (lorsque la solution est sous contrôle de code source).  
  
   Ouverture d’une solution ou un projet sous contrôle de code source, l’IDE, le contrôle de source VSPackage qui a été indiqué pour cette solution à charger.  
  
- Les commandes de menu du contrôle source VSPackage sont exécutées.  
  
  Un contrôle de code source que VSPackage doit se charger tous les composants dont il a besoin uniquement lorsqu’elles entrent en fait être utilisé (autrement dit le chargement différé).  
  
### <a name="automatic-solution-based-vspackage-swapping"></a>Le remplacement automatique VSPackage basé sur la Solution  
 Vous pouvez échanger manuellement le contrôle de code source VSPackages via le [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] **Options** boîte de dialogue sous la **contrôle de code Source** catégorie. Le remplacement automatique des packages à la solution signifie qu’un package de contrôle de code source qui a été désigné pour une solution particulière est automatiquement défini en mode actif lorsque cette solution est ouvert. Chaque package de contrôle de code source doit implémenter <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider.SetActive%2A> et <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider.SetInactive%2A>. [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] gère le basculement entre les deux plug-ins de contrôle (implémentation de l’API de plug-in de contrôle de Source) de la source et de VSPackages de contrôle de code source.  
  
 Le Package de l’adaptateur de contrôle de code Source est utilisé pour basculer vers toute API de plug-in de contrôle de Source de plug-in. Le processus de basculement pour le Package de l’adaptateur de contrôle Source intermédiaire et de déterminer quel plug-in de contrôle de code source doit être défini sur actif ou inactif est transparent pour l’utilisateur. Le Package de l’adaptateur est toujours actif lorsque n’importe quel plug-in de contrôle de code source est active. Le basculement entre deux quantités de plug-ins de contrôle de source simplement le chargement et déchargement de la DLL de plug-in. Passage à un VSPackage de contrôle de code source, toutefois, implique interagir avec l’IDE à charger le VSPackage approprié.  
  
 Un contrôle de code source VSPackage est appelé lorsqu’une solution est ouvert et la clé de Registre pour le VSPackage est dans le fichier solution. Lorsque la solution est ouverte, [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] recherche la valeur de Registre et charge le contrôle de code source appropriée VSPackage. Contrôle de source de tous les VSPackages doit avoir les entrées de Registre décrites ci-dessus. Une solution est sous contrôle de code source est marquée comme étant associée à un contrôle de code source particulier VSPackage. Les VSPackages doivent implémenter de contrôle de code source le <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence> pour activer le basée sur une solution VSPackage remplacement automatique.  
  
### <a name="visual-studio-ui-for-package-selection-and-switching"></a>L’interface utilisateur de sélection du Package et le changement de Visual Studio  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Fournit une interface utilisateur pour le contrôle de code source VSPackage et la sélection du plug-in dans le **Options** boîte de dialogue sous la **contrôle de code Source** catégorie. Il permet à l’utilisateur de sélectionner le plug-in de contrôle de code source actif ou d’un VSPackage. Une liste déroulante inclut :  
  
- Tous les packages de contrôle de code source installé  
  
- Tous les plug-ins de contrôle de code source installé  
  
- Une option « Aucun », qui désactive le contrôle de code source  
  
  Uniquement l’interface utilisateur pour le choix de contrôle source active est visible. La sélection de VSPackage masque l’interface utilisateur pour le VSPackage précédent et affiche l’interface utilisateur pour une nouvelle. Le VSPackage actif est sélectionné par l’utilisateur. Si un utilisateur a plusieurs copies de [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] ouverts simultanément, chacune d’elles peut utiliser un VSPackage actif différents. Si plusieurs utilisateurs sont connectés au même ordinateur, chaque utilisateur peut avoir des instances distinctes de [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] ouvrir, chacun avec un VSPackage actif différents. Lorsque plusieurs instances de [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] sont fermés par un utilisateur, le VSPackage qui était actif pour la dernière solution ouverte devienne le contrôle de code source par défaut VSPackage, à définir actif lors du redémarrage du contrôle de code source.  
  
  Contrairement aux versions précédentes de [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)], un redémarrage de l’IDE n’est plus la seule façon de basculer le contrôle de code source VSPackages. Sélection de VSPackage est automatique. Changement de packages nécessite des privilèges d’utilisateur de Windows (pas un administrateur ou utilisateur avec pouvoir).  
  
## <a name="see-also"></a>Voir aussi  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence>   
 [Fonctionnalités](../../extensibility/internals/source-control-vspackage-features.md)   
 [Création d’un contrôle de Source de plug-in](../../extensibility/internals/creating-a-source-control-plug-in.md)   
 [VSPackages](../../extensibility/internals/vspackages.md)

