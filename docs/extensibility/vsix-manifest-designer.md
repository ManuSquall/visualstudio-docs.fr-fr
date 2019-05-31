---
title: Concepteur de manifeste VSIX | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- VS.Sdk.VsixManifestEditor
helpviewer_keywords:
- vsixmanifest
- vsix manifest
- manifest designer
ms.assetid: 5a691e77-cf91-430d-90ea-361d9031ef83
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7c13d32ab6b91dce94bab307f6bbc6744f9c17a0
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66322834"
---
# <a name="vsix-manifest-designer"></a>Concepteur de manifeste VSIX
Modifie un fichier de manifeste de package VSIX, qui définit le comportement d’installation pour une extension Visual Studio.

 Le **Concepteur de manifeste VSIX** mappe au schéma VSIX sous-jacent. Chaque élément dans le schéma peut être définie à l’aide d’un contrôle correspondant dans le concepteur. Pour plus d’informations sur le schéma, consultez [VSIX Extension de schéma 2.0 référence](../extensibility/vsix-extension-schema-2-0-reference.md).

 Pour ouvrir le **Concepteur de manifeste VSIX**, recherchez un *source.extension.vsixmanifest* de fichiers dans **l’Explorateur de solutions**et ouvrez le fichier. Si le fichier ne contient pas de fichier XML valide, le Concepteur de manifeste ne s’ouvre.

> [!NOTE]
> Le *source.extension.vsixmanifest* la sortie de fichier à *extension.vsixmanifest* lorsque la génération du package.

## <a name="uielement-list"></a>Liste UIElement
 Le **Concepteur de manifeste VSIX** contient quatre sections qui correspondent à ces éléments de niveau supérieur du schéma :

- Métadonnées

- Les cibles d’installation

- Assets

- Dépendances

  La zone de titre contient les contrôles suivants.

  **Nom de produit** décrit le nom d’extension.

  **ID de produit** spécifie les informations d’identification unique pour ce package.

  **Auteur** Spécifie le nom de l’auteur de l’extension.

  **Version** Spécifie le numéro de version de l’extension.

  Le **métadonnées** onglet contient les contrôles suivants.

  **Description** fournit une description textuelle de l’extension, à afficher dans **Gestionnaire d’extensions**.

  **Langage** spécifie la langue par défaut pour le package, ce qui correspond aux données textuelles dans le manifeste. Le `Language` attribut suit la convention code paramètres régionaux de common language runtime (CLR) pour les assemblys de ressource, par exemple, en-us, fr, fr-fr. Par défaut, la valeur est neutre, ce qui signifie que le package s’exécute sur n’importe quelle version linguistique de Visual Studio.

  **Licence** Spécifie le fichier texte qui contient la licence utilisateur, s’il en existe.

  **Icône** Spécifie le fichier graphique ( *.png*, *.bmp*, *.jpeg*, *.ico*) qui contient l’icône à afficher dans **Gestionnaire d’extensions**, si une icône est présente. L’image d’icône doit être de 32 x 32 pixels ou il est redimensionné à ces dimensions. Si aucune icône n’est spécifiée, **Gestionnaire d’extensions** utilise une icône par défaut.

  **Image d’aperçu** Spécifie le fichier graphique ( *.png*, *.bmp*, *.jpeg*, *.ico*) qui contient l’image d’aperçu afficher dans **Gestionnaire d’extensions**, si une image d’aperçu est présente. L’image d’aperçu doit être 200 x 200 pixels. Si aucune image d’aperçu n’est spécifiée, **Gestionnaire d’extensions** utilise une image par défaut.

  **Balises** ajoute des balises de texte à utiliser pour les indicateurs de recherche.

  **Notes de publication** spécifie un fichier ( *.txt*, *.rtf*) qui contient les notes de publication. Prend également l’URL d’un site Web qui affiche les notes de publication.

  **Guide de démarrage** spécifie un fichier ( *.txt*, *.rtf*) qui contient des informations sur l’utilisation de l’extension ou le contenu du package VSIX. Ce guide s’affiche lorsque l’installation de l’extension est terminée. Prend également l’URL d’un site Web qui affiche le guide.

  **URL informations** Spécifie l’URL d’un site Web qui contient des informations supplémentaires sur le produit.

  Le **cibles d’installation** onglet contient les contrôles suivants.

  **Type d’installation** répertorie **Extension Visual Studio** et **SDK d’Extension** comme cible de types d’installation. Les options diffèrent en fonction du type que vous choisissez.

  **Extension Visual Studio** répertorie le **le InstallationTarget** éléments qui décrivent comment le package peut être installé et dans les produits Visual Studio cette extension peut être installée. Chaque produit est identifié séparément par nom et une version ou plage. Produits peuvent être ajoutés à la liste, modifiés et supprimés. Le nom et la version d’un produit correspondent à la **Id** et **Version** attributs associé **le InstallationTarget** élément.

  **Plage de versions** est [12.0, 14.0] et utilise la notation suivante :

