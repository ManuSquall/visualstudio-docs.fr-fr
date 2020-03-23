---
title: Page Références, Concepteur de projets (Visual Basic)
ms.date: 06/21/2017
ms.topic: reference
f1_keywords:
- vb.ProjectPropertiesReference
- vb.ProjectPropertiesUnusedReference
- vb.ProjectPropertiesReferencePaths
helpviewer_keywords:
- References page in Project Designer
- Project Designer, References page
ms.assetid: 5a47c595-e084-401c-86e1-74e0bf74fd86
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b80427999ad841c493e61cd704b64435f81c3914
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75565602"
---
# <a name="references-page-project-designer-visual-basic"></a>Page Références, Concepteur de projets (Visual Basic)

Utilisez la page **Références** du **Concepteur de projet** pour gérer des références, des références web et des espaces de noms importés dans votre projet. Les projets peuvent contenir des références à des composants COM, des services web XML, des assemblys ou des bibliothèques .NET, ou d’autres bibliothèques de classes. Pour plus d’informations sur l’utilisation de références, consultez [Gestion des références dans un projet](../../ide/managing-references-in-a-project.md).

Pour accéder à la page **Références**, choisissez un nœud de projet (pas le nœud **Solution**) dans l’**Explorateur de solutions**. Ensuite, choisissez **Projet**, **Propriétés** dans la barre de menus. Quand le Concepteur de projet apparaît, cliquez sur l’onglet **Références**.

## <a name="uielement-list"></a>Liste des éléments de l'interface utilisateur

Les options suivantes vous permettent de sélectionner ou supprimer des références et des espaces de noms importés dans votre projet.

**Chemins d'accès des références**

Cliquez sur ce bouton pour accéder à la boîte de dialogue **Chemins des références**.

> [!NOTE]
> Quand le système de projet trouve une référence d’assembly, le système résout la référence en regardant aux emplacements ci-dessous, dans l’ordre suivant :
>
> 1. Dossier du projet. Les fichiers du dossier du projet s’affichent dans l’**Explorateur de solutions** quand **Afficher tous les fichiers** n’est pas en vigueur.
> 2. Dossiers spécifiés dans la boîte de dialogue **Chemins des références**.
> 3. Dossiers qui affichent des fichiers dans la boîte de dialogue **Ajouter une référence**.
> 4. Dossier obj du projet. (Quand vous ajoutez une référence COM à votre projet, un ou plusieurs assemblys peuvent être ajoutés au dossier obj du projet.)

 **Références**

Cette liste affiche toutes les références dans le projet, utilisées ou non.

 **Ajouter**

Cliquez sur ce bouton pour ajouter une référence ou une référence web à la liste **Références**.

Choisissez **Référence ** pour ajouter une référence à votre projet à l’aide de la boîte de dialogue Ajouter une référence.

Choisissez **Référence web** pour ajouter une référence web à votre projet à l’aide de la boîte de dialogue **Ajouter une référence web**.

 **Supprimer**

Sélectionnez une ou plusieurs références dans la liste **Références**, puis cliquez sur ce bouton pour les supprimer.

 **Mettre à jour la référence web**

Sélectionnez une référence web dans la liste **Références** et cliquez sur ce bouton pour la mettre à jour.

 **Espaces de noms importés**

Vous pouvez taper votre propre espace de noms dans cette zone et cliquer sur **Ajouter une importation utilisateur** pour l’ajouter à la liste d’espaces de noms.

Vous pouvez créer des alias pour les espaces de noms importés par l’utilisateur. Pour ce faire, entrez le pseudonyme et l’espace nom dans le format *alias*=*namespace*. C’est utile si vous utilisez des espaces de noms longs, par exemple `Http= MyOrg.ObjectLib.Internet.WebRequestMethods.Http`.

 **Ajouter une importation utilisateur**

Cliquez sur ce bouton pour ajouter l’espace de noms spécifié dans la zone **Espaces de noms importés** à la liste des espaces de noms importés. Le bouton n’est actif que si l’espace de noms spécifié ne figure pas déjà dans la liste.

 **Liste d’espaces de noms**

Cette liste affiche tous les espaces de noms disponibles. Les cases des espaces de noms qui se trouvent dans votre projet sont cochées.

 **Mettre à jour l’importation utilisateur**

Sélectionnez un espace de noms défini par l’utilisateur dans la liste d’espaces de noms, tapez un nouveau nom pour cet espace dans la zone **Espaces de noms importés**, puis cliquez sur ce bouton pour valider le nouvel espace de noms. Le bouton n’est actif que si l’espace de noms sélectionné est l’un de ceux que vous avez ajoutés à la liste à l’aide du bouton **Ajouter une importation utilisateur**. Vous pouvez ajouter :

- Des classes ou des espaces de noms, par exemple <xref:System.Math?displayProperty=fullName>.

- Des importations avec alias, par exemple `VB=Microsoft.VisualBasic`.

- Des espaces de noms XML, par exemple `<xmlns:xsl="http://www.w3.org/1999/XSL/Transform">`.

## <a name="see-also"></a>Voir aussi

- [Gestion des références dans un projet](../../ide/managing-references-in-a-project.md)
- [Guide pratique pour ajouter ou supprimer des espaces de noms importés (Visual Basic)](../../ide/how-to-add-or-remove-imported-namespaces-visual-basic.md)
- [Imports (instruction) (espace de noms XML)](/dotnet/visual-basic/language-reference/statements/imports-statement-xml-namespace)
