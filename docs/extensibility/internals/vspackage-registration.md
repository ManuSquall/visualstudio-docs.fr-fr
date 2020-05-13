---
title: Inscription VSPackage (fr) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- registration, VSPackages
- VSPackages, registering
ms.assetid: ecd20da8-b04b-4141-a8f4-a2ef91dd597a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a05dec8fbef40143f31f2c0ac484824717ea2e32
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80703922"
---
# <a name="vspackage-registration"></a>Inscription de VSPackage
VSPackages doit [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] vous informer qu’ils sont installés et doivent être chargés. Ce processus est réalisé en écrivant de l’information dans le registre. C’est un travail typique d’un installateur.

> [!NOTE]
> Il s’agit d’une pratique acceptée pendant le développement VSPackage d’utiliser l’auto-enregistrement. Toutefois, [!INCLUDE[vsipprvsip](../../extensibility/includes/vsipprvsip_md.md)] les partenaires ne peuvent pas expédier leurs produits en utilisant l’auto-enregistrement dans le cadre de la configuration.

 Les inscriptions dans un paquet d’installateur Windows sont généralement faites dans le tableau du Registre. Vous pouvez également enregistrer des extensions de fichiers dans le tableau du Registre. Cependant, Windows Install fournit un support intégré grâce à l’identifiant programmatique (ProgId), la classe, l’extension et les tables verbes. Pour plus d’informations, voir [Tableaux de base de données](/windows/desktop/Msi/database-tables).

 Assurez-vous que vos inscriptions de registre sont associées au composant approprié pour votre stratégie côte à côte choisie. Par exemple, les entrées de registre d’un fichier partagé doivent être associées au composant d’installateur Windows de ce fichier. De même, les entrées de registre d’un fichier spécifique à la version doivent être associées au composant de ce fichier. Sinon, l’installation ou la désinstallation [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] de votre VSPackage pour une version de pourrait casser votre VSPackage dans d’autres versions. Pour plus d’informations, voir [Supporting Multiple Versions of Visual Studio](../../extensibility/supporting-multiple-versions-of-visual-studio.md).

> [!NOTE]
> La façon la plus simple de gérer l’enregistrement est d’utiliser les mêmes données dans les mêmes fichiers pour l’enregistrement des développeurs et l’enregistrement du temps d’installation. Par exemple, certains outils d’installateur-développement peuvent consommer le fichier en .reg-format au moment de la construction. Si les développeurs conservent des fichiers .reg pour leur propre développement quotidien et débogage, ces mêmes fichiers peuvent être inclus dans l’installateur automatiquement. Si vous ne pouvez pas partager automatiquement les données d’enregistrement, vous devez vous assurer que la copie des données d’enregistrement de l’installateur est à jour.

## <a name="registering-unmanaged-vspackages"></a>Enregistrement des VSPackages non mentés
 Les VSPackages non gérants (y compris ceux générés par le Visual Studio Package Template) utilisent des fichiers .rgs de type ATL pour stocker les informations d’enregistrement. Le format de fichier .rgs est spécifique à ATL et ne peut généralement pas être consommé tel quel par un outil de rédaction d’installation. Les informations d’inscription pour l’installateur VSPackage doivent être conservées séparément. Par exemple, les développeurs peuvent garder les fichiers en format .reg en synchronisation avec les modifications de fichiers .rgs. Les fichiers .reg peuvent être fusionnés avec RegEdit pour des travaux de développement ou consommés par un installateur.

## <a name="registering-managed-vspackages"></a>Enregistrement des VSPackages gérés
 L’outil RegPkg lit les attributs d’enregistrement d’un VSPackage géré et peut soit écrire les informations directement au registre ou écrire des fichiers .reg-format qui peuvent être consommés par un installateur.

> [!NOTE]
> L’outil RegPkg n’est pas redistributable et ne peut pas être utilisé pour enregistrer un VSPackage sur le système d’un utilisateur.

## <a name="why-vspackages-should-not-self-register-at-install-time"></a>Pourquoi VSPackages ne devrait pas s’auto-enregistrer à l’heure d’installation
 Vos installateurs VSPackage ne doivent pas compter sur l’auto-enregistrement. À première vue, garder les valeurs de registre d’un VSPackage seulement dans le VSPackage lui-même semble être une bonne idée. Étant donné que les développeurs ont besoin des valeurs de registre disponibles pour leur travail de routine et les tests, il est logique d’éviter de maintenir une copie distincte des données du registre dans l’installateur. L’installateur peut compter sur le VSPackage lui-même pour écrire les valeurs du registre.

 Bien que bon en théorie, l’auto-enregistrement a plusieurs défauts qui le rendent impropre à l’installation VSPackage:

- L’installation, la non-réinstallation, le recul de l’installation et la mise en retrait de la non-réinstallation vous obligent à écrire quatre actions personnalisées pour chaque VSPackage géré qui s’auto-enregistre en appelant RegPkg.

- Votre approche du support côte à côte pourrait exiger que vous auteurez quatre actions personnalisées qui [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]invoquent RegSvr32 ou RegPkg pour chaque version prise en charge de .

- Une installation avec des modules auto-enregistrés ne peut pas être annulée en toute sécurité parce qu’il n’y a aucun moyen de dire si les clés auto-enregistrées sont utilisées par une autre fonctionnalité ou application.

- Les DLL auto-enregistrés sont parfois liés à des LPL auxiliaires qui ne sont pas présentes ou qui ne sont pas la mauvaise version. En revanche, Windows Install peut enregistrer les LPL en utilisant les tables de registre sans dépendance à l’état actuel du système.

- Le code d’auto-enregistrement peut se voir refuser l’accès aux ressources réseau, telles que les bibliothèques de type, si un composant est à la fois spécifié comme étant géré par source et est inscrit dans le tableau SelfReg. Cela peut entraîner l’échec de l’installation du composant lors d’une installation administrative.

## <a name="see-also"></a>Voir aussi
- [Installateur Windows](/windows/desktop/Msi/windows-installer-portal)
- [Enregistrement des colis gérés](https://msdn.microsoft.com/library/f69e0ea3-6a92-4639-8ca9-4c9c210e58a1)
