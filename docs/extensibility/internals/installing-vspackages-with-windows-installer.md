---
title: Installation de VSPackages avec Windows Installer | Microsoft Docs
description: Découvrez comment utiliser la Microsoft Windows Installer pour installer un VSPackage et ses fichiers dépendants, puis l’inscrire et l’intégrer dans Visual Studio.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: ec49e5184071e0640d671ba0baaad8ac049fea25
ms.sourcegitcommit: a436ba564717b992eb1984b28ea0aec801eacaec
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/14/2021
ms.locfileid: "98205232"
---
# <a name="installing-vspackages-with-windows-installer"></a>Installation de VSPackages avec Windows Installer
L’intégration de votre VSPackage dans [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] nécessite plus qu’une simple copie de fichiers sur l’ordinateur d’un utilisateur. Le programme d’installation de votre VSPackage doit installer le VSPackage et ses fichiers dépendants, puis l’inscrire et l’intégrer dans [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] . Votre VSPackage peut tirer parti des fonctionnalités d’intégration, telles que l’affichage d’une icône sur l' [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] écran de démarrage et la boîte de dialogue à propos de.

 Microsoft Windows Installer fichiers sont la méthode recommandée pour distribuer vos VSPackages. Les packages Windows Installer faciles à utiliser peuvent s’exécuter sur n’importe quel système d’exploitation Windows pris en charge par [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] . Pour plus d’informations, consultez [Windows Installer](/previous-versions/2kt85ked(v=vs.120)).

## <a name="in-this-section"></a>Dans cette section
- [Éléments de base de Windows Installer](../../extensibility/internals/windows-installer-basics.md)

 Fournit une vue d’ensemble de l’Windows Installer.

- [Scénarios d’installation de VSPackage](../../extensibility/internals/vspackage-setup-scenarios.md)

 Décrit les différentes façons dont vous pouvez prendre en charge les installations côte à côte de vos VSPackages et de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .

- [Création d’un package Windows Installer](../../extensibility/internals/authoring-a-windows-installer-package.md)

 Fournit une vue d’ensemble des programmes d’installation des étapes classiques à suivre pour installer et intégrer correctement les VSPackages dans [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .

- [Détection de la configuration système requise](../../extensibility/internals/detecting-system-requirements.md)

 Décrit comment un programme d’installation peut détecter [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] et ses composants, et annuler l’installation si les exigences du VSPackage ne sont pas satisfaites.

- [Gestion des composants](../../extensibility/internals/component-management.md)

 Explique comment développer un programme d’installation qui conservera l’intégrité des versions précédentes du produit.

- [Choix du répertoire d’installation d’un VSPackage](../../extensibility/internals/choosing-the-installation-directory-for-a-vspackage.md)

 Résume les options de recherche de VSPackages.

- [Inscription de VSPackage](../../extensibility/internals/vspackage-registration.md)

 Explique comment les VSPackages sont inscrits au moment de l’installation et pourquoi l’inscription automatique est une mauvaise idée.

- [Déploiement des types de projets](../../extensibility/internals/deploying-project-types.md)

 Explique comment utiliser la nouvelle agrégation de type projet pour les types de projets de code managé.

- [Guide pratique pour générer des informations de registre pour un programme d’installation](../../extensibility/internals/how-to-generate-registry-information-for-an-installer.md)

 Explique comment utiliser RegPkg.exe pour générer un manifeste d’inscription pour un VSPackage managé.

- [Commandes à exécuter après l’installation](../../extensibility/internals/commands-that-must-be-run-after-installation.md)

 Explique comment exécuter des commandes de postconnexion pour intégrer les VSPackages dans [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .

- [Désinstallation d’un VSPackage avec Windows Installer](../../extensibility/internals/uninstalling-a-vspackage-with-windows-installer.md)

 Décrit les étapes que votre programme d’installation doit effectuer lorsque les utilisateurs désinstallent votre VSPackage.