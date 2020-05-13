---
title: CONCEPTEUR de manifeste VSIX (fr) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- VS.Sdk.VsixManifestEditor
helpviewer_keywords:
- vsixmanifest
- vsix manifest
- manifest designer
ms.assetid: 5a691e77-cf91-430d-90ea-361d9031ef83
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 30620e0fe91d0e90995d2d2f721950f878c65fdc
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697891"
---
# <a name="vsix-manifest-designer"></a>Concepteur de manifeste VSIX
Modifie un fichier manifeste de paquet VSIX, qui définit le comportement d’installation pour une extension visual Studio.

 Le **CONCEPTEUR de manifeste VSIX** cartes au schéma sous-jacent VSIX. Chaque élément du schéma peut être défini à l’aide d’un contrôle correspondant dans le concepteur. Pour plus d’informations sur le schéma, voir [VSIX Extension Schema 2.0 Référence](../extensibility/vsix-extension-schema-2-0-reference.md).

 Pour ouvrir le **concepteur de manifeste VSIX**, localiser un fichier *source.extension.vsixmanifest* dans **Solution Explorer**, et ouvrir le fichier. Si le fichier ne contient pas de XML valide, le concepteur manifeste ne s’ouvrira pas.

> [!NOTE]
> Le fichier *source.extension.vsixmanifest* est la sortie à *extension.vsixmanifest* lorsque le paquet est construit.

## <a name="uielement-list"></a>Liste des éléments de l'interface utilisateur
 Le **concepteur de manifeste VSIX** contient quatre sections qui correspondent à ces éléments de haut niveau du schéma :

- Métadonnées

- Installer des cibles

- Éléments multimédias

- Les dépendances

  La zone de cap contient les commandes suivantes.

  **Nom du produit** Décrit le nom d’extension.

  **ID produit** Spécifie les informations d’identification uniques pour ce paquet.

  **Auteur** Spécifie le nom de l’auteur de l’extension.

  **Version** Spécifie le numéro de version de l’extension.

  **L’onglet Métadonnées** contient les commandes suivantes.

  **Description** Fournit une description textuelle de l’extension, qui sera affichée dans **Extension Manager**.

  **Langue** Spécifie le langage par défaut du paquet, qui correspond aux données textuelles dans le manifeste. L’attribut `Language` suit la convention de code local de l’heure courante (CLR) pour les assemblages de ressources, par exemple, en-us, fr-fr. Par défaut, la valeur est neutre, ce qui signifie que le paquet s’exécutera sur n’importe quelle version linguistique de Visual Studio.

  **Licence** Spécifie le fichier texte qui contient la licence utilisateur, si l’on est présent.

  **Icône** Spécifie le fichier graphique (*.png*, *.bmp*, *.jpeg*, *.ico*) qui contient l’icône à afficher dans **Extension Manager**, si une icône est présente. L’image d’icône doit être 32x32 pixels ou elle est resized à ces dimensions. Si aucune icône n’est spécifiée, **Le gestionnaire d’extension** utilise une icône par défaut.

  **Aperçu de l’image** Spécifie le fichier graphique (*.png*, *.bmp*, *.jpeg*, *.ico*) qui contient l’image de prévisualisation à afficher dans **Extension Manager**, si une image de prévisualisation est présente. L’image de prévisualisation doit être 200x200 pixels. Si aucune image de prévisualisation n’est spécifiée, **Le gestionnaire d’extension** utilise une image par défaut.

  **Tags** Ajoute des balises de texte à utiliser pour les conseils de recherche.

  **Notes de sortie** Spécifie un fichier (*.txt*, *.rtf*) qui contient des notes de sortie. Prend également l’URL d’un site Web qui affiche les notes de sortie.

  **Guide de démarrage** Spécifie un fichier (*.txt*, *.rtf*) qui contient des informations sur la façon d’utiliser l’extension ou le contenu dans le paquet VSIX. Ce guide apparaît lorsque l’installation d’extension est terminée. Prend également l’URL d’un site Web qui affiche le guide.

  **Plus d’info URL** Spécifie l’URL d’un site Web qui contient des informations supplémentaires sur le produit.

  **L’onglet Cibles d’installation** contient les commandes suivantes.

  **Type d’installation** Répertorie **Visual Studio Extension** et Extension **SDK** comme types d’installation cible. Les options diffèrent, selon le type que vous choisissez.

  **Extension de studio visuel** Répertorie les éléments **InstallationTarget** qui décrivent comment le paquet peut être installé et dans lequel les produits Visual Studio cette extension peuvent être installés. Chaque produit est identifié séparément par son nom et une version ou une gamme de version. Les produits peuvent être ajoutés à la liste, modifiés et supprimés. Le nom et la version d’un produit correspondent aux attributs **Id** et **Version** de l’élément **InstallationTarget** associé.

  **La gamme de versions** est [12.0, 14.0] et utilise la notation suivante :

