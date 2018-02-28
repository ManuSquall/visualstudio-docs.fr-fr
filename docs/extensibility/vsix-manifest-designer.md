---
title: Concepteur de manifeste VSIX | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VS.Sdk.VsixManifestEditor
helpviewer_keywords:
- vsixmanifest
- vsix manifest
- manifest designer
ms.assetid: 5a691e77-cf91-430d-90ea-361d9031ef83
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 0d7af3ab109c922a8182a93db6852a331229ceca
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="vsix-manifest-designer"></a>Concepteur de manifeste VSIX
Modifie un fichier de manifeste de package VSIX, qui définit le comportement d’installation d’une extension de Visual Studio.  
  
 Le **Concepteur de manifeste VSIX** mappe au schéma VSIX sous-jacent. Chaque élément dans le schéma peut être défini à l’aide d’un contrôle correspondant dans le concepteur. Pour plus d’informations sur le schéma, consultez [une Extension de schéma 2.0 référence VSIX](../extensibility/vsix-extension-schema-2-0-reference.md).  
  
 Pour ouvrir la **Concepteur de manifeste VSIX**, rechercher un fichier source.extension.vsixmanifest dans **l’Explorateur de solutions**, puis ouvrez le fichier. Si le fichier ne contient pas un XML valide, le Concepteur de manifestes n’ouvre pas.  
  
> [!NOTE]
>  Source.extension.vsixmanifest est extension.vsixmanifest lors de la création du package.  
  
## <a name="uielement-list"></a>Liste des éléments d’interface  
 Le **Concepteur de manifeste VSIX** contient quatre sections qui correspondent à ces éléments de niveau supérieur du schéma :  
  
-   Métadonnées  
  
-   Installer des cibles  
  
-   Ressources  
  
-   Dépendances  
  
 La zone de titre contient les contrôles suivants.  
  
 **Nom du produit**  
 Décrit l’extension de nom.  
  
 **ID de produit**  
 Spécifie les informations d’identification unique pour ce package.  
  
 **Auteur**  
 Spécifie le nom de l’auteur de l’extension.  
  
 **Version**  
 Spécifie le numéro de version de l’extension.  
  
 Le **métadonnées** onglet contient les commandes suivantes.  
  
 **Description**  
 Fournit une description de l’extension, à afficher dans **Gestionnaire d’extensions**.  
  
 **Language**  
 Spécifie la langue par défaut pour le package, ce qui correspond aux données textuelles dans le manifeste. Le `Language` attribut suit la convention code paramètres régionaux de common language runtime (CLR) pour les assemblys de ressources, par exemple, en-us, fr, fr-fr. Par défaut, la valeur est neutre ; Cela signifie que le package s’exécute sur n’importe quelle version de langue de Visual Studio.  
  
 **Licence**  
 Spécifie le fichier texte qui contient la licence de l’utilisateur, s’il en existe.  
  
 **Icône**  
 Spécifie le fichier graphique (.png, .bmp, .jpeg, .ico) qui contient l’icône à afficher dans **Gestionnaire d’extensions**, si une icône est présente. L’image d’icône doit être de 32 x 32 pixels ou il doit être redimensionnée pour ces dimensions. Si aucune icône n’est spécifiée, **Gestionnaire d’extensions** utilise une icône par défaut.  
  
 **Image d’aperçu**  
 Spécifie le fichier graphique (.png, .bmp, .jpeg, .ico) qui contient l’image d’aperçu s’affiche dans **Gestionnaire d’extensions**, s’il existe une image d’aperçu. L’image d’aperçu doit être de 200 x 200 pixels. Si aucune image d’aperçu n’est spécifiée, **Gestionnaire d’extensions** utilise une image par défaut.  
  
 **Balises**  
 Ajoute des balises de texte à utiliser pour les indicateurs de recherche.  
  
 **Notes de publication**  
 Spécifie un fichier (.txt, .rtf) qui contient les notes de publication. Prend également l’URL d’un site Web qui affiche les notes de publication.  
  
 **Guide de mise en route**  
 Spécifie un fichier (.txt, .rtf) qui contient des informations sur l’utilisation de l’extension ou le contenu du package VSIX. Ce guide s’affiche lorsque l’installation de l’extension est terminée. Prend également l’URL d’un site Web qui affiche le guide.  
  
 **Plus d’informations URL**  
 Spécifie l’URL d’un site Web qui contient des informations supplémentaires sur le produit.  
  
 Le **cibles d’installation** onglet contient les commandes suivantes.  
  
 **Type d’installation**  
 Répertorie les **Extension Visual Studio** et **SDK d’Extension** comme cible de types d’installation. Les options varient selon le type que vous choisissez.  
  
 **Extension Visual Studio**  
 Répertorie les **le InstallationTarget** éléments qui décrivent comment le package peut être installé et dans les produits Visual Studio cette extension peut être installée. Chaque produit est identifié séparément par nom et une version ou plage.  Produits peuvent être ajoutés à la liste, modifiés et supprimés. Le nom et la version d’un produit correspondent à la **Id** et **Version** attributs associé au **le InstallationTarget** élément.  
  
 **Plage de versions** est [12.0, 14.0] et utilise la notation suivante :  
  
