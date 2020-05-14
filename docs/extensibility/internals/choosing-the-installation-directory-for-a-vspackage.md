---
title: Choisir l’annuaire d’installation pour un VSPackage (fr) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, installation directory
ms.assetid: 01fbbb5b-f747-446c-afe0-2a081626a945
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b8391cbdd3a857ea4ebaf3a36655520935f1a128
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709759"
---
# <a name="choose-the-installation-directory-for-a-vspackage"></a>Choisissez l’annuaire d’installation pour un VSPackage
Un VSPackage et ses fichiers supportatifs doivent figurer sur le système de fichiers d’un utilisateur. L’emplacement dépend si le VSPackage est géré ou non géré, votre système de version côte à côte, et le choix de l’utilisateur.

## <a name="unmanaged-vspackages"></a>VSPackages non mentés
 Un VSPackage non menté est un serveur COM qui peut être installé à n’importe quel endroit. Ses informations d’enregistrement doivent refléter fidèlement son emplacement. Votre interface utilisateur d’installateur (interface utilisateur) devrait fournir `ProgramFilesFolder` un emplacement par défaut en tant que sous-direction de la valeur de propriété de Windows Installer. Par exemple :

*&lt;ProgramFilesFolder&gt;\\&lt;MyCompany&gt;\\&lt;MyVSPackageProduct&gt;(V1.0)\\*

 L’utilisateur doit être autorisé à modifier l’annuaire par défaut pour accueillir les utilisateurs qui gardent une petite partition de démarrage et préfèrent installer des applications et des outils sur un autre volume.

 Si votre système côte à côte utilise un VSPackage versionné, vous pouvez utiliser des sous-directeurs pour stocker différentes versions. Par exemple :

 *&lt;ProgramFilesFolder&gt;\\&lt;MyCompany&gt;\\&lt;MyVSPackageProduct&gt;\\V1.0\\2002\\*

 *&lt;ProgramFilesFolder&gt;\\&lt;MyCompany&gt;\\&lt;MyVSPackageProduct&gt;\\V1.0\\2003\\*

 *&lt;ProgramFilesFolder&gt;\\&lt;MyCompany&gt;\\&lt;MyVSPackageProduct&gt;\\V1.0\\2005\\*

## <a name="managed-vspackages"></a>VSPackages gérés
 Les VSPackages gérés peuvent également être installés à n’importe quel endroit. Cependant, vous devriez envisager de toujours les installer dans le cache d’assemblage global (GAC) pour réduire les temps de chargement d’assemblage. Étant donné que les VSPackages gérés sont toujours des assemblages de nom fort, leur installation dans le GAC signifie que leur vérification de signature de nom fort ne prend qu’au moment de l’installation. Les assemblages nommés forts installés ailleurs dans le système de fichiers doivent faire vérifier leurs signatures chaque fois qu’elles sont chargées. Lorsque vous installez des VSPackages gérés dans le GAC, utilisez le commutateur de l’outil **regpkg/assemblage** pour écrire des entrées de registre indiquant le nom fort de l’assemblage.

 Si vous installez des VSPackages gérés dans un endroit autre que le GAC, suivez les conseils donnés précédemment pour les VSPackages non gérés pour le choix des hiérarchies d’annuaire. Utilisez le commutateur de base de **code de** l’outil regpkg pour écrire des entrées de registre indiquant le chemin de l’assemblage VSPackage.

 Pour plus d’informations, voir [Inscrivez-vous et non enregistré VSPackages](../../extensibility/registering-and-unregistering-vspackages.md).

## <a name="satellite-dlls"></a>DLL satellites
 Par convention, les DLL par satellite VSPackage, qui contiennent des ressources pour un endroit particulier, sont situés dans des sous-directeurs de l’annuaire *VSPackage.* Les sous-directions correspondent aux valeurs locales d’ID (LCID).

 [L’article Manage VSPackages](../../extensibility/managing-vspackages.md) indique [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] que les entrées de registre contrôlent là où recherche réellement le satellite DLL d’un VSPackage. Cependant, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] tente de charger un satellite DLL dans une sous-direction nommée d’après une valeur LCID, dans l’ordre suivant:

1. Par défaut LCID (Visual Studio LCID; par exemple, *1033* euros pour l’anglais)

2. Par défaut LCID avec le sous-languement par défaut.

3. Système par défaut LCID.

4. Système par défaut LCID avec le sous-système par défaut.

5. U.S. English *(.1033* ou *.-0x409*).

Si votre VSPackage DLL comprend des ressources et que le registre [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] **SatelliteDll-DllName** y indique, tente de les charger dans l’ordre ci-dessus.

## <a name="see-also"></a>Voir aussi
- [Choisissez entre VSPackages partagés et versions](../../extensibility/choosing-between-shared-and-versioned-vspackages.md)
- [Gérer VSPackages](../../extensibility/managing-vspackages.md)
- [Gérer l’enregistrement des colis](https://msdn.microsoft.com/library/f69e0ea3-6a92-4639-8ca9-4c9c210e58a1)
