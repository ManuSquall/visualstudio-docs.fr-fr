---
title: Concepteur de manifeste VSIX | Microsoft Docs
description: Découvrez comment le concepteur de manifeste VSIX modifie un fichier manifeste de package VSIX, qui définit le comportement d’installation d’une extension Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- VS.Sdk.VsixManifestEditor
helpviewer_keywords:
- vsixmanifest
- vsix manifest
- manifest designer
ms.assetid: 5a691e77-cf91-430d-90ea-361d9031ef83
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: baea7be60c67f186da2372c4644366b4a1a7a202
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112905187"
---
# <a name="vsix-manifest-designer"></a>Concepteur de manifeste VSIX
Modifie un fichier manifeste de package VSIX, qui définit le comportement d’installation d’une extension Visual Studio.

 Le **Concepteur de manifeste VSIX** est mappé au schéma VSIX sous-jacent. Chaque élément du schéma peut être défini à l’aide d’un contrôle correspondant dans le concepteur. Pour plus d’informations sur le schéma, consultez [Référence du schéma d’extension VSIX 2,0](../extensibility/vsix-extension-schema-2-0-reference.md).

 Pour ouvrir le **Concepteur de manifeste VSIX**, localisez un fichier *. extension. vsixmanifest source* dans **Explorateur de solutions**, puis ouvrez le fichier. Si le fichier ne contient pas de code XML valide, le concepteur de manifeste ne s’ouvre pas.

> [!NOTE]
> Le fichier *source. extension. vsixmanifest* est généré dans l' *extension. vsixmanifest* lors de la génération du package.

## <a name="uielement-list"></a>Liste des éléments de l'interface utilisateur
 Le **Concepteur de manifeste VSIX** contient quatre sections qui correspondent à ces éléments de niveau supérieur du schéma :

- Métadonnées

- Installer les cibles

- Éléments multimédias

- Les dépendances

  La zone d’en-tête contient les contrôles suivants.

  **Nom du produit** Décrit le nom de l’extension.

  **ID du produit** Spécifie les informations d’identification uniques pour ce package.

  **Auteur** Spécifie le nom de l’auteur de l’extension.

  **Version** de Spécifie le numéro de version de l’extension.

  L’onglet **métadonnées** contient les contrôles suivants.

  **Description** Fournit une description textuelle de l’extension, à afficher dans le **Gestionnaire d’extensions**.

  **Langue** Spécifie la langue par défaut du package, qui correspond aux données textuelles du manifeste. L' `Language` attribut suit la Convention du code de paramètres régionaux Common Language Runtime (CLR) pour les assemblys de ressources, par exemple, en-US, en, fr-fr. Par défaut, la valeur est neutre, ce qui signifie que le package s’exécute sur n’importe quelle version linguistique de Visual Studio.

  **Licence** Spécifie le fichier texte qui contient la licence utilisateur, si celle-ci est présente.

  **Icône** Spécifie le fichier graphique (*.png*, *.bmp*, *. jpeg*, *. ico*) qui contient l’icône à afficher dans le **Gestionnaire d’extensions**, si une icône est présente. L’image de l’icône doit être de 32x32 pixels ou elle est redimensionnée à ces dimensions. Si aucune icône n’est spécifiée, le **Gestionnaire d’extensions** utilise une icône par défaut.

  **Aperçu** de l’image Spécifie le fichier graphique (*.png*, *.bmp*, *. jpeg*, *. ico*) qui contient l’image d’aperçu à afficher dans le **Gestionnaire d’extensions**, si une image d’aperçu est présente. L’image d’aperçu doit être 200x200 pixels. Si aucune image d’aperçu n’est spécifiée, le **Gestionnaire d’extensions** utilise une image par défaut.

  **Balises** Ajoute des balises de texte à utiliser pour les indicateurs de recherche.

  **Notes de publication** Spécifie un fichier (*.txt*, *. rtf*) qui contient des notes de publication. Prend également l’URL d’un site Web qui affiche les notes de publication.

  **Guide de prise en main** Spécifie un fichier (*.txt*, *. rtf*) qui contient des informations sur l’utilisation de l’extension ou du contenu dans le package VSIX. Ce guide s’affiche lorsque l’installation de l’extension est terminée. Prend également l’URL d’un site Web qui affiche le guide.

  **URL d’informations supplémentaires** Spécifie l’URL d’un site Web qui contient des informations supplémentaires sur le produit.

  L’onglet **installer les cibles** contient les contrôles suivants.

  **Type d’installation** Répertorie les extensions et le **Kit de développement logiciel** de l’extension **Visual Studio** en tant que types d’installation cibles. Les options varient selon le type que vous choisissez.

  **Extension Visual Studio** Répertorie les éléments **le installationtarget** qui décrivent comment le package peut être installé et dans quels produits Visual Studio cette extension peut être installée. Chaque produit est identifié séparément par son nom et par une version ou une plage de versions. Les produits peuvent être ajoutés à la liste, modifiés et supprimés. Le nom et la version d’un produit correspondent aux attributs **ID** et **version** de l’élément **le installationtarget** associé.

  La **plage de versions** est [12,0, 14,0] et utilise la notation suivante :

