---
title: Scénarios d’installation de VSPackage | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, deployment considerations
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: eddfc0aa9b8f5b3a169ce87b31a2221983f57aaa
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72722185"
---
# <a name="vspackage-setup-scenarios"></a>Scénarios d’installation de VSPackage

Il est important de concevoir votre programme d’installation VSPackage pour plus de flexibilité. Par exemple, vous devrez peut-être libérer un correctif de sécurité à l’avenir, ou modifier une stratégie d’entreprise qui nécessite une prise en charge minutieuse de la gestion des versions côte à côte.

La [prise en charge de plusieurs versions de Visual Studio](../../extensibility/supporting-multiple-versions-of-visual-studio.md)vous permet d’en savoir plus sur les avantages et les problèmes liés à la prise en charge d’installations côte à côte de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] avec des installations partagées ou côte à côte de votre VSPackage. En bref, les VSPackages côte à côte vous offrent la plus grande flexibilité pour prendre en charge les nouvelles fonctionnalités de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].

Les scénarios abordés dans cette rubrique ne sont pas les seuls choix possibles, mais ils sont présentés en tant que meilleures pratiques suggérées.

## <a name="components-privacy-and-sharing"></a>Composants, confidentialité et partage

### <a name="make-your-components-independent"></a>Rendre vos composants indépendants

Une fois que vous avez identifié et rempli un composant, affecté un `GUID` et déployé le composant, vous ne pouvez pas modifier sa composition. Si vous modifiez la composition d’un composant, le composant résultant doit être un nouveau composant avec un nouveau `GUID`. Compte tenu de ces faits, la plus grande flexibilité en matière de contrôle de version est accordée en faisant de chaque composant une unité indépendante. Pour plus d’informations sur les règles régissant les composants, consultez [modification du code du composant](/windows/desktop/Msi/changing-the-component-code) et [que se passe-t-il si les règles des composants sont rompues ?](/windows/desktop/Msi/what-happens-if-the-component-rules-are-broken).

### <a name="do-not-mix-shared-and-private-resources-in-a-component"></a>Ne pas mélanger les ressources partagées et privées dans un composant

Le décompte de références se produit au niveau du composant. Par conséquent, la combinaison de ressources partagées et privées dans un composant rend impossible la mise à jour des ressources privées, telles qu’un fichier exécutable, sans remplacer également les ressources partagées. Ce scénario crée des problèmes de compatibilité descendante et vous empêche de créer des fonctionnalités côte à côte.

Par exemple, les valeurs de Registre utilisées pour inscrire votre VSPackage avec le [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] doivent être conservées dans un composant distinct de celui utilisé pour inscrire votre VSPackage avec Visual Studio. Les fichiers partagés ou les valeurs de Registre vont encore à un autre composant.

## <a name="scenario-1-shared-vspackage"></a>Scénario 1 : VSPackage partagé

Dans ce scénario, un VSPackage partagé (un fichier binaire unique qui prend en charge plusieurs versions de Visual Studio est fourni dans un package Windows Installer. L’inscription avec chaque version de Visual Studio est contrôlée par des fonctionnalités sélectionnables par l’utilisateur. Cela signifie également que lorsqu’il est attribué à des fonctionnalités distinctes, chaque composant peut être sélectionné individuellement pour l’installation ou la désinstallation, ce qui permet à l’utilisateur de contrôler l’intégration du VSPackage dans différentes versions de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. (Pour plus d’informations sur l’utilisation des fonctionnalités de Windows Installer packages, consultez [fonctionnalités de Windows Installer](/windows/desktop/Msi/windows-installer-features) .)

![Programme d’installation de VS Shared VSPackage](../../extensibility/internals/media/vs_sharedpackage.gif "VS_SharedPackage")

Comme indiqué dans l’illustration, les composants partagés font partie de la fonctionnalité Feat_Common, qui est toujours installée. En rendant les fonctionnalités Feat_VS2002 et Feat_VS2003 visibles, les utilisateurs peuvent choisir au moment de l’installation dans quelles versions de Visual Studio ils souhaitent que le VSPackage s’intègre. Les utilisateurs peuvent également utiliser le mode de maintenance Windows Installer pour ajouter ou supprimer des fonctionnalités, ce qui, dans ce cas, ajoute ou supprime les informations d’inscription du VSPackage dans différentes versions de Visual Studio.

> [!NOTE]
> La définition de la valeur 0 pour la colonne d’affichage d’une fonctionnalité le masque. Une valeur de colonne de bas niveau, telle que 1, garantit qu’elle sera toujours installée. Pour plus d’informations, consultez la [propriété INSTALLLEVEL](/windows/desktop/Msi/installlevel) et la [table des fonctionnalités](/windows/desktop/Msi/feature-table).

## <a name="scenario-2-shared-vspackage-update"></a>Scénario 2 : mise à jour du package VSPackage partagé

Dans ce scénario, une version mise à jour du programme d’installation VSPackage dans le scénario 1 est fournie. Par souci de discussion, la mise à jour ajoute la prise en charge de Visual Studio, mais il peut également s’agir d’un correctif de sécurité ou d’un correctif de bogue plus simple Service Pack. Les règles de Windows Installer pour l’installation de composants plus récents nécessitent que les composants inchangés déjà présents sur le système ne soient pas recopiés. Dans ce cas, un système avec la version 1,0 déjà présente remplace le composant mis à jour Comp_MyVSPackage. dll et permet aux utilisateurs de choisir d’ajouter la nouvelle fonctionnalité Feat_VS2005 avec son composant Comp_VS2005_Reg.

> [!CAUTION]
> Chaque fois qu’un VSPackage est partagé entre plusieurs versions de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], il est essentiel que les versions ultérieures du VSPackage maintiennent la compatibilité descendante avec les versions antérieures de Visual Studio. Si vous ne pouvez pas assurer la compatibilité descendante, vous devez utiliser des VSPackages privés côte à côte. Pour plus d’informations, consultez [prise en charge de plusieurs versions de Visual Studio](../../extensibility/supporting-multiple-versions-of-visual-studio.md).

