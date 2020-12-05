---
title: Options des paramètres du projet C++
description: Découvrez comment utiliser la page Paramètres du projet VC + + dans la section projets et solutions pour définir les paramètres de génération et de projet C++ relatifs à la journalisation, aux performances et aux types de fichiers de prise en charge.
ms.custom: SEO-VS-2020
ms.date: 08/02/2017
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Projects.VCBuild
helpviewer_keywords:
- builds [Visual Studio], logs
- build process [C++]
- files [Visual Studio], built by C/C++ compiler
- file extensions, built by C or C++ compiler
- cl.exe compiler, file extensions
- extensions, files built by C or C++ compiler
- BuildLog.htm
ms.assetid: 56420efd-6a95-464e-b890-e2b38c48d66a
author: corob-msft
ms.author: corob
manager: markl
ms.workload:
- cplusplus
ms.openlocfilehash: 16226cd66c2cf46d1dc46f1cb3f90dc3bad9658c
ms.sourcegitcommit: 2cf87f79762906ccaa133a7645aa4c77a0bed7da
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2020
ms.locfileid: "96616276"
---
# <a name="vc-project-settings-projects-and-solutions-options-dialog-box"></a>Paramètres du projet VC++, Projets et solutions, boîte de dialogue Options

Cette boîte de dialogue vous permet de définir les paramètres du projet et de la build C++ relatifs à la journalisation, aux performances et à la prise en charge des types de fichiers.

## <a name="to-access-this-dialog-box"></a>Pour accéder à cette boîte de dialogue

1. Dans le menu **Outils** , cliquez sur **Options**.

2. Sélectionnez **Projets et solutions**, puis **Paramètres de projet VC++**.

## <a name="build-logging"></a>Journalisation de la génération

 **Oui**

  Active la création du fichier journal de génération. Cette option génère le fichier BuildLog.htm, qui se trouve dans le répertoire des fichiers intermédiaires du projet. Chaque nouvelle génération remplace le fichier BuildLog.htm précédent.

 **Non**

  Désactive la création du fichier journal de génération.

## <a name="show-environment-in-log"></a>Affichage de l’environnement dans le journal

 **Oui**

Répertorie les variables d’environnement dans le fichier journal de génération. Cette option spécifie d’indiquer le contenu de toutes les variables d’environnement dans le fichier journal de build lors des builds de projets C++.

 **Non**

Exclut les variables d’environnement du fichier journal de génération.

## <a name="build-timing"></a>Minutage de la génération

 **Oui**

  Active le minutage de la génération. Si vous sélectionnez cette option, la durée de la génération est enregistrée dans la fenêtre Sortie. Pour plus d’informations, consultez [Fenêtre Sortie](../../ide/reference/output-window.md).

 **Non**

Désactive le minutage de la génération.

## <a name="maximum-concurrent-c-compilations"></a>Nombre maximal de compilations C++ simultanées

Spécifie le nombre maximal de cœurs de processeur à utiliser pour la compilation C++ parallèle.

## <a name="extensions-to-include"></a>Extensions à inclure

Spécifie les extensions de noms des fichiers qui peuvent être portés dans votre projet.

## <a name="extensions-to-hide"></a>Extensions à masquer

Spécifie les extensions de noms des fichiers qui ne s’affichent pas dans l’**Explorateur de solutions** quand l’option **Afficher tous les fichiers** est activée.

## <a name="build-customization-search-path"></a>Chemin de recherche des personnalisations de la build

Spécifie la liste des répertoires contenant les fichiers .rules, qui vous permettent de définir des règles de génération pour vos projets.

## <a name="solution-explorer-mode"></a>Mode Explorateur de solutions

**Afficher uniquement les fichiers du projet**

Configure l’**Explorateur de solutions** de sorte qu’il n’affiche que les fichiers du projet.

**Afficher tous les fichiers**

Configure l’**Explorateur de solutions** de sorte qu’il affiche les fichiers du projet et les fichiers sur disque dans le dossier du projet.

## <a name="enable-project-caching"></a>Activer la mise en cache du projet

**Oui**

Permet à Visual Studio de mettre en cache les données du projet afin de pouvoir, à l’ouverture suivante du projet, charger ces données mises en cache au lieu de les recalculer à partir des fichiers du projet. L’utilisation de données mises en cache peut accélérer considérablement la vitesse de chargement du projet.

**Non**

N’utilise pas les données de projet mises en cache. Analyse les fichiers projet chaque fois que le projet se charge.

## <a name="see-also"></a>Voir aussi

- [Génération de programmes C/C++](/cpp/build/projects-and-build-systems-cpp)
- [Référence à la génération C/C++](/cpp/build/reference/c-cpp-building-reference)