- [-version minimale incluse

- ]-version inclusive maximale

- (-version minimale exclusive

- )-version exclusive maximale

- Version unique #-seule la version spécifiée

  **SDK d’extension** Spécifie une installation globale qui n’est pas limitée à un produit et une version spécifiques. L’identificateur de la **plateforme cible** est la plateforme, telle que « Windows », que vous ciblez. La version de la **plateforme cible** est la version, telle que 8,0, de votre plateforme cible. **Nom du SDK** et **version du SDK** sont respectivement le nom et le numéro de version du kit de développement logiciel (SDK).

  **Ce VSIX est installé pour tous les utilisateurs (nécessite une élévation lors de l’installation)** Si vous activez cette case à cocher, l’extension est installée pour tous les utilisateurs. dans le cas contraire, il est installé uniquement pour l’utilisateur actuel.

  **Ce VSIX est installé par Windows Installer** Si vous activez cette case à cocher, l’extension est installée par le Windows Installer (fichier *.msi* ); dans le cas contraire, il est installé en tant que package VSIX standard (fichier *. vsix* ).

  L’onglet **ressources** contient les contrôles suivants.

  **Liste des ressources** Répertorie les éléments de ressource qui décrivent l’extension ou les éléments de contenu que ce package couvre. Chaque élément d’extension ou de contenu est listé séparément par la source, le type et le chemin d’accès. Les extensions et les éléments de contenu peuvent être ajoutés à la liste, modifiés et supprimés. Le type et le chemin d’accès d’une extension ou d’un élément de contenu correspondent aux `Type` `Path` attributs et de l' `Asset` élément associé. Les types suivants sont connus :

- Microsoft. VisualStudio. Package

- Microsoft.VisualStudio.MefComponent

- Microsoft. VisualStudio. ToolboxControl

- Microsoft. VisualStudio. Samples

- Microsoft. VisualStudio. ProjectTemplate

- Microsoft. VisualStudio. ItemTemplate

- Microsoft. VisualStudio. assembly

- Microsoft. ExtensionSDK

  Pour ajouter ou modifier un élément multimédia, vous devez spécifier le type de ressource, si la ressource est un projet dans la solution actuelle ou un fichier dans le système de fichiers, et le nom du projet. Vous pouvez également spécifier le nom du dossier dans lequel doit être incorporé.

  Vous pouvez également créer vos propres types et leur attribuer des noms uniques.

  L’onglet **dépendances** contient les contrôles suivants.

  **Nom, source et plage de versions** Répertorie les éléments de dépendance de ce package, qui sont les autres packages dont dépend ce package. Si un package de dépendances est spécifié, il doit être installé avant l’installation de ce package. dans le cas contraire, ce package doit l’installer.

  Les packages de dépendances sont spécifiés par l’identificateur, le nom, la plage de versions, la source et la manière dont la dépendance doit être résolue. Chaque package de dépendances est listé séparément par nom, version et source. Les packages de dépendances peuvent être ajoutés à la liste, modifiés et supprimés.

  L’identificateur doit correspondre à l' `ID` attribut des métadonnées du package de dépendances. La source peut être un projet dans la solution actuelle, une extension actuellement installée ou un fichier. Le paramètre **Comment est résolue la dépendance** peut être le chemin d’accès relatif d’un package imbriqué ou l’URL de l’emplacement de téléchargement pour la dépendance. L’ID, la version et la résolution du package de dépendance correspondent aux `Id` `Version` attributs, et `Location` de l' `Dependency` élément associé.

## <a name="see-also"></a>Voir aussi
- [Informations de référence sur le schéma d’extension VSIX 2,0](../extensibility/vsix-extension-schema-2-0-reference.md)
- [Anatomie d’un package VSIX](../extensibility/anatomy-of-a-vsix-package.md)