- [-version minimale inclusive

- ]-version maximale inclusive

- (-version minimale exclusive

- )-version maximale exclusive

- Version unique # - uniquement la version spécifiée

  **Kit SDK d’extension** spécifie une installation globale qui n’est pas limitée à un produit spécifique et une version. **Identificateur de plateforme cible** est la plateforme, tels que « Windows », que vous ciblez. **Cibler la Version de la plateforme** est la version, par exemple 8.0, de votre plateforme cible. **Nom du SDK** et **Version du SDK** sont le nom et le numéro de version du SDK, respectivement.

  **Cet extension VSIX est installé pour tous les utilisateurs (nécessite une élévation lors de l’installation)** si vous sélectionnez cette case à cocher, l’extension est installée pour tous les utilisateurs ; sinon, elle est installée uniquement pour l’utilisateur actuel.

  **Cet extension VSIX est installé par le programme d’installation de Windows** si vous sélectionnez cette case à cocher, l’extension est installée par le programme d’installation de Windows ( *.msi* fichier) ; sinon, il est installé comme un package VSIX standard ( *.vsix*  fichier).

  Le **actifs** onglet contient les contrôles suivants.

  **Liste de biens** répertorie les éléments de ressource qui décrivent les éléments d’extension ou le contenu que ce package des surfaces. Chaque extension ou un élément de contenu est répertoriée séparément par source, de type et de chemin d’accès. Extensions et le contenu des éléments peuvent être ajoutés à la liste, modifiés et supprimés. Le type et le chemin d’accès d’un élément d’extension ou le contenu correspond à la `Type` et `Path` attributs associé `Asset` élément. Les types suivants sont connus :

- Microsoft.VisualStudio.Package

- Microsoft.VisualStudio.MefComponent

- Microsoft.VisualStudio.ToolboxControl

- Microsoft.VisualStudio.Samples

- Microsoft.VisualStudio.ProjectTemplate

- Microsoft.VisualStudio.ItemTemplate

- Microsoft.VisualStudio.Assembly

- Microsoft.ExtensionSDK

  Pour ajouter ou modifier un élément multimédia, vous devez spécifier le type de ressource, si la ressource est un projet dans la solution actuelle ou un fichier dans le système de fichiers et le nom du projet. Vous pouvez également spécifier le nom du dossier dans lequel à incorporer.

  Vous pouvez également créer vos propres types et leur donner des noms uniques.

  Le **dépendances** onglet contient les contrôles suivants.

  **Nom Source et la plage de versions** répertorie les éléments de dépendance de ce package, qui sont des autres packages qui dépend de ce package. Si un package de dépendance est spécifié, il doit être installé avant l’installation de ce package ; Sinon, ce package devez l’installer.

  Packages de dépendance sont spécifiées par l’identificateur de nom, plage de versions, source et comment la dépendance doit être résolu. Chaque package de dépendance est répertoriée séparément par le nom et la version source. Packages de dépendance peuvent être ajoutés à la liste, modifiés et supprimés.

  L’identificateur doit correspondre à la `ID` attribut de métadonnées de package de dépendance. La source peut être un projet dans la solution actuelle, une extension actuellement installée ou un fichier. Le **est la dépendance est résolue** paramètre peut être le chemin d’accès relatif d’un package imbriqué ou l’URL de l’emplacement de téléchargement de la dépendance. L’ID, la version et la résolution du package de dépendance correspondent à la `Id`, `Version`, et `Location` attributs associé `Dependency` élément.

## <a name="see-also"></a>Voir aussi
- [Référence de schéma 2.0 d’extension VSIX](../extensibility/vsix-extension-schema-2-0-reference.md)
- [Anatomie d’un package VSIX](../extensibility/anatomy-of-a-vsix-package.md)