-   [-version minimale incluse  
  
-   ]-version maximale inclus  
  
-   (-version minimale exclusive  
  
-   )-version maximale exclusif  
  
-   Version unique # - uniquement la version spécifiée  
  
 **SDK d’extension**  
 Spécifie une installation globale qui n’est pas limitée à un produit spécifique et une version. **Cible l’identificateur de plateforme** est la plateforme, tels que « Windows », que vous ciblez. **Cibler la Version de la plateforme** est la version, par exemple 8.0, de votre plateforme cible. **Nom du Kit de développement logiciel** et **Version du Kit de développement logiciel** sont le nom et le numéro de version du SDK, respectivement.  
  
 **Ce VSIX est installé pour tous les utilisateurs (nécessite des privilèges élevés lors de l’installation)** case à cocher  
 Si cette case à cocher est activée, cette extension est installée pour tous les utilisateurs ; dans le cas contraire, il est installé uniquement pour l’utilisateur actuel.  
  
 **Ce VSIX est installé par Windows Installer** case à cocher  
 Si cette case à cocher est activée, cette extension est installée par le programme d’installation de Windows (fichier .msi) ; dans le cas contraire, il est installé en tant qu’un package VSIX classique (fichier .vsix).  
  
 Le **actifs** onglet contient les commandes suivantes.  
  
 **Liste des composants**  
 Répertorie les éléments de ressource qui décrivent les éléments d’extension ou le contenu que ce package surfaces. Chaque extension ou un élément de contenu est répertoriée séparément par source, de type et de chemin d’accès. Les éléments de contenu et les extensions peuvent être ajoutés à la liste, modifiés et supprimés. Le type et le chemin d’accès d’un élément d’extension ou le contenu correspond à la `Type` et `Path` attributs associé au `Asset` élément. Les types suivants sont connus :  
  
-   Microsoft.VisualStudio.Package  
  
-   Microsoft.VisualStudio.MefComponent  
  
-   Microsoft.VisualStudio.ToolboxControl  
  
-   Microsoft.VisualStudio.Samples  
  
-   Microsoft.VisualStudio.ProjectTemplate  
  
-   Microsoft.VisualStudio.ItemTemplate  
  
-   Microsoft.VisualStudio.Assembly  
  
-   Microsoft.ExtensionSDK  
  
 Pour ajouter ou modifier un élément multimédia, vous devez spécifier le type de ressource, si l’élément multimédia est un projet dans la solution actuelle ou un fichier dans le système de fichiers et le nom du projet. Vous pouvez également spécifier le nom du dossier dans lequel à incorporer.  
  
 Vous pouvez également créer vos propres types et leur attribuer des noms uniques.  
  
 Le **dépendances** onglet contient les commandes suivantes.  
  
 **Nom, Source et la plage de versions**  
 Répertorie les éléments de dépendance de ce package, qui sont d’autres packages qui dépend de ce package. Si un package de dépendance est spécifié, il doit être installé avant l’installation de ce package ; dans le cas contraire, ce package devez l’installer.  
  
 Packages de dépendance sont spécifiées par l’identificateur de nom, la plage de versions, source et comment la dépendance doit être résolu. Chaque package de dépendance est répertoriée séparément par le nom et la version source. Packages de dépendance peuvent être ajoutés à la liste, modifiés et supprimés.  
  
 L’identificateur doit correspondre à la `ID` attribut de métadonnées du package de dépendance. La source peut être un projet dans la solution actuelle, d’une extension actuellement installée ou d’un fichier. Le **la dépendance est résolue** paramètre peut être le chemin d’accès relatif d’un package imbriqué ou l’URL de l’emplacement de téléchargement de la dépendance. L’ID, la version et la résolution de l’ensemble de dépendance correspondent à la `Id`, `Version`, et `Location` attributs associé au `Dependency` élément.  
  
## <a name="see-also"></a>Voir aussi  
 [Référence de schéma 2.0 Extension VSIX](../extensibility/vsix-extension-schema-2-0-reference.md)   
 [Anatomie d’un package VSIX](../extensibility/anatomy-of-a-vsix-package.md)