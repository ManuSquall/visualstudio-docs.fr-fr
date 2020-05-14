---
title: Installation de VSPackages avec installateur Windows (fr) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- installation [Visual Studio SDK], with Windows Installer
- VSPackages, deploying
ms.assetid: 41d2c72c-0a97-4fcd-b3aa-33a8d3aa962a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2eb90dbffa9f04cd17afa70d2bdfc59205bc99cb
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707463"
---
# <a name="installing-vspackages-with-windows-installer"></a>Installation de VSPackages avec Windows Installer
L’intégration de votre [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] VSPackage nécessite plus que la simple copie de fichiers sur l’ordinateur d’un utilisateur. L’installateur de votre VSPackage doit installer le VSPackage et [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]ses fichiers dépendants, et les enregistrer et les intégrer dans . Votre VSPackage peut profiter de fonctionnalités d’intégration telles que l’affichage d’une icône sur l’écran [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] d’éclaboussure et about dialog box.

 Les fichiers Microsoft Windows Install sont le moyen recommandé de distribuer vos VSPackages. Les forfaits Windows InstallAteur faciles à utiliser peuvent [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]s’exécuter sur n’importe quel système d’exploitation Windows pris en charge par . Pour plus d’informations, voir [Windows Installer](https://msdn.microsoft.com/library/121be21b-b916-43e2-8f10-8b080516d2a0).

## <a name="in-this-section"></a>Dans cette section
- [Éléments de base de Windows Installer](../../extensibility/internals/windows-installer-basics.md)

 Fournit un aperçu de l’installateur Windows.

- [Scénarios d’installation de VSPackage](../../extensibility/internals/vspackage-setup-scenarios.md)

 Discute de différentes façons dont vous pouvez prendre en charge [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]les installations côte à côte de vos VSPackages et .

- [Création d’un package Windows Installer](../../extensibility/internals/authoring-a-windows-installer-package.md)

 Fournit un aperçu des étapes typiques installateurs suivre pour [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]installer et intégrer correctement VSPackages dans .

- [Détection de la configuration système requise](../../extensibility/internals/detecting-system-requirements.md)

 Décrit comment un installateur peut détecter [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] et ses composants et annuler la configuration si les exigences VSPackage ne sont pas remplies.

- [Gestion des composants](../../extensibility/internals/component-management.md)

 Discute de la façon de développer un installateur qui maintiendra l’intégrité des versions de produits précédentes.

- [Choix du répertoire d’installation d’un VSPackage](../../extensibility/internals/choosing-the-installation-directory-for-a-vspackage.md)

 Résume les options pour localiser VSPackages.

- [Inscription de VSPackage](../../extensibility/internals/vspackage-registration.md)

 Discute de la façon dont les VSPackages sont enregistrés au moment de l’installation et pourquoi l’auto-enregistrement est une mauvaise idée.

- [Déploiement des types de projets](../../extensibility/internals/deploying-project-types.md)

 Discute de la façon d’utiliser le nouvel agrégateur de type projet pour les types de projets à code géré.

- [Guide pratique pour générer des informations de registre pour un programme d’installation](../../extensibility/internals/how-to-generate-registry-information-for-an-installer.md)

 Explique comment utiliser RegPkg.exe pour générer un manifeste d’enregistrement pour un VSPackage géré.

- [Commandes à exécuter après l’installation](../../extensibility/internals/commands-that-must-be-run-after-installation.md)

 Explique comment exécuter des commandes post-installation pour [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]intégrer VSPackages dans .

- [Désinstallation d’un VSPackage avec Windows Installer](../../extensibility/internals/uninstalling-a-vspackage-with-windows-installer.md)

 Décrit les étapes que votre installateur doit effectuer lorsque les utilisateurs désinstallent votre VSPackage.
