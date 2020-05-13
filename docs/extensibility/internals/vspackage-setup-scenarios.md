---
title: Scénarios d’installation VSPackage (fr) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, deployment considerations
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 01279666642adb729d4350b8a497c42d78159120
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80703972"
---
# <a name="vspackage-setup-scenarios"></a>Scénarios d’installation de VSPackage

Il est important de concevoir votre installateur VSPackage pour plus de flexibilité. Par exemple, vous devrez peut-être publier un correctif de sécurité à l’avenir, ou vous pouvez modifier une stratégie d’entreprise qui nécessite un support complet de version côte à côte.

Dans [Supporting Multiple Versions of Visual Studio](../../extensibility/supporting-multiple-versions-of-visual-studio.md), vous pouvez lire sur les [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] avantages et les questions de prendre en charge les installations côte à côte avec des installations partagées ou côte à côte de votre VSPackage. En bref, côte à côte VSPackages vous donner le [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]plus de flexibilité pour prendre en charge de nouvelles fonctionnalités de .

Les scénarios discutés dans ce sujet ne sont pas vos seuls choix, mais ils sont présentés comme des pratiques exemplaires suggérées.

## <a name="components-privacy-and-sharing"></a>Composants, confidentialité et partage

### <a name="make-your-components-independent"></a>Rendre vos composants indépendants

Une fois que vous identifiez `GUID`et peuplez un composant, assignez un , et déployez le composant, vous ne pouvez pas changer sa composition. Si vous modifiez la composition d’un composant, le composant `GUID`résultant doit être un nouveau composant avec un nouveau . Compte tenu de ces faits, la plus grande flexibilité de version est offerte en rendant chaque composant indépendant, unité autonome. Pour plus d’informations sur les règles régissant les composants, voir [Changer le code des composants](/windows/desktop/Msi/changing-the-component-code) et que se [passe-t-il si les règles de composante sont enfreintes?](/windows/desktop/Msi/what-happens-if-the-component-rules-are-broken).

### <a name="do-not-mix-shared-and-private-resources-in-a-component"></a>Ne pas mélanger les ressources partagées et privées dans un composant

Le comptage des références se produit au niveau des composants. Par conséquent, le mélange de ressources partagées et privées dans un composant rend impossible la mise à jour des ressources privées, comme un fichier exécutable, sans également supercrire des ressources partagées. Ce scénario crée des problèmes de compatibilité rétrograde et vous empêche de créer des capacités côte à côte.

Par exemple, les valeurs de registre utilisées [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] pour enregistrer votre VSPackage avec le devrait être conservé dans un composant séparé de celui utilisé pour enregistrer votre VSPackage avec Visual Studio. Les fichiers partagés ou les valeurs de registre entrent dans un autre composant.

## <a name="scenario-1-shared-vspackage"></a>Scénario 1 : VSPackage partagé

