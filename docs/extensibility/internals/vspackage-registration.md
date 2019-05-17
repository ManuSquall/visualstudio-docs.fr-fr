---
title: L’inscription de VSPackage | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- registration, VSPackages
- VSPackages, registering
ms.assetid: ecd20da8-b04b-4141-a8f4-a2ef91dd597a
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f9fc6bf6b096cfc5f961164abeb4703e2a18f1d2
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63429528"
---
# <a name="vspackage-registration"></a>Inscription de VSPackage
Les VSPackages doivent informer [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] qu’ils sont installés et qu’il doivent être chargé. Ce processus s’effectue en écrivant des informations dans le Registre. C’est une tâche classique d’un programme d’installation.

> [!NOTE]
> Il est une pratique acceptée pendant le développement VSPackage à utiliser l’inscription automatique. Toutefois, [!INCLUDE[vsipprvsip](../../extensibility/includes/vsipprvsip_md.md)] partenaires n’est pas livrable leurs produits à l’aide de l’inscription automatique dans le cadre du programme d’installation.

 Les entrées de Registre dans un package Windows Installer sont généralement effectuées dans la table de Registre. Vous pouvez également inscrire des extensions de fichier dans la table de Registre. Toutefois, le programme d’installation de Windows fournit une prise en charge intégrée via l’identificateur programmatique (ProgId), classe, extension et les tables de verbe. Pour plus d’informations, consultez [les Tables de base de données](/windows/desktop/Msi/database-tables).

 N’oubliez pas que vos entrées de Registre associés avec le composant qui convient à votre stratégie côte à côte choisie. Par exemple, les entrées de Registre d’un fichier partagé doivent être associées au composant du programme d’installation Windows de ce fichier. De même, les entrées de Registre pour un fichier spécifique à la version doivent être associées à composant de ce fichier. Sinon, l’installation ou la désinstallation de votre VSPackage pour une version de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] endommage votre VSPackage dans les autres versions. Pour plus d’informations, consultez [prenant en charge plusieurs Versions de Visual Studio](../../extensibility/supporting-multiple-versions-of-visual-studio.md)

> [!NOTE]
> Pour gérer l’inscription, le plus simple consiste à utiliser les mêmes données dans les mêmes fichiers pour développeur d’enregistrement et d’inscription du moment de l’installation. Par exemple, certains outils de développement de programme d’installation peuvent consommer le fichier au format .reg au moment de la génération. Si les développeurs gardent le fichiers .reg pour leurs propres quotidiennes de développement et débogage, ces mêmes fichiers peuvent être inclus dans le programme d’installation automatiquement. Si vous ne pouvez pas partager automatiquement les données d’inscription, vous devez vous assurer que la copie du programme d’installation des données d’inscription est en cours.

## <a name="registering-unmanaged-vspackages"></a>L’inscription de VSPackages non managés
 Les VSPackages non managés (y compris celles générées par le modèle de Package Visual Studio) utiliser les fichiers .rgs ATL-style pour stocker les informations d’inscription. Le format de fichier .rgs est spécifique à ATL et généralement ne peut pas être consommé en tant que-est à l’aide d’une installation d’outil de création. Informations d’inscription pour le programme d’installation de package Visual Studio doivent être gérées séparément. Par exemple, les développeurs peuvent synchroniser les fichiers au format .reg avec .rgs les modifications de fichier. Fichiers .reg peuvent être fusionnées avec RegEdit pour le travail de développement ou consommées par un programme d’installation.

## <a name="registering-managed-vspackages"></a>L’inscription de VSPackages gérés
 L’outil RegPkg lit les attributs d’inscription à partir d’un VSPackage managé et peut écrire les informations directement au Registre ou écrire des fichiers au format .reg qui peuvent être utilisés par un programme d’installation.

> [!NOTE]
> L’outil RegPkg n’est pas redistribuable et ne peut pas être utilisé pour inscrire un VSPackage sur le système d’un utilisateur.

## <a name="why-vspackages-should-not-self-register-at-install-time"></a>Pourquoi les VSPackages ne doivent pas s’inscrire automatiquement au moment de l’installation
 Vos programmes d’installation de package Visual Studio ne doivent pas dépendre de l’inscription automatique. À première vue, conservation des valeurs de Registre d’un VSPackage uniquement dans le VSPackage lui-même semble être une bonne idée. Étant donné que les développeurs ont besoin les valeurs de Registre disponibles pour leurs tâches de routine et de test, il est judicieux pour éviter de maintenir une copie distincte des données de Registre dans le programme d’installation. Le programme d’installation peut reposer sur le VSPackage lui-même à écrire des valeurs de Registre.

 Lors de la bonne en théorie, l’inscription automatique a plusieurs défauts qui ne sont pas adaptés pour l’installation de package Visual Studio :

- Prise en charge correctement de l’installation, désinstallation, restauration de l’installation et la désinstallation rollback vous oblige à créer quatre actions personnalisées pour chaque VSPackage managé qui s’inscrit automatiquement en appelant RegPkg.

- Votre approche de prise en charge côte à côte peut nécessiter que vous créez quatre actions personnalisées qui appellent RegSvr32 ou RegPkg pour chaque version prise en charge de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].

- Une installation avec modules inscrits automatiquement ne peut pas être restaurée en toute sécurité car il n’existe aucun moyen de déterminer si les clés inscrits automatiquement sont utilisées par une autre fonctionnalité ou une application.

- DLL auto-enregistrer lient parfois à des DLL auxiliaires qui ne sont pas présents ou sont une mauvaise version. En revanche, le programme d’installation de Windows peuvent inscrire des DLL à l’aide de tables Registre sans dépendance sur l’état actuel du système.

- Code d’auto-inscription peut être refusé l’accès aux ressources réseau, telles que des bibliothèques de types, si un composant est à la fois spécifié en tant que l’exécution à partir de la source et est répertorié dans la table SelReg. Cela peut entraîner l’installation du composant échoue pendant une installation administrative.

## <a name="see-also"></a>Voir aussi
- [Windows Installer](/windows/desktop/Msi/windows-installer-portal)
- [Inscription de Package gérée](https://msdn.microsoft.com/library/f69e0ea3-6a92-4639-8ca9-4c9c210e58a1)