![Programme d’installation des mises à jour du package vs partagé VS](../../extensibility/internals/media/vs_sharedpackageupdate.gif "VS_SharedPackageUpdate")

Ce scénario présente un nouveau programme d’installation VSPackage, tirant parti de la prise en charge de Windows Installer pour les mises à niveau mineures. Les utilisateurs installent simplement la version 1,1 et le service informatique met à niveau la version 1,0. Toutefois, il n’est pas nécessaire d’avoir la version 1,0 sur le système. Le même programme d’installation installera la version 1,1 sur un système sans la version 1,0. L’avantage de fournir des mises à niveau mineures de cette manière est qu’il n’est pas nécessaire de suivre le travail de développement d’un programme d’installation de mise à niveau et d’un programme d’installation de produit complet. Un programme d’installation effectue les deux tâches. Un correctif ou une Service Pack de sécurité peut tirer parti des correctifs de Windows Installer. Pour plus d’informations, consultez [mise à jour corrective et mises à niveau](/windows/desktop/Msi/patching-and-upgrades).

## <a name="scenario-3-side-by-side-vspackage"></a>Scénario 3 : VSPackage côte à côte

Ce scénario présente deux programmes d’installation VSPackage : un pour chaque version de Visual Studio .NET 2003 et Visual Studio. Chaque programme d’installation installe un VSPackage côte à côte, ou privé, (qui est spécifiquement conçu et installé pour une version particulière de Visual Studio). Chaque VSPackage est dans son propre composant. Par conséquent, chaque service peut être individuellement pris en main avec des correctifs ou des versions de maintenance. Étant donné que la DLL VSPackage est désormais spécifique à la version, il est possible d’inclure en toute sécurité ses informations d’inscription dans le même composant que la DLL.

![Programme d’installation du package vs côte à côte VS](../../extensibility/internals/media/vs_sbys_package.gif "VS_SbyS_Package")

Chaque programme d’installation comprend également du code partagé entre les deux programmes d’installation. Si le code partagé est installé à un emplacement commun, l’installation des deux fichiers. msi n’installe le code partagé qu’une seule fois. Le deuxième programme d’installation incrémente simplement un décompte de références sur le composant. Le décompte de références s’assure que si l’un des VSPackages est désinstallé, le code partagé restera pour l’autre VSPackage. Si le deuxième VSPackage est également désinstallé, le code partagé sera supprimé.

## <a name="scenario-4-side-by-side-vspackage-update"></a>Scénario 4 : mise à jour VSPackage côte à côte

Dans ce scénario, votre VSPackage pour Visual Studio a subi une faille de sécurité et vous devez émettre une mise à jour. Comme dans le scénario 2, vous pouvez créer un nouveau fichier. msi qui met à jour une installation existante pour inclure le correctif de sécurité, ainsi que déployer de nouvelles installations avec le correctif de sécurité déjà en place.

Dans ce cas, le VSPackage est un VSPackage géré installé dans le Global Assembly Cache (GAC). Lorsque vous le régénérez pour inclure le correctif de sécurité, vous devez modifier la partie numéro de révision du numéro de version de l’assembly. Les informations d’inscription pour le nouveau numéro de version de l’assembly remplacent la version précédente, provoquant ainsi [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] le chargement de l’assembly fixe.

![Programme d’installation de la mise à jour du package vs côte à côte VS](../../extensibility/internals/media/vs_sbys_packageupdate.gif "VS_SbyS_PackageUpdate")

Pour plus d’informations sur le déploiement d’assemblys côte à côte, consultez [simplification du déploiement et résolution de l’enfer des dll avec l' .NET Framework](https://msdn.microsoft.com/library/ms973843.aspx).

## <a name="see-also"></a>Voir aussi

- [Windows Installer](/windows/desktop/Msi/windows-installer-portal)
- [Prise en charge de plusieurs versions de Visual Studio](../../extensibility/supporting-multiple-versions-of-visual-studio.md)