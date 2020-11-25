---
title: Utilisation d’extraits XML
description: Apprenez à utiliser des commandes dans l’éditeur XML pour insérer des extraits XML ou pour encapsuler un extrait de code XML dans le texte sélectionné.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 3a27375b-81cc-48f6-a884-e1cb8c4f78f5
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4bebca3a27d11015388e45ff6839f446506e716c
ms.sourcegitcommit: 935e4d9a20928b733e573b6801a6eaff0d0b1b14
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/25/2020
ms.locfileid: "95970600"
---
# <a name="how-to-use-xml-snippets"></a>Comment : utiliser des extraits XML

Vous pouvez appeler des extraits XML à l’aide des deux commandes suivantes dans le menu contextuel de l’éditeur XML. La commande **Insérer un extrait** insère l’extrait XML à la position du curseur. La commande **entourer de** encapsule l’extrait XML autour du texte sélectionné. Chaque extrait XML possède des types d'extrait désignés. Les types d’extraits déterminent si l’extrait de code est disponible avec la commande **Insérer un extrait** , la commande **entourer de** ou les deux.

Une fois l'extrait XML ajouté à l'éditeur, tous ses champs modifiables sont surlignés en jaune et le curseur est placé dans le premier d'entre eux.

## <a name="insert-snippet"></a>Insérer un extrait

Les procédures suivantes décrivent comment accéder à la commande **Insérer un extrait** .

> [!NOTE]
> La commande **Insérer un extrait** de code est également disponible par le biais du raccourci clavier (**CTRL** + **K**, puis **CTRL** + **X**).

### <a name="to-insert-snippets-from-the-shortcut-menu"></a>Pour insérer des extraits à partir du menu contextuel

1. Placez le curseur à l'endroit où vous souhaitez insérer l'extrait XML.

2. Cliquez avec le bouton droit et sélectionnez **Insérer un extrait**.

   Une liste des extraits XML disponibles s'affiche.

3. Sélectionnez un extrait dans la liste à l’aide de la souris, ou en tapant le nom de l’extrait de code et en appuyant sur **Tab** ou **entrée**.

### <a name="to-insert-snippets-using-the-intellisense-menu"></a>Pour insérer des extraits à l'aide du menu IntelliSense

1. Placez le curseur à l'endroit où vous souhaitez insérer l'extrait XML.

2. Dans le menu **Edition** , pointez sur **IntelliSense**, puis sélectionnez **Insérer un extrait**.

   Une liste des extraits XML disponibles s'affiche.

3. Sélectionnez un extrait dans la liste à l’aide de la souris ou en tapant le nom de l’extrait de code et en appuyant sur **Tab** ou **entrée**.

### <a name="to-insert-snippets-through-the-intellisense-complete-word-list"></a>Pour insérer des extraits de code dans la liste complète des mots IntelliSense

1. Placez le curseur à l'endroit où vous souhaitez insérer l'extrait XML.

2. Commencez à entrer l'extrait XML à ajouter à votre fichier. Si le remplissage automatique est activé, la liste de remplissage IntelliSense s'affiche. Si elle n’apparaît pas, appuyez sur **CTRL** + **Space** pour l’activer.

3. Sélectionnez l'extrait XML dans la liste de remplissage.

4. Appuyez sur **Tab**, **onglet** pour appeler l’extrait XML.

> [!NOTE]
> Parfois, l'extrait XML n'est pas invoqué. Par exemple, si vous tentez d'insérer un élément `xs:complexType` dans un nœud `xs:element`, l'éditeur ne génère aucun extrait XML. En effet, lorsqu'un élément `xs:complexType` est utilisé à l'intérieur d'un nœud `xs:element`, aucun attribut ni sous-élément n'est requis, de sorte que l'éditeur n'a aucune donnée à insérer.

### <a name="to-insert-snippets-using-the-shortcut-name"></a>Pour insérer des extraits à l'aide du nom raccourci

1. Placez le curseur à l'endroit où vous souhaitez insérer l'extrait XML.

2. Entrez `<` dans le volet de l'éditeur.

3. Appuyez sur **Échap** pour fermer la liste compléter le mot IntelliSense.

4. Tapez le nom du raccourci de l’extrait de code, puis appuyez sur la touche **Tab** pour appeler l’extrait XML.

## <a name="surround-with"></a>Entourer de

Les procédures suivantes décrivent comment accéder à la commande **surround** .

> [!NOTE]
> La commande **entourer de** est également disponible via le raccourci clavier (**CTRL** + **K**, puis **CTRL** + **S**).

### <a name="to-use-surround-with-from-the-context-menu"></a>Pour utiliser entourer de dans le menu contextuel

1. Sélectionnez le texte à entourer dans l’éditeur XML.

2. Cliquez avec le bouton droit et sélectionnez **entourer de**.

   Une liste des encadrements d'extraits XML disponibles s'affiche.

3. Sélectionnez un extrait dans la liste à l’aide de la souris, ou en tapant le nom de l’extrait de code et en appuyant sur **Tab** ou **entrée**.

### <a name="to-use-surround-with-from-the-intellisense-menu"></a>Pour utiliser entourer de à partir du menu IntelliSense

1. Sélectionnez le texte à entourer dans l’éditeur XML.

2. Dans le menu **Edition** , pointez sur **IntelliSense**, puis sélectionnez **entourer de**.

   Une liste des encadrements d'extraits XML disponibles s'affiche.

3. Sélectionnez un extrait dans la liste à l’aide de la souris, ou en tapant le nom de l’extrait de code et en appuyant sur **Tab** ou **entrée**.

## <a name="use-xml-snippets"></a>Utiliser des extraits XML

Une fois que vous avez choisi un extrait XML, le texte de cet extrait de code est automatiquement inséré à l'emplacement du curseur. Tous les champs modifiables contenus dans l'extrait sont surlignés et le premier de ces champs est automatiquement sélectionné. Le champ actuellement sélectionné est encadré.

Après avoir sélectionné un champ, vous pouvez y entrer une nouvelle valeur. La pression sur la touche **Tab** parcourt les champs modifiables de l’extrait de code. en appuyant sur la **touche Maj** + **Tab** , vous les Parcourez dans l’ordre inverse. Cliquer dans un champ place le curseur dans ce champ ; double-cliquer sur un champ permet de le sélectionner. Lorsqu'un champ est en évidence, une info-bulle peut s'afficher pour le décrire.

Seule la première instance d'un champ donné est modifiable. Lorsque ce champ est surligné, les autres instances du même champ sont mises en évidence. Lorsque vous modifiez la valeur d'un champ modifiable, ce champ change partout où il est utilisé dans l'extrait.

Appuyez sur **entrée** ou sur **Échap** pour annuler la modification du champ et revenir à la normale de l’éditeur.

Les couleurs par défaut des champs d’extrait de code modifiables peuvent être modifiées en modifiant le paramètre **champ d’extrait de code** dans le volet **polices et couleurs** de la boîte de dialogue **options** . Pour plus d’informations, consultez [Comment : modifier les polices et les couleurs dans l’éditeur](../ide/reference/how-to-change-fonts-and-colors-in-the-editor.md).

## <a name="see-also"></a>Voir aussi

- [extraits XML](../xml-tools/xml-snippets.md)
- [Comment : générer un extrait XML à partir d’un schéma XML](../xml-tools/how-to-generate-an-xml-snippet-from-an-xml-schema.md)
- [Comment : créer des extraits XML](../xml-tools/how-to-create-xml-snippets.md)
