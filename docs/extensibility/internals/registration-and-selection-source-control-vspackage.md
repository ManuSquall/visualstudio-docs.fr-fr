---
title: Inscription et sélection (Source Control VSPackage) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- registration, source control packages
- source control packages, registration
ms.assetid: 7d21fe48-489a-4f55-acb5-73da64c4e155
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 973eb19916a737dfa775fe79ee62cb3d11fe0123
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705721"
---
# <a name="registration-and-selection-source-control-vspackage"></a>Inscription et sélection (VSPackage de contrôle de code source)
Un contrôle source VSPackage doit être [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]enregistré pour l’exposer à la . Si plus d’une source de contrôle VSPackage est enregistrée, l’utilisateur peut sélectionner le VSPackage à charger aux moments appropriés. Consultez [VSPackages](../../extensibility/internals/vspackages.md) pour plus de détails sur VSPackages et comment les enregistrer.

## <a name="registering-a-source-control-package"></a>Enregistrement d’un forfait de contrôle des sources
 Le paquet de contrôle source [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] est enregistré afin que l’environnement puisse le trouver et les requêtes pour ses fonctionnalités prises en charge. Ceci est conforme à un système de chargement de retard dans lequel un cas d’un paquet n’est créé que lorsque ses caractéristiques ou commandes sont requises ou sont demandées explicitement.

 VSPackages place des informations dans une clé de registre spécifique à la\\version, HKEY_LOCAL_MACHINE-SOFTWARE-Microsoft-VisualStudio*X.Y*, où *X* est le numéro de version principal et *Y* est le numéro de version mineur. Cette pratique offre la possibilité de soutenir l’installation [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]côte à côte de plusieurs versions de .

 L’interface [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] utilisateur (interface utilisateur) prend en charge la sélection parmi les multiples plug-ins de contrôle source installés (via le package d’adaptateur de contrôle des sources) ainsi que les VSPackages de contrôle source. Il ne peut y avoir qu’un seul plug-in de contrôle de source actif ou VSPackage à la fois. Cependant, comme décrit ci-dessous, l’IDE permet de passer d’un plug-in de contrôle source à VSPackages par le biais d’un mécanisme automatique d’échange de paquets basé sur une solution. Il y a quelques exigences de la part du contrôle source VSPackage pour activer ce mécanisme de sélection.

### <a name="registry-entries"></a>Entrées de Registre
 Un package de contrôle des sources a besoin de trois GUIDs privés :

- Paquet GUID: Il s’agit de la GUID principale pour le paquet qui contient la mise en œuvre de contrôle source (appelé ID_Package dans cette section).

- Source Control GUID: Il s’agit d’un GUID pour le contrôle source VSPackage utilisé pour s’inscrire auprès de la visual Studio Source Control Stub et est également utilisé comme un contexte de commande interface utilisateur GUID. Le service de contrôle source GUID est enregistré sous le contrôle source GUID. Dans l’exemple, le contrôle source GUID est appelé ID_SccProvider.

- Service de contrôle des sources GUID: Il s’agit du service privé GUID utilisé par Visual Studio (appelé SID_SccPkgService dans cette section). En plus de cela, le paquet de contrôle source doit définir d’autres GUIDs pour VSPackages, fenêtres d’outils, et ainsi de suite.

  Les entrées de registre suivantes doivent être faites par un contrôle source VSPackage :

