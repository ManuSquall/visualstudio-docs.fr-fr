---
title: Paramètres de projet VC++, Projets et solutions, boîte de dialogue Options | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
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
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: ef861d13387c013659e5e4c1714680b71896858c
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72657864"
---
# <a name="vc-project-settings-projects-and-solutions-options-dialog-box"></a>Paramètres de projet VC++, Projets et solutions, boîte de dialogue Options
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Cette boîte de dialogue vous permet de définir des paramètres du projet [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)] relatifs à la journalisation de la génération et à la prise en charge des types de fichiers.

### <a name="to-access-this-dialog-box"></a>Pour accéder à cette boîte de dialogue

1. Dans le menu **Outils** , cliquez sur **Options**.

2. Sélectionnez **Projets et solutions**, puis **Paramètres de projet VC++** .

## <a name="build-customization-search-path"></a>Chemin de recherche des personnalisations de la build
 Spécifie la liste des répertoires contenant les fichiers .rules, qui vous permettent de définir des règles de génération pour vos projets.

## <a name="build-logging"></a>Journalisation de la génération
 **Oui** Active la génération du fichier journal de génération. Cette option génère le fichier BuildLog.htm, qui se trouve dans le répertoire des fichiers intermédiaires du projet. Chaque nouvelle génération remplace le fichier BuildLog.htm précédent.

 **Non** Désactive la génération du fichier journal de génération.

## <a name="build-timing"></a>Minutage de la génération
 **Oui** Active le minutage de la génération. Si vous sélectionnez cette option, la durée de la génération est enregistrée dans la fenêtre Sortie. Pour plus d’informations, consultez [Fenêtre Sortie](../../ide/reference/output-window.md).

 **Non** Désactive le minutage de la génération.

## <a name="extensions-to-hide"></a>Extensions à masquer
 Spécifie les extensions de noms des fichiers qui ne s’affichent pas dans l’**Explorateur de solutions** quand l’option **Afficher tous les fichiers** est activée.

## <a name="extensions-to-include"></a>Extensions à inclure
 Spécifie les extensions de noms des fichiers qui peuvent être portés dans votre projet.

## <a name="maximum-concurrent-c-compilations"></a>Nombre maximal de compilations C++ simultanées
 Spécifie le nombre maximal de cœurs de processeur à utiliser pour la compilation C++ parallèle.

## <a name="show-environment-in-log"></a>Affichage de l’environnement dans le journal
 **Oui** Répertorie les variables d’environnement dans le fichier journal de génération. Cette option indique de répercuter toutes les variables d’environnement, lors de la génération de projets [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)], dans le fichier journal de génération.

 **Non** Excluez les variables d’environnement du fichier journal de génération.

## <a name="solution-explorer-mode"></a>Mode Explorateur de solutions
 **Afficher uniquement les fichiers du projet** Configure **Explorateur de solutions** pour afficher uniquement les fichiers du projet.

 **Afficher tous les fichiers** Configure **Explorateur de solutions** pour afficher les fichiers du projet et les fichiers sur le disque dans le dossier du projet.

## <a name="see-also"></a>Voir aussi
 [Génération de cC++ /Programs](https://msdn.microsoft.com/library/fa6ed4ff-334a-4d99-b5e2-a1f83d2b3008) [cC++ /Build de référence](https://msdn.microsoft.com/library/100b4ccf-572c-4d1f-970c-fa0bc0cc0d2d)
