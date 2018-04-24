---
title: Gérer les outils externes | Microsoft Docs
ms.custom: ''
ms.date: 11/20/2017
ms.technology:
- vs-ide-general
ms.topic: conceptual
f1_keywords:
- vs.externaltools
helpviewer_keywords:
- external tools [Visual Studio]
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ea718d2170d058897db4bfa7a9a2cfc32da563a1
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="manage-external-tools"></a>Gérer les outils externes

Vous pouvez appeler des outils externes depuis Visual Studio en utilisant le menu **Outils**. Certains outils par défaut sont disponibles dans le menu **Outils** et vous pouvez personnaliser le menu en ajoutant vos propres exécutables.

## <a name="tools-available-on-the-tools-menu"></a>Outils disponibles dans le menu Outils

Le menu **Outils** contient plusieurs commandes prédéfinies comme :

* **Extensions et mises à jour** pour [gérer les extensions Visual Studio](finding-and-using-visual-studio-extensions.md)
* **Gestionnaire des extraits de code...** pour [organiser les extraits de code](code-snippets.md)
* **PreEmptive Protection - Dotfuscator** pour lancer [Dotfuscator Community Edition (CE)](dotfuscator/index.md) s’il est [installé](dotfuscator/install.md)
* **Personnaliser...** pour [personnaliser les menus et les barres d’outils](how-to-customize-menus-and-toolbars-in-visual-studio.md)
* **Options...** pour [définir différentes options de l’IDE Visual Studio et d’autres outils](reference/options-dialog-box-visual-studio.md)

## <a name="add-new-tools-to-the-tools-menu"></a>Ajouter de nouveaux outils au menu Outils

Vous pouvez ajouter un outil externe pour qu’il s’affiche dans le menu **Outils**.

1. Ouvrez la boîte de dialogue **Outils externes** en choisissant **Outils** > **Outils externes...**

1. Cliquez sur **Ajouter** et renseignez les informations. Par exemple, l'entrée suivante peut provoquer l'ouverture de l'Explorateur Windows dans le répertoire du fichier qui est actuellement ouvert dans Visual Studio :

   * Titre : `Open File Location`

   * Commande : `explorer.exe`

   * Arguments : `/root, "$(ItemDir)"`

   ![Boîte de dialogue Outils externes](media/external-tools-dialog.png)

Voici une liste complète des arguments qui peuvent être utilisés lors de la définition d’un outil externe :

|Name|Argument|Description|  
|----------|--------------|-----------------|  
|Chemin d'accès de l'élément|$(ItemPath)|Nom complet du fichier actif (lecteur + chemin d'accès + nom de fichier).|  
|Répertoire de l'élément|$(ItemDir)|Répertoire du fichier actif (lecteur + chemin d'accès).|  
|Nom de fichier de l'élément|$(ItemFilename)|Nom du fichier actif (nom de fichier).|  
|Extension de l'élément|$(ItemExt)|Extension du nom du fichier actif.|  
|Ligne active|$(CurLine)|Position de la ligne active du curseur dans la fenêtre de code.|  
|Colonne active.|$(CurCol)|Position de la colonne active du curseur dans la fenêtre de code.|  
|Texte actif|$(CurText)|Texte sélectionné.|  
|Chemin d'accès cible|$(TargetPath)|Nom de fichier complet de l'élément à générer (lecteur + chemin d'accès + nom de fichier).|  
|Répertoire cible|$(TargetDir)|Répertoire de l'élément à générer.|  
|Nom cible|$(TargetName)|Nom de fichier de l'élément à générer.|  
|Extension cible|$(TargetExt)|Extension de nom de fichier de l'élément à générer.|  
|Répertoire binaire|$(BinDir)|Emplacement final du binaire en cours de génération (sous la forme lecteur + chemin d’accès).|  
|Répertoire du projet|$(ProjDir)|Répertoire du projet actif (lecteur + chemin d'accès).|  
|Nom du fichier projet|$(ProjFileName)|Nom de fichier du projet actif (lecteur + chemin d'accès + nom de fichier).|  
|Répertoire de la solution|$(SolutionDir)|Répertoire de la solution active (lecteur + chemin d'accès).|  
|Nom du fichier solution|$(SolutionFileName)|Nom de fichier de la solution active (lecteur + chemin d’accès + nom de fichier).|

> [!NOTE]
> La barre d'état IDE affiche les variables Ligne active et Colonne active pour indiquer l'emplacement du point d'insertion dans l'éditeur de code actif. La variable Texte actif retourne le texte ou le code sélectionné à cet emplacement.

## <a name="see-also"></a>Voir aussi

[Outils de génération C/C++](/cpp/build/reference/c-cpp-build-tools)