Dans ce scénario, un VSPackage partagé (un binaire unique qui prend en charge plusieurs versions de Visual Studio est expédié dans un package Windows Installer. L’inscription à chaque version de Visual Studio est contrôlée par des fonctionnalités sélectionnables par l’utilisateur. Cela signifie également que lorsqu’il est affecté à des fonctionnalités distinctes, chaque composant peut être sélectionné individuellement pour l’installation ou la non-réinstallation, ce qui place l’utilisateur dans le contrôle de l’intégration du VSPackage dans différentes versions de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. (Voir [les fonctionnalités d’installateur Windows](/windows/desktop/Msi/windows-installer-features) pour plus d’informations sur l’utilisation des fonctionnalités dans les paquets d’installateur Windows.)

![INSTALLateur VS Partagé VSPackage](../../extensibility/internals/media/vs_sharedpackage.gif "VS_SharedPackage")

Comme le montre l’illustration, les composants partagés font partie de la Feat_Common fonction, qui est toujours installée. En rendant visibles les caractéristiques Feat_VS2002 et Feat_VS2003, les utilisateurs peuvent choisir à l’heure d’installation dans quelles versions de Visual Studio qu’ils souhaitent intégrer. Les utilisateurs peuvent également utiliser le mode de maintenance De l’installateur Windows pour ajouter ou supprimer des fonctionnalités qui, dans ce cas, ajoutent ou suppriment les informations d’enregistrement VSPackage provenant de différentes versions de Visual Studio.

> [!NOTE]
> La définition de la colonne d’affichage d’une fonctionnalité à 0 la cache. Une faible valeur de colonne de niveau, comme 1, garantit qu’elle sera toujours installée. Pour plus d’informations, voir [INSTALLLEVEL Property](/windows/desktop/Msi/installlevel) and [Feature Table](/windows/desktop/Msi/feature-table).

## <a name="scenario-2-shared-vspackage-update"></a>Scénario 2 : Mise à jour VSPackage partagée

Dans ce scénario, une version mise à jour de l’installateur VSPackage dans le scénario 1 est expédiée. Pour des raisons de discussion, la mise à jour ajoute un soutien pour Visual Studio, mais il pourrait également être un correctif de sécurité plus simple ou bug-fix pack de service. Les règles de Windows Installer pour l’installation de composants plus récents exigent que les composants inchangés déjà sur le système ne soient pas réopiés. Dans ce cas, un système avec la version 1.0 déjà présent va remplacer le composant mis à jour Comp_MyVSPackage.dll et laisser les utilisateurs choisissent d’ajouter la nouvelle fonctionnalité Feat_VS2005 avec son composant Comp_VS2005_Reg.

> [!CAUTION]
> Chaque fois qu’un VSPackage [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]est partagé entre plusieurs versions de , il est essentiel que les versions ultérieures de la VSPackage maintenir la compatibilité vers l’arrière avec les versions antérieures de Visual Studio. Lorsque vous ne pouvez pas maintenir la compatibilité vers l’arrière, vous devez utiliser côte à côte, VSPackages privés. Pour plus d’informations, voir [Supporting Multiple Versions of Visual Studio](../../extensibility/supporting-multiple-versions-of-visual-studio.md).

![INSTALLateur de mise à jour de paquets VS partagé VS](../../extensibility/internals/media/vs_sharedpackageupdate.gif "VS_SharedPackageUpdate")

Ce scénario présente un nouvel installateur VSPackage, en profitant du support de Windows Installer pour des mises à niveau mineures. Les utilisateurs installent simplement la version 1.1 et il améliore la version 1.0. Cependant, il n’est pas nécessaire d’avoir la version 1.0 sur le système. Le même installateur installera la version 1.1 sur un système sans version 1.0. L’avantage de fournir des améliorations mineures de cette manière est qu’il n’est pas nécessaire de passer par le travail de développement d’un installateur de mise à niveau et un installateur de produits complets. Un installateur fait les deux travaux. Un correctif de sécurité ou un pack de service peut plutôt profiter des correctifs Windows Installer. Pour plus d’informations, voir [Patching and Upgrades](/windows/desktop/Msi/patching-and-upgrades).

## <a name="scenario-3-side-by-side-vspackage"></a>Scénario 3 : VSPackage côte à côte

Ce scénario présente deux installateurs VSPackage - un pour chaque version de Visual Studio .NET 2003 et Visual Studio. Chaque installateur installe un VSPackage côte à côte ou privé (qui est spécialement construit et installé pour une version particulière de Visual Studio). Chaque VSPackage est dans son propre composant. Par conséquent, chacun peut être entretenu individuellement avec des correctifs ou des communiqués de maintenance. Étant donné que le VSPackage DLL est maintenant spécifique à la version, il est sûr d’inclure ses informations d’enregistrement dans le même composant que le DLL.

![INSTALLateur de forfait VS Side-by-Side VS](../../extensibility/internals/media/vs_sbys_package.gif "VS_SbyS_Package")

Chaque installateur comprend également le code qui est partagé entre les deux installateurs. Si le code partagé est installé à un emplacement commun, l’installation des deux fichiers .msi n’installera le code partagé qu’une seule fois. Le deuxième installateur incrémente juste un compte de référence sur le composant. Le décompte des références garantit que si l’un des VSPackages n’est pas bloqué, le code partagé restera pour l’autre VSPackage. Si le deuxième VSPackage n’est pas bloqué, le code partagé sera supprimé.

## <a name="scenario-4-side-by-side-vspackage-update"></a>Scénario 4 : Mise à jour VSPackage côte à côte

Dans ce scénario, votre VSPackage pour Visual Studio a souffert d’une vulnérabilité de sécurité et vous devez émettre une mise à jour. Comme dans le scénario 2, vous pouvez créer un nouveau fichier .msi qui met à jour une installation existante pour inclure le correctif de sécurité, ainsi que déployer de nouvelles installations avec le correctif de sécurité déjà en place.

Dans ce cas, le VSPackage est un VSPackage géré installé dans le cache d’assemblage global (GAC). Lorsque vous le reconstruisez pour inclure le correctif de sécurité, vous devez modifier la partie numéro de révision du numéro de version d’assemblage. Les informations d’enregistrement pour le nouveau numéro de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] version d’assemblage surécrit la version précédente, ce qui provoque le chargement de l’assemblage fixe.

![INSTALLateur de mise à jour de paquet VS side-by-Side VS](../../extensibility/internals/media/vs_sbys_packageupdate.gif "VS_SbyS_PackageUpdate")

Pour plus d’informations sur le déploiement d’assemblages côte à côte, voir [Simplifier le déploiement et résoudre l’enfer DLL avec le cadre .NET](https://msdn.microsoft.com/library/ms973843.aspx).

## <a name="see-also"></a>Voir aussi

- [Installateur Windows](/windows/desktop/Msi/windows-installer-portal)
- [Prise en charge de plusieurs versions de Visual Studio](../../extensibility/supporting-multiple-versions-of-visual-studio.md)
