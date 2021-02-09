---
title: Inscription du VSPackage | Microsoft Docs
description: En savoir plus sur l’inscription du VSPackage, où les packages conseillent à Visual Studio de les installer et doivent être chargés en écrivant des informations dans le registre.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- registration, VSPackages
- VSPackages, registering
ms.assetid: ecd20da8-b04b-4141-a8f4-a2ef91dd597a
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 5ed2dfccb47c980852bcdda423871f7517ef785a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99900042"
---
# <a name="vspackage-registration"></a>Inscription de VSPackage
Les VSPackages doivent signaler [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] qu’ils sont installés et doivent être chargés. Ce processus s’effectue en écrivant des informations dans le registre. Il s’agit d’un travail classique d’un programme d’installation.

> [!NOTE]
> Il s’agit d’une pratique acceptée pendant le développement VSPackage pour utiliser l’inscription automatique. Toutefois, [!INCLUDE[vsipprvsip](../../extensibility/includes/vsipprvsip_md.md)] les partenaires ne peuvent pas livrer leurs produits à l’aide de l’auto-inscription dans le cadre de l’installation.

 Les entrées de Registre dans un package Windows Installer sont généralement effectuées dans la table du Registre. Vous pouvez également enregistrer des extensions de fichier dans la table du Registre. Toutefois, Windows Installer fournit une prise en charge intégrée par le biais de l’identificateur programmatique (ProgId), de la classe, de l’extension et des tables de verbes. Pour plus d’informations, consultez [tables de base de données](/windows/desktop/Msi/database-tables).

 Veillez à ce que vos entrées de registre soient associées au composant adapté à la stratégie côte à côte choisie. Par exemple, les entrées de registre d’un fichier partagé doivent être associées au composant Windows Installer de ce fichier. De même, les entrées de registre d’un fichier spécifique à la version doivent être associées au composant de ce fichier. Dans le cas contraire, l’installation ou la désinstallation de votre VSPackage pour une version de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] peut rompre votre VSPackage dans d’autres versions. Pour plus d’informations, consultez [prise en charge de plusieurs versions de Visual Studio](../../extensibility/supporting-multiple-versions-of-visual-studio.md).

> [!NOTE]
> Le moyen le plus simple de gérer l’inscription consiste à utiliser les mêmes données dans les mêmes fichiers pour l’inscription du développeur et l’inscription au moment de l’installation. Par exemple, certains outils de développement de programme d’installation peuvent consommer un fichier au format. reg au moment de la génération. Si les développeurs maintiennent des fichiers. reg pour leur propre développement et débogage quotidiens, ces mêmes fichiers peuvent être inclus dans le programme d’installation automatiquement. Si vous ne pouvez pas partager automatiquement les données d’inscription, vous devez vous assurer que la copie du programme d’installation des données d’inscription est à jour.

## <a name="registering-unmanaged-vspackages"></a>Inscription des VSPackages non managés
 Les VSPackages non managés (y compris ceux générés par le modèle de package Visual Studio) utilisent des fichiers. RGS de style ATL pour stocker des informations d’inscription. Le format de fichier. RGS est spécifique à ATL et ne peut généralement pas être utilisé tel quel par un outil de création d’installation. Les informations d’inscription pour le programme d’installation du package Windows doivent être gérées séparément. Par exemple, les développeurs peuvent conserver les fichiers au format. reg synchronisé avec les modifications apportées au fichier. RGS. Les fichiers. reg peuvent être fusionnés avec RegEdit pour le travail de développement ou utilisés par un programme d’installation.

## <a name="registering-managed-vspackages"></a>Inscription des VSPackages managés
 L’outil RegPkg lit les attributs d’inscription à partir d’un VSPackage géré et peut soit écrire les informations directement dans le registre, soit écrire des fichiers de format. reg qui peuvent être utilisés par un programme d’installation.

> [!NOTE]
> L’outil RegPkg n’est pas redistribuable et ne peut pas être utilisé pour inscrire un VSPackage sur le système d’un utilisateur.

## <a name="why-vspackages-should-not-self-register-at-install-time"></a>Pourquoi les VSPackages ne doivent pas Self-Register au moment de l’installation
 Vos programmes d’installation VSPackage ne doivent pas s’appuyer sur l’auto-inscription. À première vue, la conservation des valeurs de registre d’un VSPackage uniquement dans le VSPackage lui-même semble être une bonne idée. Étant donné que les développeurs ont besoin des valeurs de Registre disponibles pour le travail et les tests de routine, il est logique d’éviter de conserver une copie distincte des données du Registre dans le programme d’installation. Le programme d’installation peut s’appuyer sur le VSPackage lui-même pour écrire des valeurs de registre.

 Bien qu’en théorie, l’auto-enregistrement présente plusieurs défauts qui le rendent inapproprié pour l’installation du VSPackage :

- La prise en charge correcte de l’installation, de la désinstallation, de la restauration de l’installation et de la restauration de la désinstallation vous oblige à créer quatre actions personnalisées pour chaque VSPackage géré qui s’inscrit automatiquement en appelant RegPkg.

- Votre approche de la prise en charge côte à côte peut vous amener à créer quatre actions personnalisées qui appellent RegSvr32 ou RegPkg pour chaque version prise en charge de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .

- Une installation avec des modules auto-inscrits ne peut pas être restaurée en toute sécurité, car il n’est pas possible d’indiquer si les clés auto-inscrites sont utilisées par une autre fonctionnalité ou application.

- Les dll auto-inscrites sont parfois liées à des dll auxiliaires absentes ou dont la version est incorrecte. En revanche, Windows Installer pouvez inscrire des dll à l’aide des tables de registre sans dépendance sur l’état actuel du système.

- Le code d’auto-inscription peut se voir refuser l’accès aux ressources réseau, telles que les bibliothèques de types, si un composant est à la fois spécifié en tant que source d’exécution à partir de la source et est listé dans la table SelfReg. Cela peut entraîner l’échec de l’installation du composant pendant une installation administrative.

## <a name="see-also"></a>Voir aussi
- [Windows Installer](/windows/desktop/Msi/windows-installer-portal)
- [Inscription du package géré](/previous-versions/bb166783(v=vs.100))