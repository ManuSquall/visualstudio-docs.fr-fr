---
title: "Inscription et sélection (Source contrôle VSPackage) | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- registration, source control packages
- source control packages, registration
ms.assetid: 7d21fe48-489a-4f55-acb5-73da64c4e155
caps.latest.revision: 34
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 693955c38d4d53418a92357e54bfc7c2965bdc3e
ms.lasthandoff: 02/22/2017

---
# <a name="registration-and-selection-source-control-vspackage"></a>Inscription et sélection (VSPackage du contrôle de code Source)
Un contrôle de code source VSPackage doit être inscrit pour l’exposer à la [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Si plus d’un contrôle de code source VSPackage est enregistré, l’utilisateur peut sélectionner le VSPackage charger aux moments opportuns. Consultez la page [VSPackages](../../extensibility/internals/vspackages.md) pour plus d’informations sur les VSPackages et comment les enregistrer.  
  
## <a name="registering-a-source-control-package"></a>L’inscription d’un Package de contrôle de code Source  
 Le package de contrôle de code source est enregistré pour que le [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] environnement trouverez il et requête de ses fonctionnalités prises en charge. Il s’agit conformément à un schéma de chargement différé dans lequel une instance d’un package est créée uniquement lorsque ses fonctionnalités ou les commandes requises ou sont explicitement demandés.  
  
 Les VSPackages placer des informations dans une clé de Registre de spécifique à la version HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\\*X.Y*, où *X* est le numéro de version principale et *Y* est le numéro de version secondaire. Cette pratique offre la possibilité de prendre en charge d’installation côte à côte de plusieurs versions de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
 Le [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] l’interface utilisateur (IU) prend en charge la sélection parmi le contrôle de code source installé plusieurs plug-ins (via le Package de l’adaptateur de contrôle Source), ainsi que le contrôle de code source VSPackages. Il peut être uniquement un plug-in de contrôle de code source actif ou VSPackage à la fois. Toutefois, comme décrit ci-dessous, l’IDE permet de basculer entre les plug-ins de contrôle de code source et des VSPackages via un mécanisme package échange automatique sur les solutions. Il existe certaines exigences part du contrôle de code source VSPackage pour activer ce mécanisme de sélection.  
  
### <a name="registry-entries"></a>Entrées de Registre  
 Un package de contrôle de code source a besoin de trois GUID privé :  
  
-   GUID du package : Il s’agit de la principal GUID pour le package qui contient l’implémentation du contrôle de code source (appelée ID_Package dans cette section).  
  
-   Contrôle de code source GUID : Ceci est un GUID pour le contrôle de code source VSPackage pour inscrire dans Visual Studio Source contrôle Stub et est également utilisé comme contexte GUID de l’interface utilisateur de commande. Le service de contrôle source GUID est enregistré sous le contrôle de source de GUID. Dans l’exemple, le GUID du contrôle de code source est appelé ID_SccProvider.  
  
-   GUID du service de contrôle de la source : il s’agit du service privé GUID utilisé par Visual Studio (appelée SID_SccPkgService dans cette section). En outre, le package de contrôle de code source doit définir les autres GUID pour les VSPackages, fenêtres Outil et ainsi de suite.  
  
 Les entrées de Registre suivantes doivent être apportées par un contrôle de source de package VS :  
  
|Nom de la clé|Entrées|  
|--------------|-------------|  
|`HKEY_LOCAL_MACHINE\   SOFTWARE\     Microsoft\       VisualStudio\         X.Y\           SourceControlProviders\`|(par défaut) = rg_sz : {ID_SccProvider}|  
|`HKEY_LOCAL_MACHINE\   SOFTWARE\     Microsoft\       VisualStudio\         X.Y\           SourceControlProviders\             {ID_SccProvider}\`|(par défaut) = rg_sz :\<nom convivial du Package ><br /><br /> Service = rg_sz : {SID_SccPkgService}|  
|`HKEY_LOCAL_MACHINE\   SOFTWARE\     Microsoft\       VisualStudio\         X.Y\           SourceControlProviders\             {ID_SccProvider}\               Name\`|(par défaut) = rg_sz : #\<ID de ressource pour le nom localisé ><br /><br /> Package = rg_sz : {ID_Package}|  
|`HKEY_LOCAL_MACHINE\   SOFTWARE\     Microsoft\       VisualStudio\         X.Y\           SolutionPersistence\             <PackageName>\`<br /><br /> (Notez que le nom de la clé `SourceCodeControl`, est déjà utilisé par [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] et n’est pas disponible comme un choix pour \<PackageName >.)|(par défaut) = rg_sz : {ID_Package}|  
  
## <a name="selecting-a-source-control-package"></a>Sélection d’un Package de contrôle de code Source  
 Plusieurs basés sur les API de plug-in de contrôle de Source de plug-ins et les VSPackages peuvent être enregistrés simultanément un contrôle de code source. Le processus de sélection d’un plug-in de contrôle de code source ou un VSPackage doit s’assurer que [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] charge le plug-in ou VSPackage au moment opportun et peut différer le chargement des composants inutiles jusqu'à ce qu’ils sont requis. En outre, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] doit supprimer l’interface utilisateur à partir d’autres packages VS inactives, y compris les éléments de menu, les boîtes de dialogue et les barres d’outils et afficher l’interface utilisateur pour le VSPackage actif.  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]charge un contrôle de code source VSPackage lors de l’une des opérations suivantes :  
  
-   Solution est ouverte (lorsque la solution est sous contrôle de code source).  
  
     Ouverture d’une solution ou un projet sous contrôle de code source, l’IDE, le contrôle de source VSPackage qui a été désignée pour cette solution doit être chargé.  
  
-   Les commandes de menu du contrôle source VSPackage sont exécutées.  
  
 Un contrôle de code source que VSPackage doit charger tous les composants dont il a besoin uniquement lorsqu’ils vont en fait être utilisé (autrement dit le chargement différé).  
  
### <a name="automatic-solution-based-vspackage-swapping"></a>Échange automatique VSPackage basée sur la Solution  
 Vous pouvez basculer manuellement de contrôle de code source VSPackages via la [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] **Options** boîte de dialogue sous la **contrôle de code Source** catégorie. Le remplacement automatique des packages sur les solutions signifie qu’un package de contrôle de code source qui a été désigné pour une solution spécifique est automatiquement définir actif lors de cette solution est ouverte. Chaque package de contrôle de code source doit implémenter <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider.SetActive%2A>et <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider.SetInactive%2A>.</xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider.SetInactive%2A> </xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider.SetActive%2A> [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]gère le basculement entre les deux plug-ins de contrôle (l’implémentation de l’API de plug-in de contrôle de Source) de la source et les VSPackages de contrôle de code source.  
  
 Le Package de l’adaptateur de contrôle Source est utilisé pour basculer sur les API de plug-in de contrôle de Source de plug-in. Le processus de basculement vers le Package d’adaptateur de contrôle Source intermédiaire et de déterminer quel plug-in de contrôle de code source doit être défini active ou inactive est transparente pour l’utilisateur. Le Package de l’adaptateur est toujours actif lorsque tout plug-in de contrôle de code source est active. Basculement entre deux quantités de plug-ins de contrôle de source simplement le chargement et déchargement de la DLL de plug-in. Passer à un contrôle de code source VSPackage, toutefois, implique interagir avec l’IDE pour charger le VSPackage approprié.  
  
 Un contrôle de code source VSPackage est appelé lorsqu’une solution est ouverte et la clé de Registre pour le VSPackage est dans le fichier solution. Lorsque la solution est ouverte, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] détecte que la valeur de Registre et charge le contrôle de code source appropriée VSPackage. Contrôle de source de tous les packages VS doit avoir les entrées de Registre décrites ci-dessus. Une solution sous contrôle de code source est marquée comme étant associé à un contrôle de code source particulier VSPackage. Les VSPackages doit implémenter un contrôle de code source du <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence>pour activer le basée sur une solution VSPackage remplacement automatique.</xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence>  
  
### <a name="visual-studio-ui-for-package-selection-and-switching"></a>L’interface utilisateur de sélection du Package et le changement de Visual Studio  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]Fournit une interface utilisateur pour le contrôle de code source VSPackage et la sélection du plug-in dans le **Options** boîte de dialogue sous la **contrôle de code Source** catégorie. Il permet à l’utilisateur de sélectionner le plug-in de contrôle de source active ou un VSPackage. Une liste déroulante inclut :  
  
-   Tous les packages de contrôle de code source installé  
  
-   Tous les plug-ins de contrôle de code source installé  
  
-   « none » plutôt que l’option qui désactive le contrôle de code source  
  
 Uniquement l’interface utilisateur pour le choix du contrôle source active est visible. La sélection VSPackage masque l’interface utilisateur pour le VSPackage précédent et affiche l’interface utilisateur pour une nouvelle. Le VSPackage actif est sélectionné sur une base par utilisateur. Si un utilisateur possède plusieurs copies de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ouverts simultanément, chacune d’elles peut utiliser un VSPackage Directory différents. Si plusieurs utilisateurs sont connectés au même ordinateur, chaque utilisateur peut avoir des instances distinctes de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ouvrir, chacun avec un VSPackage Directory différents. Lorsque plusieurs instances de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] sont fermés par un utilisateur, le contrôle de code source VSPackage qui était actif pour la dernière solution ouverte devienne le contrôle de code source par défaut VSPackage, à définir actif lors du redémarrage.  
  
 Contrairement aux versions précédentes de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], un redémarrage de l’IDE n’est plus la seule façon de basculer le contrôle de code source VSPackages. Sélection de VSPackage est automatique. Basculement de packages nécessite des privilèges d’utilisateur Windows (non administrateur ou utilisateur avec pouvoir).  
  
## <a name="see-also"></a>Voir aussi  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence></xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence>   
 [Fonctionnalités](../../extensibility/internals/source-control-vspackage-features.md)   
 [Création d’un contrôle de Source de plug-in](../../extensibility/internals/creating-a-source-control-plug-in.md)   
 [Packages VS](../../extensibility/internals/vspackages.md)
