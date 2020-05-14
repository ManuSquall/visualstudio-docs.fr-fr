---
title: Bases de l’installateur Windows Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Windows Installer, VSPackages
- VSPackages, Windows Installer basics
ms.assetid: 497e479b-add8-4644-870a-917f15306b97
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: aeea0b17a3c234bb7670642fb9ae0a442c9d60cd
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80703420"
---
# <a name="windows-installer-basics"></a>Éléments de base de Windows Installer
L’installateur Windows installe et désinstalle des applications ou des produits logiciels sur l’ordinateur d’un utilisateur, exécutant ces tâches dans des unités appelées composants d’installateur Windows (parfois appelés WIC ou juste des composants). Un GUID identifie chaque WIC, qui est l’unité de base de l’installation et le comptage de référence pour les configurations à l’aide de Windows Installer.

 Pour une documentation complète de l’installateur Windows, consultez le sujet Plate-forme SDK, [Windows Installer](/previous-versions/2kt85ked(v=vs.120)).

## <a name="authoring-a-vspackage"></a>Auteur d’un VSPackage
 Windows Install utilise des paquets d’installation, qui contiennent des informations que Windows Installer doit installer, désinstaller ou réparer un produit et pour exécuter l’interface utilisateur de configuration (interface utilisateur). Chaque paquet d’installation comprend un fichier .msi, qui contient une base de données d’installation, un flux d’informations sommaires et des flux de données pour diverses parties de l’installation. Pour utiliser l’installateur, vous devez écrire une installation. Étant donné que l’installateur organise des installations autour du concept de composants et stocke des informations sur l’installation dans une base de données relationnelle, le processus de rédaction d’un ensemble d’installation comporte largement les étapes suivantes :

1. Planifiez votre mise en place pour prendre en charge votre version et vos stratégies côte à côte.

2. Identifiez les fonctionnalités à présenter aux utilisateurs.

3. Organisez le VSPackage et les dépendances en composants.

4. Remplissez la base de données d’installation avec des informations.

5. Valider le paquet d’installation.

   Cette documentation porte principalement sur les premières et troisième étapes du processus. Au cours de ces étapes, vous organisez vos fonctionnalités VSPackage en WIC [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]afin que vous puissiez encadrer votre stratégie de version et de service pour tenir compte des versions ultérieures de . Les trois autres étapes sont couvertes en détail dans la documentation De Windows Installer dans la plate-forme SDK.

## <a name="key-terms"></a>Termes clés
 Voici des définitions des termes clés liés à la technologie Windows Installer.

 Fichiers de ressources, clés de registre, raccourcis, ou ainsi de suite qui peuvent être installés sur un ordinateur. Ces ressources sont regroupées logiquement en composants Windows Installer.

 Composant d’installateur Windows (WIC) L’unité de base de l’installation représentant un regroupement logique des ressources connexes qui sont installées et non bloquées en tant qu’unité. Les composants d’installateur Windows sont identifiés par un id de composant unique, ou GUID. En outre, Windows Installer maintient son comptage de référence au niveau WIC. Pour une flexibilité de version maximale, n’incluez pas plus d’une ressource primaire, comme un DLL, dans un WIC donné. Notez qu’après avoir identifié et peuplé un WIC, lui donner un GUID, et le déployer, vous ne pouvez pas changer sa composition. Pour plus d’informations, voir [Organiser les applications en composants](/windows/desktop/Msi/organizing-applications-into-components).

 Paquet (paquet Redist) Une unité de déploiement qui se compose d’un fichier .msi et des fichiers sources externes auxquels ce fichier pourrait pointer. Un paquet contient toutes les informations dont Windows Installateur a besoin pour exécuter l’interface utilisateur et installer ou désinstaller l’application.

 .msi Fichier Un fichier de stockage structuré COM contenant les instructions et les données requises pour installer une application. Chaque paquet contient au moins un fichier .msi. Le fichier .msi contient la base de données de l’installateur, un flux d’informations sommaires, et peut-être une ou plusieurs transformations et fichiers sources internes. Les fichiers à installer peuvent être comprimés dans une armoire et stockés dans un flux dans le fichier .msi ou stockés, compressés ou non compressés, en dehors du fichier .msi sur le support source. Pour plus d’informations, voir [Windows Installer File Extensions](/windows/desktop/Msi/windows-installer-file-extensions).

## <a name="windows-installer-rules-enforcement"></a>Application des règles d’installateur Windows
 Deux ensembles de règles déterminent le déploiement des ressources grâce aux composants de votre configuration. Un ensemble de règles est maintenu par l’installateur Windows lui-même, tandis que vous devez appliquer le deuxième ensemble en tant qu’auteur d’installation.

> [!NOTE]
> L’application des règles d’installateur Windows ne se produit que si vous exécutez une validation de votre fichier .msi. Néanmoins, vous êtes mis en garde pour traiter ces règles comme des pratiques exemplaires. Pour plus d’informations, voir [Valider une base de données d’installation](/windows/desktop/Msi/validating-an-installation-database) et [la validation des paquets](/windows/desktop/Msi/package-validation).

#### <a name="installer-enforced-rules"></a>Règles d’installateur-appliquées

- Tous les fichiers d’un composant donné doivent être installés dans le même répertoire. Inversement, les fichiers installés pour séparer les dossiers doivent appartenir à des composants distincts.

- Il ne peut y avoir qu’un seul chemin clé par composant. La voie clé est simplement une clé de fichier ou de registre qui représente l’ensemble du composant.

#### <a name="component-provider-responsibilities"></a>Responsabilités composantes-fournisseurs

- Toutes les deux ressources qui pourraient être expédiées séparément dans les versions ultérieures devraient exister dans des composants distincts. Les ressources ne doivent être regroupées dans le même composant que lorsque vous êtes certain que ces ressources ne seront jamais expédiées séparément. En fait, il est recommandé que toutes les ressources primaires (DLL, par exemple) existent toujours dans des WIC distincts. Pour plus d’informations, voir [Définir les composants d’installateur](/windows/desktop/Msi/defining-installer-components).

- Aucune ressource versionnée ne devrait jamais expédier dans plus d’un WIC.

## <a name="see-also"></a>Voir aussi
- [Que se passe-t-il si les règles de composants sont enfreintes?](/windows/desktop/Msi/what-happens-if-the-component-rules-are-broken)
