---
title: Page Références, Concepteur de projet (Visual Basic) │ Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- vb.ProjectPropertiesReference
- vb.ProjectPropertiesUnusedReference
- vb.ProjectPropertiesReferencePaths
helpviewer_keywords:
- References page in Project Designer
- Project Designer, References page
- Unused References dialog box
ms.assetid: 5a47c595-e084-401c-86e1-74e0bf74fd86
caps.latest.revision: 40
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 8bb18ec8dd12431d650d844e3698c1986c8d8bd8
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72665643"
---
# <a name="references-page-project-designer-visual-basic"></a>Page Références, Concepteur de projets (Visual Basic)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Utilisez la page **Références** du **Concepteur de projet** pour gérer des références, des références web et des espaces de noms importés dans votre projet. Les projets peuvent contenir des références aux composants COM, services web XML, assemblys ou bibliothèques de classes .NET Framework, ou d’autres bibliothèques de classes. Pour plus d’informations sur l’utilisation de références, consultez [Gestion des références dans un projet](../../ide/managing-references-in-a-project.md).

 Pour accéder à la page **Références**, choisissez un nœud de projet (pas le nœud **Solution**) dans l’**Explorateur de solutions**. Ensuite, choisissez **Projet**, **Propriétés** dans la barre de menus. Quand le Concepteur de projet apparaît, cliquez sur l’onglet **Références**.

## <a name="uielement-list"></a>Liste des éléments d’interface
 Les options suivantes vous permettent de sélectionner ou supprimer des références et des espaces de noms importés dans votre projet.

 **Références inutilisées** Cliquez sur ce bouton pour accéder à la boîte de dialogue **références inutilisées** .

 La boîte de dialogue **Références inutilisées** vous permet de supprimer des références qui sont dans votre projet mais qui, en fait, ne sont pas utilisées par le code. Elle contient une grille qui répertorie le **Nom de la référence**, le **Chemin** et d’autres informations sur les références d’espace de noms inutilisées dans votre projet. Dans la grille, sélectionnez les références d’espace de noms que vous souhaitez supprimer de votre projet et cliquez sur **Supprimer**.

 **Chemins d’accès de référence** Cliquez sur ce bouton pour accéder à la boîte de dialogue **chemins d'** accès des références.

> [!NOTE]
> Quand le système de projet trouve une référence d’assembly, le système résout la référence en regardant aux emplacements ci-dessous, dans l’ordre suivant :
>
> 1. Dossier du projet. Les fichiers du dossier du projet s’affichent dans l’**Explorateur de solutions** quand **Afficher tous les fichiers** n’est pas en vigueur.
>    2. Dossiers spécifiés dans la boîte de dialogue **Chemins des références**.
>    3. Dossiers qui affichent des fichiers dans la boîte de dialogue **Ajouter une référence**.
>    4. Dossier obj du projet. (Quand vous ajoutez une référence COM à votre projet, un ou plusieurs assemblys peuvent être ajoutés au dossier obj du projet.)

 **Références** Cette liste affiche toutes les références dans le projet, utilisées ou inutilisées.

 **Ajouter** Cliquez sur ce bouton pour ajouter une référence ou une référence Web à la liste des **références** .

 Choisissez **Référence**  pour ajouter une référence à votre projet à l’aide de la boîte de dialogue Ajouter une référence.

 Choisissez **Référence web** pour ajouter une référence web à votre projet à l’aide de la boîte de dialogue Ajouter une référence web.

 **Supprimer** Sélectionnez une ou plusieurs références dans la liste **références** , puis cliquez sur ce bouton pour la supprimer.

 **Mettre à jour la référence Web** Sélectionnez une référence Web dans la liste **références** et cliquez sur ce bouton pour la mettre à jour.

 **Espaces de noms importés** Vous pouvez taper votre propre espace de noms dans cette zone, puis cliquer sur **Ajouter une importation d’utilisateur** pour l’ajouter à la liste des espaces de noms.

 Vous pouvez créer des alias pour les espaces de noms importés par l’utilisateur. Pour ce faire, entrez l’alias et l’espace de noms au format *alias*=*espace de noms*. C’est utile si vous utilisez des espaces de noms longs, par exemple `Http= MyOrg.ObjectLib.Internet.WebRequestMethods.Http`.

 **Ajouter une importation d’utilisateur** Cliquez sur ce bouton pour ajouter l’espace de noms spécifié dans la zone **espaces de noms importés** à la liste des espaces de noms importés. Le bouton n’est actif que si l’espace de noms spécifié ne figure pas déjà dans la liste.

 **Liste des espaces de noms** Cette liste affiche tous les espaces de noms disponibles. Les cases des espaces de noms qui se trouvent dans votre projet sont cochées.

 **Mettre à jour l’importation d’utilisateur** Sélectionnez un espace de noms spécifié par l’utilisateur dans la liste espaces de noms, tapez le nom à utiliser pour le remplacer dans la zone **espaces de noms importés** , puis cliquez sur ce bouton pour passer au nouvel espace de noms. Le bouton n’est actif que si l’espace de noms sélectionné est l’un de ceux que vous avez ajoutés à la liste à l’aide du bouton **Ajouter une importation utilisateur**. Vous pouvez ajouter :

- Des classes ou des espaces de noms, par exemple <xref:System.Math?displayProperty=fullName>.

- Des importations avec alias, par exemple `VB=Microsoft.VisualBasic`.

- Des espaces de noms XML, par exemple `<xmlns:xsl="http://www.w3.org/1999/XSL/Transform">`.

## <a name="see-also"></a>Voir aussi
 [Plume Comment : ajouter ou supprimer des références à l’aide de la boîte de dialogue Ajouter une référence](https://msdn.microsoft.com/3bd75d61-f00c-47c0-86a2-dd1f20e231c9) [Comment : ajouter ou supprimer des espaces de noms importés (Visual Basic)](../../ide/how-to-add-or-remove-imported-namespaces-visual-basic.md) [bec : boîte de dialogue Ajouter une référence Web](https://msdn.microsoft.com/bdf05776-c591-40af-bfd7-e1e2aa1e87b5) [, instruction (espace de noms XML)](https://msdn.microsoft.com/library/1f4d50a6-08c7-4c2e-8206-ccae35fcd1b4)