| Nom de clé | Entrées |
| - | - |
| `HKEY_LOCAL_MACHINE\   SOFTWARE\     Microsoft\       VisualStudio\         X.Y\           SourceControlProviders\` | (par défaut) rg_sz : 'ID_SccProvider' |
| `HKEY_LOCAL_MACHINE\   SOFTWARE\     Microsoft\       VisualStudio\         X.Y\           SourceControlProviders\             {ID_SccProvider}\` | (par défaut) rg_sz :\<Nom ami de l'> de paquet<br /><br /> Service rg_sz : SID_SccPkgService |
| `HKEY_LOCAL_MACHINE\   SOFTWARE\     Microsoft\       VisualStudio\         X.Y\           SourceControlProviders\             {ID_SccProvider}\               Name\` | (par défaut) rg_sz :\<ID de ressource pour les> de noms localisés<br /><br /> Forfait rg_sz : ID_Package |
| `HKEY_LOCAL_MACHINE\   SOFTWARE\     Microsoft\       VisualStudio\         X.Y\           SolutionPersistence\             <PackageName>\`<br /><br /> (Notez que le `SourceCodeControl`nom clé, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] , est déjà utilisé \<par et n’est pas disponible comme un choix pour PackageName>.) | (par défaut) rg_sz : 'ID_Package' |

## <a name="selecting-a-source-control-package"></a>Sélection d’un package de contrôle des sources
 Plusieurs plug-ins à base d’API de contrôle des sources et vsPackages de contrôle source peuvent être enregistrés simultanément. Le processus de sélection d’un plug-in de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] contrôle source ou d’un VSPackage doit s’assurer que le plug-in ou le VSPackage charge au moment opportun et peut reporter le chargement des composants inutiles jusqu’à ce qu’ils soient nécessaires. En [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] outre, doit supprimer toute l’interface utilisateur d’autres VSPackages inactifs, y compris les éléments de menu, les boîtes de dialogue, et les barres d’outils, et afficher l’interface utilisateur pour le VSPackage actif.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]charge une source de contrôle VSPackage lorsque l’une des opérations suivantes est effectuée :

- La solution est ouverte (lorsque la solution est sous contrôle source).

   Lorsqu’une solution ou un projet sous contrôle source est ouvert, l’IDE provoque le contrôle source VSPackage qui a été désigné pour que cette solution soit chargée.

- Toutes les commandes de menu du contrôle source VSPackage sont exécutées.

  Un contrôle source VSPackage devrait charger tous les composants dont il a besoin que lorsqu’ils vont réellement être utilisés (autrement connu sous le nom de chargement retardé).

### <a name="automatic-solution-based-vspackage-swapping"></a>Échange automatique de VSPackage basé sur une solution
 Vous pouvez échanger manuellement vsPackages [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] de contrôle source via la boîte de dialogue **Options** dans la catégorie **Contrôle Source.** L’échange automatique de paquets basés sur des solutions signifie qu’un paquet de contrôle source qui a été désigné pour une solution particulière est automatiquement configuré pour être actif lorsque cette solution est ouverte. Chaque paquet de <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider.SetActive%2A> contrôle <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider.SetInactive%2A>source doit implémenter et . [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]gère le commutateur entre les plug-ins de contrôle source (mise en œuvre de l’API de contrôle source) et le contrôle source VSPackages.

 Le paquet d’adaptateur de contrôle des sources est utilisé pour passer à n’importe quel plug-in de contrôle source. Le processus de passage au paquet intermédiaire d’adaptateur de contrôle des sources et la détermination du plug-in de contrôle source qui doit être réglé à actif ou inactif est transparent pour l’utilisateur. Le paquet Adaptateur est toujours actif lorsque n’importe quel plug-in de contrôle source est actif. Passer entre deux plug-ins de contrôle source équivaut à simplement charger et décharger le plug-in DLL. Le passage à un VSPackage de contrôle source implique toutefois d’interagir avec l’IDE pour charger le VSPackage approprié.

 Un contrôle source VSPackage est appelé lorsque toute solution est ouverte et la clé de registre pour le VSPackage est dans le fichier de solution. Lorsque la solution [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] est ouverte, trouve la valeur du registre et charge le contrôle source approprié VSPackage. Tous les VSPackages de contrôle de source doivent avoir les entrées de registre décrites ci-dessus. Une solution qui est sous contrôle source est marquée comme étant associée à un contrôle source particulier VSPackage. Les VSPackages de <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence> contrôle des sources doivent implémenter le pour permettre l’échange automatique de VSPackage basé sur une solution.

### <a name="visual-studio-ui-for-package-selection-and-switching"></a>Interface utilisateur Visual Studio pour la sélection et le commutation des paquets
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]fournit une interface utilisateur pour le contrôle à la source VSPackage et la sélection plug-in dans la boîte de dialogue **Options** dans la catégorie **Contrôle Source.** Il permet à l’utilisateur de sélectionner le plug-in de contrôle source actif ou VSPackage. Une liste d’abandon comprend :

- Tous les paquets de contrôle de source installés

- Tous les plug-ins de contrôle de source installés

- Une option "aucun", qui désactive le contrôle du code source

  Seule l’interface utilisateur pour le choix de contrôle source actif est visible. La sélection VSPackage cache l’interface utilisateur pour le VSPackage précédent et montre l’interface utilisateur pour le nouveau. Le VSPackage actif est sélectionné par utilisateur. Si un utilisateur a [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] plusieurs copies d’ouverture en même temps, chacun peut potentiellement utiliser un VSPackage actif différent. Si plusieurs utilisateurs sont connectés au même ordinateur, chaque [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] utilisateur peut avoir des instances distinctes d’ouverture, chacune avec un VSPackage actif différent. Lorsque plusieurs [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] cas sont fermés par un utilisateur, le contrôle source VSPackage qui était actif pour la dernière solution ouverte devient le contrôle source par défaut VSPackage, à définir actif sur le redémarrage.

  Contrairement aux versions précédentes de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], un redémarrage IDE n’est plus le seul moyen de changer de contrôle source VSPackages. La sélection VSPackage est automatique. Le commutation des paquets nécessite des privilèges d’utilisateur Windows (pas administrateur ou utilisateur d’alimentation).

## <a name="see-also"></a>Voir aussi
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence>
- [Fonctionnalités](../../extensibility/internals/source-control-vspackage-features.md)
- [Création d’un plug-in de contrôle de code source](../../extensibility/internals/creating-a-source-control-plug-in.md)
- [VSPackages](../../extensibility/internals/vspackages.md)