- [ - version minimale inclusive

- ] - version maximale inclusive

- ( - version minimale exclusive

- ) - version maximale exclusive

- Version unique - seule la version spécifiée

  **Extension SDK** Spécifie une installation globale qui n’est pas étendue à un produit et une version spécifiques. **Target Platform Identifier** est la plate-forme, telle que "Windows", que vous ciblez. **Target Platform Version** est la version, comme 8.0, de votre plate-forme cible. **SDK Name** et **SDK Version** sont le nom et le numéro de version du SDK, respectivement.

  **Ce VSIX est installé pour tous les utilisateurs (nécessite l’élévation sur l’installation)** Si vous sélectionnez cette case à cocher, l’extension est installée pour tous les utilisateurs; sinon, il est installé uniquement pour l’utilisateur actuel.

  **Ce VSIX est installé par Windows Install** Si vous sélectionnez cette case à cocher, l’extension est installée par l’installateur Windows ( fichier *.msi);* sinon, il est installé comme un package VSIX typique ( fichier *.vsix).*

  **L’onglet Actifs** contient les contrôles suivants.

  **Liste des actifs** Répertorie les éléments d’actif qui décrivent les éléments d’extension ou de contenu que ce paquet fait surface. Chaque élément d’extension ou de contenu est répertorié séparément par source, type et chemin. Les extensions et les éléments de contenu peuvent être ajoutés à la liste, modifiés et supprimés. Le type et le chemin d’un `Type` élément `Path` d’extension `Asset` ou de contenu correspondent aux attributs et aux attributs de l’élément associé. Les types suivants sont connus :

- Microsoft.VisualStudio.Package (en anglais seulement)

- Microsoft.VisualStudio.MefComponent

- Microsoft.VisualStudio.ToolboxControl (en anglais seulement)

- Microsoft.VisualStudio.Échantillons

- Microsoft.VisualStudio.ProjectTemplate (en anglais seulement)

- Microsoft.VisualStudio.ItemTemplate (en anglais seulement)

- Microsoft.VisualStudio.Assembly (en anglais seulement)

- Microsoft.ExtensionSDK (en)

  Pour ajouter ou modifier un actif, vous devez spécifier le type d’actif, que l’actif soit un projet dans la solution actuelle ou un fichier dans le système de fichiers, et le nom du projet. Vous pouvez également spécifier le nom du dossier dans lequel il faut encastrer.

  Vous pouvez également créer vos propres types et leur donner des noms uniques.

  **L’onglet Dépendances** contient les contrôles suivants.

  **Gamme de noms, de source et de version** Répertorie les éléments de dépendance de ce paquet, qui sont d’autres paquets dont ce paquet dépend. Si un paquet de dépendance est spécifié, il doit être installé avant l’installation de ce paquet; sinon, ce paquet doit l’installer.

  Les paquets de dépendance sont spécifiés par identifiant, nom, plage de version, source, et comment la dépendance doit être résolue. Chaque paquet de dépendance est répertorié séparément par nom, version et source. Les paquets de dépendance peuvent être ajoutés à la liste, modifiés et supprimés.

  L’identifiant doit `ID` correspondre à l’attribut des métadonnées du paquet dépendance. La source peut être un projet dans la solution actuelle, une extension actuellement installée, ou un fichier. Le **réglage comment la dépendance est résolue** peut être le chemin relatif d’un paquet imbriqué ou l’URL de l’emplacement de téléchargement pour la dépendance. L’ID, la version et la résolution du `Id` `Version`paquet `Location` de dépendance correspondent `Dependency` à la , et les attributs de l’élément associé.

## <a name="see-also"></a>Voir aussi
- [SCHÉMA d’extension VSIX 2.0 référence](../extensibility/vsix-extension-schema-2-0-reference.md)
- [Anatomie d’un paquet VSIX](../extensibility/anatomy-of-a-vsix-package.md)
