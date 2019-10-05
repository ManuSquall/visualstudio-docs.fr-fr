---
title: Propriétés générales du projet (Android C++) | Microsoft Docs
ms.custom: ''
ms.date: 10/23/2017
ms.technology: vs-ide-mobile
ms.topic: conceptual
ms.assetid: 65f4868b-b864-4989-a275-1e51869ef599
author: corob-msft
ms.author: corob
manager: jillfra
f1_keywords:
- VC.Project.VCConfiguration.OutputDirectory
- VC.Project.VCConfiguration.IntermediateDirectory
- VC.Project.VCConfiguration.TargetName
- VC.Project.VCConfiguration.TargetExt
- VC.Project.VCConfiguration.DeleteExtensionsOnClean
- VC.Project.VCConfiguration.BuildLogFile
- VC.Project.VCConfiguration.PlatformToolset
- VC.Project.VCConfiguration.ConfigurationType
- VC.Project.VCConfiguration.DeleteExtensionsOnClean
- VC.Project.VCConfiguration.UseOfSTL
- VC.Project.VCConfiguration.ThumbMode
ms.workload:
- xplat-cplusplus
ms.openlocfilehash: 4526a329b4e047a449995b7b5ef66362aff1cc8f
ms.sourcegitcommit: 6ae0a289f1654dec63b412bfa22035511a2ef5ad
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/04/2019
ms.locfileid: "71950585"
---
# <a name="general-project-properties-android-c"></a>Propriétés générales du projet (Android C++)

Propriété | Description | Options
--- | ---| ---
Répertoire de sortie | Spécifie un chemin relatif vers le répertoire de fichiers de sortie ; peut inclure des variables d’environnement.
Répertoire intermédiaire | Spécifie un chemin relatif vers le répertoire de fichiers intermédiaire ; peut inclure des variables d’environnement.
Nom de la cible | Spécifie un nom de fichier généré par ce projet.
Extension cible | Spécifie une extension de fichier générée par ce projet. (Exemple : *.exe* ou *.dll*)
Extensions à supprimer lors du nettoyage | Spécification de caractères génériques séparés par des points-virgules pour les fichiers du répertoire intermédiaire à supprimer durant le nettoyage ou la regénération.
Fichier journal de génération | Spécifie le fichier journal de génération à utiliser quand la journalisation de la génération est activée.
Ensemble d'outils de plateforme | Spécifie l’ensemble d’outils utilisé pour générer la configuration actuelle ; s’il n’est pas défini, l’ensemble d’outils par défaut est utilisé
Type de configuration | Spécifie le type de sortie générée par cette configuration. | **Bibliothèque dynamique (.so)** : bibliothèque dynamique ( *.so*)<br>**Bibliothèque statique (.a)** : bibliothèque statique ( *.a*)<br>**Utilitaire** : utilitaire<br>**Makefile** : makefile<br>
Niveau d’API cible | Niveau d’API du Kit de développement natif (NDK) Android ciblé par cette configuration.
Utilisation de STL | Spécifie la bibliothèque C++ standard à utiliser pour cette configuration. | **Bibliothèque minimale runtime C++ (system)**<br>**Bibliothèque statique runtime C++ (gabi++_static)**<br>**Bibliothèque partagée runtime C++ (gabi++_shared)**<br>**Bibliothèque statique runtime STLport (stlport_static)**<br>**Bibliothèque partagée runtime STLport (stlport_shared)**<br>**Bibliothèque statique GNU STL (gnustl_static)**<br>**Bibliothèque partagée GNU STL (gnustl_shared)**<br>**Bibliothèque statique LLVM libc++ (c++_static)**<br>**Bibliothèque partagée LLVM libc++ (c++_shared)**<br>
Mode Thumb | Générez du code qui s’exécute pour une microarchitecture Thumb. Applicable uniquement à l’architecture ARM. | **Thumb**<br>**ARM**<br>**Désactivé**<br>
