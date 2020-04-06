---
title: Gestion des composants (fr) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- installation [Visual Studio SDK], components
- installation [Visual Studio SDK], file management
ms.assetid: 029bffa2-6841-4caa-a41a-442467e1aedc
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b5dcac9fb14a83021b852be2c52436fcdca84bf5
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709338"
---
# <a name="component-management"></a>Gestion des composants
Les unités de tâches dans l’installateur Windows sont appelées composants d’installateur Windows (parfois appelés WIC ou juste des composants). Un GUID identifie chaque WIC, qui est l’unité de base de l’installation et le comptage de référence pour les configurations qui utilisent Windows Installer.

 Bien que vous puissiez utiliser plusieurs produits pour créer votre installateur VSPackage, cette discussion suppose l’utilisation de Windows Installer (*.msi*) fichiers. Lors de la création de votre installateur, vous devez gérer correctement le déploiement de fichiers afin que le bon comptage des références se fasse en tout temps. Par conséquent, différentes versions de votre produit n’interfèrent pas ou ne se cassent pas les unes les autres dans un mélange de scénarios d’installation et de désinstallation.

 Dans Windows Install, le comptage des références se produit au niveau des composants. Vous devez organiser soigneusement vos ressources — dossiers, entrées de registre, etc. — en composants. Il existe d’autres niveaux d’organisation — comme les modules, les fonctionnalités et les produits — qui peuvent aider à différents scénarios. Pour plus d’informations, voir [les bases de Windows Installer](../../extensibility/internals/windows-installer-basics.md).

## <a name="guidelines-of-authoring-setup-for-side-by-side-installation"></a>Lignes directrices de la mise en place de la rédaction d’une installation côte à côte

- Fichiers d’auteurs et clés de registre qui sont partagés entre les versions dans leurs propres composants.

     Cela vous permet de les consommer facilement dans la version suivante. Par exemple, les bibliothèques de type qui sont enregistrées à l’échelle mondiale, les extensions de fichiers, d’autres articles enregistrés dans **HKEY_CLASSES_ROOT,** et ainsi de suite.

- Regrouper les composants partagés en modules de fusion distincts.

     Cette stratégie vous aide à présenter correctement l’installation côte à côte pour aller de l’avant.

- Installez des fichiers partagés et des clés de registre en utilisant les mêmes composants Windows Installer à travers les versions.

     Si vous utilisez un composant différent, les fichiers et les entrées de registre sont nonins bloqués lorsqu’une version VSPackage est désinstallée, mais un autre VSPackage est toujours installé.

- Ne mélangez pas les éléments versionnés et partagés dans le même composant.

     Cela rend impossible l’installation d’éléments partagés à un emplacement global et des articles en version à des endroits isolés.

- N’avez pas de clés de registre partagées qui pointent vers les fichiers versionnés.

     Si vous le faites, les clés partagées seront écrasées lors de l’installation d’un autre VSPackage version. Après avoir supprimé la deuxième version, le fichier auquel la clé est pointée a disparu.

## <a name="see-also"></a>Voir aussi
- [Choisissez entre VSPackages partagés et versions](../../extensibility/choosing-between-shared-and-versioned-vspackages.md)
- [Scénarios de configuration VSPackage](../../extensibility/internals/vspackage-setup-scenarios.md)
